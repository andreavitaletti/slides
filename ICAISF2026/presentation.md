---
marp: true
# theme: default
theme: beam
paginate: true
header: "Collective Seed Storage"
footer: "ICSSC2026"
style: |
  @import url('https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.1/css/all.min.css');
  section {
    font-size: 28px;
  }
  h1 {
    color: #2c3e50;
  }
  h2 {
    color: #34495e;
  }
  .box {
      background-color: var(--color-primary, #1f38c5);
      color: white;
      padding: 25px;
      border-radius: 8px;
      margin-top: 20px;
    }
    /* This targets the ### header specifically inside your box */
  .box h3 {
      color: white !important;
      margin-top: 0;
      border-bottom: 1px solid rgba(255,255,255,0.3);
      padding-bottom: 10px;
    }
  .box strong { color: #ffcc00; } /* Yellow for bold text inside */
  .source {
    position: absolute;
    bottom: 10px;
    right: 10px;
    font-size: 12px;
    background: rgba(255, 255, 255, 0.7);
    padding: 2px 8px;
    border-radius: 4px;
    z-index: 100;
  }
  /* Style links inside the source tag */
  .source a {
    color: #333;
    text-decoration: none;
  }
---

<!--
https://rnd195.github.io/marp-community-themes/theme/beam.html
https://fontawesome.com/icons
-->

# Collective Seed Storage
### A Sustainable Approach to Ex Situ Seed Conservation through Citizen Participation and Distributed Storage

**Andrea Vitaletti**<sup>1</sup> **and Khalil Massri**<sup>2</sup>
*<sup>1</sup>Sapienza University of Rome, <sup>2</sup>Hebron University*

![bg right:35% fit](img/vision.png)

---

# The Need for Seed Diversity

- Over 50,000 edible plants exist worldwide, but **just 15 provide 90% of food energy intake** (e.g., rice, corn, wheat).
- More than 95% of crop **genetic erosion** articles report changes in diversity, with nearly 80% showing evidence of loss [[1]](https://doi.org/10.1111/nph.17733).

<div class="box">

### :seedling: Genetic diversity 
Vital to adapt to climate change, extreme weather, pests, and diseases

</div>

![bg right:40% fit](img/GD.gif)

---

# Conservation Strategies

| Criteria | In Situ Conservation | Ex Situ Conservation |
|----------|----------------------|----------------------|
| **Location** | Natural environment / farms | Seed banks, seed vaults |
| **Evolution** | Plants adapt naturally | Static; no natural evolution |
| **Risk of Loss**| Higher (climate, land-use) | Lower (controlled conditions) |
| **Access** | Local and informal | Global access via formal mechanisms |
| **Cost** | Lower short-term cost | Higher cost (infrastructure) |
| **Best Use** | Wild relatives, landraces | Major crops, backup |

---

# Svalbard Global Seed Vault (SGSV)

- A global backup facility for seed banks worldwide.
- Safeguards over 1.2 million samples representing >6,000 plant species.
- Unanimously considered the **backup seed facility that provides the highest standards of safety and security.**

![bg right:40%](img/SGSV.jpg)

---

# Open Problem

- The vast majority of species, mostly CWR in the SGSV, have only a **single depositor** [[2]](https://seedvault.nordgen.org/Search).
- **The Threat:** if a disaster hits both the primary seed bank and the vault, the species could be lost.

![bg right:40% fit](img/distr.png)

---

# Orthodox Seeds and Storage

- **Orthodox Seeds:** Approximately 90% of species can retain viability if dried and kept at low temperatures (e.g., wheat, rice, legumes).
- **Storage Standards:** FAO recommends [[3]](https://doi.org/10.4060/cc0021en) long-term storage at **-18°C and 15% relative humidity.**
- Subzero freezers are acceptable if ideal conditions are not available.

![bg right:40% fit](img/surv_rate.jpg)

---

# Collective Seed Storage (CSS)

- **Domestic freezers provide suitable conditions for seed conservation** 
- **Vision:** Each household becomes a micro-node in a distributed seed conservation system. Citizens are active contributors to food system resilience and biodiversity conservation
- **Shared Economy Approach:** Sharing a tiny, idle portion of home freezers for seed preservation, to drastically increase redundancy and the overall availability of seeds with minimal infrastructure investments.

![bg right:35% fit](img/vision.png)

---

# CSS Requirements

To ensure feasibility and active participation, the system must meet:

1. **Storage Standards (R1):** FAO long-term storage conditions (approx. -18°C). Subzero acceptable.
2. **User-Friendly (R2):** Simple installation using off-the-shelf equipment and home WiFi.
3. **Longevity (R3):** Operate for at least 1 year without user intervention (battery life).
4. **Incentivization (R4):** Implement mechanisms to reward users for their long-term commitment.

---

# R1: Storage

<!--
- **Experiment:** Monitoring a Bosch domestic freezer set to -18°C.
- **Results:** Subzero conditions are easily met, though temperature fluctuates (as per acceptable secondary standards).
--> 

- FAO standards :neutral_face:
- Subzero conditions :slightly_smiling_face:

![bg right:65% fit](img/visualization.png)

---

# Architecture

<!--
https://www.emojicheatsheet.com/
https://github.com/ikatyang/emoji-cheat-sheet
-->


- R2: friendly  :slightly_smiling_face:

![bg right:65% fit](img/css.drawio.png)

---

# R3: Lifetime 

- **> 1 year** :slightly_smiling_face:
- 1.5Ah LiFePo4 battery
- Duty Cycle: active period about 6 seconds, sleep period >0.73 hours

![bg right:65% fit](img/current_new.png)

---

# R4: Incentive

- Blockchain Lottery :neutral_face:

![bg right:65% fit](img/lottery.png)

---

# Conclusions

- CSS can support the preservation of seed diversity by transforming urban citizens into "active" agents of agricultural resilience. 
- Households become micro-nodes within a distributed seed conservation system
- Our Proof-of-Concept demonstrates the feasibility of the core technical components underlying this vision.

![bg right:35% fit](img/vision.png)

---

![bg fit](img/Sustainable_Development_Goals_h.png)

---

# A recent visit to the seed bank at Rome's Botanic Garden

![bg](img/IMG_20260721_111740317_HDR.jpg)
![bg](img/IMG_20260721_111842274_HDR.jpg)
![bg](img/IMG_20260721_112431320_HDR.jpg)

---

# Discussion

- A modern approach to seed preservation should promote <u>more active citizen participation</u> (e.g., Seed Guardians) that extends beyond the mere act of storage.
-  Although the preservation of seeds in domestic freezers is a novel and valuable practice, it may remain, to some extent, a "passive" activity. 

___

# Future Vision: [www.seedpeers.net](https://www.seedpeers.net/)

![bg fit](img/micro-greenhouse-MF.png)

--- 


# Thank you!

### Questions?

<!-- :envelope: vitaletti@diag.uniroma1.it -->
<i class="fa-solid fa-at"></i> vitaletti@diag.uniroma1.it
<i class="fa-brands fa-github"></i> [https://andreavitaletti.github.io/](https://andreavitaletti.github.io/)

[https://github.com/andreavitaletti/slides/tree/main/ICAISF2026](https://github.com/andreavitaletti/slides/tree/main/ICAISF2026)

![bg right:35% fit](img/qrcode_github.com.png)

---

# Image sources

- Slide 6: https://doi.org/10.1111/rec.13174
- Slide 2: https://medium.com/thenextnorm/importance-of-genetic-diversity-in-agriculture-b9f88f5fda55
- Slide 4: https://en.wikipedia.org/wiki/Svalbard_Global_Seed_Vault#/media/File:Svalbard_Global_Seed_Vault_February_2025.jpg
