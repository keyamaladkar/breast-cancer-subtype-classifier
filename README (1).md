# 📂 Dataset Instructions

Real TCGA-BRCA data is **not included** in this repository due to file size and GDC data access terms.

---

## How to Download Real TCGA-BRCA Data (Free)

### Option A — cBioPortal (Easiest)

1. Go to: https://www.cbioportal.org/study/summary?id=brca_tcga_pan_can_atlas_2018
2. Click the **Download** button (top right)
3. Download these two files:
   - **mRNA expression (RNA Seq V2 RSEM)** → `data_mrna_seq_v2_rsem.txt`
   - **Clinical data (Sample)** → `data_clinical_sample.txt`
4. Upload both to your Colab session (Files panel on the left sidebar)
5. In the notebook, set `USE_REAL_DATA = True` in Section 2

### Option B — GDC Data Portal

1. Go to: https://portal.gdc.cancer.gov/
2. Filter by: Program = TCGA, Project = TCGA-BRCA, Data Type = Gene Expression Quantification
3. Add to cart and download
4. Requires GDC client tool for bulk download

---

## Notes

- The notebook runs perfectly on **simulated data** (default) — no download needed to test the pipelines
- Real data will give you the actual PAM50 AUC numbers to put in your resume and README
- TCGA-BRCA has ~1,100 samples with ~20,000 genes — runtime on Colab GPU is ~5–10 min
