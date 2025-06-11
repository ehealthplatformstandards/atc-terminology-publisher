# 🧬 ATC Terminology Publisher

This repository automatically publishes the latest **ATC (Anatomical Therapeutic Chemical Classification System)** terminology every week. The resulting file, [`atc-codesystem.csv`](./atc-codesystem.csv), is intended to be used in healthcare applications that rely on up-to-date medication classification data.

## 🚀 How It Works

A GitHub Actions workflow (`.github/workflows/update-atc.yml`) runs **every Monday at 6:00 UTC** and performs the following steps:

1. Downloads and extracts the data processing script from  
   [`sarrabenyahia/webscrap_health_monitoring`](https://github.com/sarrabenyahia/webscrap_health_monitoring)
2. Installs the required Python dependencies.
3. Executes the script that downloads and converts the official ATC/DDD Excel file.
4. Converts the Excel file to a CSV file using `ssconvert`.
5. Replaces the existing `atc-codesystem.csv` file with the newly generated version.
6. Commits and pushes the updated CSV file to the repository.

This repository is part of the [eHealth Platform Standards initiative](https://github.com/ehealthplatformstandards) and is used in the workflow of  
👉 [`ehealthplatformstandards/atc-terminology-publisher`](https://github.com/ehealthplatformstandards/atc-terminology-publisher)

## 📦 Output

- `atc-codesystem.csv`: The latest ATC terminology in CSV format, regenerated weekly.

## 📅 Schedule

The workflow is scheduled as follows:

```yaml
cron: '0 6 * * 1'  # Every Monday at 6:00 UTC
````

## 🛠️ Requirements (Handled by the workflow)

* Python 3
* `pip`
* `gnumeric` (for `ssconvert`)
* `wget`, `unzip`

These are automatically installed inside the GitHub Actions runner during execution.

## 📚 ATC/DDD Copyright & Disclaimer

© Copyright
[WHO Collaborating Centre for Drug Statistics Methodology](https://atcddd.fhi.no/copyright_disclaimer/), Oslo, Norway

The ATC/DDD data used in this repository is published by the WHO Collaborating Centre for Drug Statistics Methodology. Use of this material must comply with their conditions of use, summarized as follows:

* ✅ Use of all or parts of the material **requires proper attribution** to the WHO Collaborating Centre.
* 🚫 **Copying or redistribution for commercial purposes is strictly prohibited.**
* ⚠️ **Changing or manipulating** the content of the material is **not allowed**.

> **Disclaimer**
> The WHO Collaborating Centre makes every effort to ensure the quality and accuracy of the information available on its website and updates it regularly. However, the Centre does not guarantee and assumes no legal liability for the accuracy, completeness, or interpretation of the information.

### ✅ Compliance Statement

This repository respects the above terms by ensuring:

* Clear **attribution** to the WHO Collaborating Centre.
* Usage for **non-commercial**, **educational**, or **research** purposes only.
* The original dataset is **not modified** or rebranded.
* The data is **not redistributed** on package registries or platforms in a way that implies ownership or redistribution rights.

If in doubt, please refer to the official [copyright & disclaimer page](https://atcddd.fhi.no/copyright_disclaimer/) or contact the WHO Collaborating Centre directly at **[atcddd@fhi.no](mailto:atcddd@fhi.no)**.

## 🤝 Acknowledgements

Thanks to [@sarrabenyahia](https://github.com/sarrabenyahia) for maintaining the [ATC scraping script](https://github.com/sarrabenyahia/webscrap_health_monitoring).