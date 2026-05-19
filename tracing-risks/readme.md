npx -y @marp-team/marp-cli@latest -p presentation.md --allow-local-files

npx -y @marp-team/marp-cli@latest presentation.md --pdf --allow-local-files -o presentation.pdf

npx -y @marp-team/marp-cli@latest --theme beam.css -p presentation.md --allow-local-files

npx -y @marp-team/marp-cli@latest --theme beam.css presentation.md --pdf --allow-local-files -o presentation.pdf

