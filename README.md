# Panorama to ParentSquare: Automated SIS ID Stamping & Merging

## 📖 Project Overview
This utility was developed for **Deerfield Public Schools District 109** to bridge a critical data gap between **Panorama Education** exports and **ParentSquare** Secure Document Delivery.

### The Challenge
Panorama exports individual student reports as PDFs named by **Student SIS ID**. However, ParentSquare’s Secure Document Delivery engine requires the SIS ID to be physically present as text on the document body to facilitate automated routing. Additionally, these documents are prepared for archival in **Skyward** student portals.

### The Solution
By leveraging the Unix-based backend of **macOS**, this script automates the "last mile" of data management. It batch-processes a folder of PDFs, extracts the SIS ID from the filename, stamps it onto the document header, and merges the results into a single Master PDF for a seamless, one-click upload.

## 🚀 Features
- **High-Speed Batch Processing:** Handles 400+ PDFs in under 30 seconds.
- **Dynamic OCR-Ready Stamping:** "Burns" the SIS ID onto the page header for system readability.
- **Automated Consolidation:** Merges individual files into one Master Upload file for ParentSquare.
- **FERPA & Privacy Compliant:** All processing is performed locally on the workstation. No student data is ever uploaded to third-party web tools or external cloud converters.

## 🛠️ Prerequisites (macOS)
This workflow is optimized for **macOS** and requires **Homebrew** and **cpdf**.

1. **Install Homebrew:**
   ```bash
   /bin/bash -c "$(curl -fsSL [https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh](https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh))"
