
# Panorama to ParentSquare: Automated SIS ID Stamping & Merging

## 📖 Project Overview
This utility was developed for **Deerfield Public Schools District 109** to resolve a critical interoperability gap between **Panorama Education** exports and **ParentSquare** Secure Document Delivery.

### The Challenge
Panorama exports student reports as individual PDFs named by **Student SIS ID**. However, ParentSquare’s Secure Document Delivery engine requires the SIS ID to be physically present as text on the document body to facilitate automated routing. Furthermore, these documents must be processed for archival within **Skyward** student portals.

### The Solution
By leveraging the Unix-based backend of **macOS**, this script automates the "last mile" of data management. It batch-processes a folder of PDFs, extracts the SIS ID from the filename, stamps it onto the document header, and merges the results into a single Master PDF for a seamless, one-click upload.



## 🚀 Features
- **High-Speed Batch Processing:** Handles 400+ PDFs in under 30 seconds.
- **Dynamic OCR-Ready Stamping:** "Burns" the SIS ID onto the page header for system readability.
- **Automated Consolidation:** Merges individual files into one Master Upload file for ParentSquare.
- **Skyward Ready:** Prepares documents for individual portal archival.
- **FERPA & Privacy Compliant:** All processing is performed locally on the workstation. No student data is ever uploaded to third-party web tools or external cloud converters.

## 🛠️ Prerequisites (macOS)
This workflow is optimized for **macOS** and requires **Homebrew** and **cpdf** (Classic PDF).

1. **Install Homebrew:**
   ```bash
   /bin/bash -c "$(curl -fsSL [https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh](https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh))"

```

2. **Install cpdf:**
```bash
brew install cpdf

```



## 💻 Usage

1. Open Terminal and navigate to your directory: `cd /path/to/pdfs`
2. Execute the following master command:
```bash
mkdir -p Final_Stamped; for f in *.pdf; do cpdf -add-text "${f%.pdf}" -top 20 -font "Helvetica" -font-size 10 -color "0 0 0" "$f" -o "Final_Stamped/$f"; done; cpdf -merge Final_Stamped/*.pdf -o Master_Combined_Upload.pdf

```



## ⚙️ Logic Breakdown

* `mkdir -p Final_Stamped`: Creates a destination folder to preserve original source files.
* `${f%.pdf}`: Shell parameter expansion to strip the extension, ensuring only the numeric SIS ID is stamped.
* `-top 20`: Precise vertical placement optimized for the ParentSquare scanning engine.
* `-merge`: Efficiently combines hundreds of individual records into a single upload-ready master file.

## 👤 Author

**Annette Maloney** Data and Systems Manager

Deerfield Public Schools District 109

```

***

```
