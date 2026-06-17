---
marp: true
theme: beam
paginate: true
header: "Digital Twin of an Ultrasonic Fermentation System"
footer: "IE 2026 · 22nd International Conference on Intelligent Environments"
style: |
  @import url('https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.1/css/all.min.css');
  section {
    font-size: 26px;
  }
  h1 { color: #2c3e50; }
  h2 { color: #34495e; }
  .box {
    background-color: var(--color-primary, #0a7e8c);
    color: white;
    padding: 22px 25px;
    border-radius: 8px;
    margin-top: 16px;
  }
  .box h3 {
    color: white !important;
    margin-top: 0;
    border-bottom: 1px solid rgba(255,255,255,0.3);
    padding-bottom: 8px;
  }
  .box strong { color: #f4a52c; }
  .warn {
    background-color: #c0392b;
    color: white;
    padding: 22px 25px;
    border-radius: 8px;
    margin-top: 16px;
  }
  .warn h3 {
    color: white !important;
    margin-top: 0;
    border-bottom: 1px solid rgba(255,255,255,0.3);
    padding-bottom: 8px;
  }
  .warn strong { color: #f4a52c; }
  .highlight {
    background-color: #0d1b3e;
    color: white;
    padding: 18px 22px;
    border-radius: 8px;
    margin-top: 16px;
    font-size: 24px;
    border-left: 5px solid #f4a52c;
  }
  .highlight strong { color: #f4a52c; }
  .source {
    position: absolute;
    bottom: 10px;
    right: 10px;
    font-size: 12px;
    background: rgba(255,255,255,0.7);
    padding: 2px 8px;
    border-radius: 4px;
    z-index: 100;
  }
  .source a { color: #333; text-decoration: none; }
  table { font-size: 22px; }
---

# Digital Twin of an Ultrasonic Fermentation System
### A Proof of Concept 

F.S. Sconocchia Pisoni, D. Appolloni, F. Ortenzi, M.J. Guillén,
A. Contaldo, B. Morozzo della Rocca, **A. Vitaletti**

*Sapienza University of Rome · University of Rome Tor Vergata · Yeastime Srl*

---

# Context: Beer Fermentation & Ultrasound

- Beer fermentation is a **slow, resource-intensive** industrial process: experiments take days and are costly to repeat
- **Ultrasound technology** (20–50 kHz, low power) is a promising tool to accelerate yeast activity

<div class="highlight">

**[Yeastime](https://yeastime.com/)** estimates: a 30% reduction in fermentation time in craft breweries could lead to cost savings of approximately **10–15%**

</div>

- Key effects: improved mass transfer, increased cell permeability, reduced inhibitory metabolites
- This work presents the **first digital twin tailored to an ultrasound-treated fermentation system**

---

# What is a Digital Twin?

A **digital twin** is a virtual representation of a physical system that stays continuously synchronised through real-time data.

<div class="highlight">

### <i class="fa-solid fa-lightbulb"></i> Key Benefit
Physical fermentation trials are **slow and expensive**, the digital twin complements them with **rapid simulation and intelligent actuation**.

</div>

---


![bg 80%](images/fermentator_DT_1.drawio.png)


---

# The Dataset

Biological datasets are limited by **slow, manual sampling** each growth curve takes days

<div class="warn">

### <i class="fa-solid fa-triangle-exclamation"></i> Data Scarcity Challenge
~100 data points: approximately **100× smaller** than the reference study [Palacios et al., 2014]

</div>

Classical training is ineffective: high risk of overfitting.

--- 

# The Dataset

| Feature | Description |
|---------|-------------|
| Ultrasound duty cycle | Fraction of time transducer is active |
| Irradiation frequency | Ultrasonic frequency applied (normalised) |
| Temperature | Medium temperature (normalised) |
| Initial / final OD | Yeast density measured at 600 nm |

> Points sharing the same duty cycle, frequency, and initial density belong to the **same biological growth curve**: treated as a group in cross-validation.

---

# Predictive Model: Gompertz + Bayesian NN

The core of the digital twin is a **Gompertz growth model** whose parameters, **D** = total growth amplitude, **μ** = max growth rate and **λ** = lag time,  are inferred by a Bayesian neural network:

$$E[N_t \mid N_0, D, \mu, \lambda] = N_0 + D \cdot \exp\!\left(-\exp\!\left(1 + \frac{\mu e (\lambda - t)}{D}\right)\right)$$

![bg right:50% fit](images/Gompertz_params_1.png)


---

# Priors

We have "clear", physical intuition for the outputs ($D$, $\mu$, $\lambda$), but we have zero biological intuition for what individual neural network weights ($w$) should look like. 

<div class="highlight">

Translate a Prior on the Output Space into a Prior on the Parameter Space via the Likelihood function and MCMC sampling.

</div>

---

# Detour

The posterior probability of a set of weights $\mathbf{w}$ given the observed fermentation data $y$ is:

$$p(\mathbf{w} \mid y) \propto p(y \mid \mathbf{w}) \cdot p(\mathbf{w})$$

- $p(y \mid \mathbf{w})$ is the Likelihood: How well do the weights explain the raw sensor data?
- $p(\mathbf{w})$ is the Weight Prior

If a randomly proposed step in the weights ($\mathbf{w}^*$) causes the network to output an impossible value for $D$, $\mu$, or $\lambda$, the mathematical probability of that weight configuration is zero. Therefore, the biological output limits act as a filter that shapes the allowed weight space.

---

# Monte Carlo (MCMC) Sampling


Because we can't analytically calculate how to constrain the weights to get the right outputs, we let the Random Walk Metropolis algorithm discover the valid weight spaces through exploration.

![bg right:50% fit](images/mcmc_weight_filtering_flowchart.png)

---

![bg fit](images/bayesian_montecarlo_priors_process.png)
![bg fit](images/nn_gompertz_architecture.png)

---


# Bayesian Inference Pipeline

Given the **limited dataset**, classical training is ineffective. We adopt [Palacios et al., 2014]:

1. **Prior assignment** — probability distributions encode biological domain knowledge
2. **Random Walk Metropolis** — explores the posterior to find valid weight configurations; Metropolis-Hastings criterion escapes local maxima
3. **Network ensemble** — each accepted MCMC state instantiates a distinct NN outputting D, μ, λ
4. **Final prediction** — parameters averaged across all sampled networks → Gompertz curve

<div class="highlight">

For **small datasets**, highly informative priors are essential. For larger datasets, weakly informative priors such as $\mathcal{N}(0, 100)$ are sufficient — as also recommended in [Palacios et al.].

</div>

---

# Informative Priors Matter

![bg right:52% fit](images/prior_comparison.png)

Removing informative priors causes a **~7× increase in MSE**:



- Mean Absolute Percentage Error (Mean APE)
- Median Absolute Percentage Error (Median APE)
- Mean Square Error (MSE)

---

<div class="warn">

### <i class="fa-solid fa-triangle-exclamation"></i> Takeaway
In fermentation, experiments are too slow to generate large datasets — **biological prior knowledge is the only practical regulariser**.

</div>

---

# Model Performance: 5-Fold Cross-Validation

![bg right:55% fit](images/fold_metrics.png)

> MSE is ~88× higher than [Palacios et al.] — attributable to dataset size (~100× smaller), single MCMC chain, and optical density (OD) measurement scale differences.

---

![bg fit sepia](images/observed_vs_predicted_uninformative.png)
![bg fit](images/observed_vs_predicted.png)

---

![bg fit sepia](images/error_distribution_uninformative.png)
![bg fit](images/error_distribution.png)

---


# Predicted vs. Observed Growth Curve

![bg right:55% fit](images/optical_density_with_uncertainty_.png)



<div class="box">

### <i class="fa-solid fa-circle-check"></i> Validation
**The model demonstrates Feasibility for small-data bioprocess prediction**: a solid foundation for a fully autonomous digital twin.

</div>

---

# Actuation: Closing the Loop

The digital twin controls the **ultrasonic stimulation parameters**:

- <i class="fa-solid fa-wave-square"></i> **Frequency** — piezoelectric transducer driven at resonance via PWM square wave (ESP32 + H-bridge amplifier)
- <i class="fa-solid fa-sliders"></i> **Duty cycle** — delivered as energy bursts modulated at 150 Hz
- <i class="fa-solid fa-thermometer-half"></i> **Temperature** — monitored; closed-loop thermal control is left for future work

<div class="highlight">

**Accelerating yeast growth** shortens the production cycle → significant economic benefit. The digital twin enables testing actuation strategies **without costly physical trials**.

</div>

---

# Conclusions

- First **proof of concept** digital twin for an ultrasonic fermentation system
- Bayesian NN + Gompertz model **effective under data scarcity** (~100 points)
- Informative priors reduce MSE by **~7×** vs. non-informative baseline
- Real-time sensing pipeline (ESP32, piezoelectric disk, Dallas probe) **validated on physical fermenter**

<div class="box">

### <i class="fa-solid fa-scale-balanced"></i> Core Message
The digital twin enables **faster, cheaper, smarter** fermentation optimisation — complementing slow physical experiments with rapid simulation and autonomous actuation.

</div>

---

# Future Work

- <i class="fa-solid fa-database"></i> **Expand dataset** — collect more growth curves to relax prior constraints and improve generalisation
- <i class="fa-solid fa-eye"></i> **Automate OD sensing** — currently manual; real-time density measurement is the key bottleneck for full automation
- <i class="fa-solid fa-thermometer-half"></i> **Integrate thermal control** — close the temperature actuation loop
- <i class="fa-solid fa-arrows-spin"></i> **Multiple MCMC chains** — improve posterior exploration beyond the current single-chain implementation
- <i class="fa-solid fa-flask"></i> **Full closed-loop validation** — experimentally validate the feedback-optimisation framework end-to-end

---

# Discussion

- How can **digital twin frameworks** best handle the tension between data scarcity and model accuracy in biological systems?
- What are the practical thresholds at which **Bayesian priors** can be relaxed in favour of data-driven learning?
- How should **ultrasonic actuation parameters** be explored efficiently — can the digital twin guide active learning?
- What does **intelligent environment** design look like for bio-oriented systems such as breweries?
