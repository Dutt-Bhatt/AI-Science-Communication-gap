# The Illusion of Competence: AI vs. Primary Scientific Literature

## Overview
This computational biology project quantifies the readability gap between primary molecular biology literature and AI-generated summaries. By programmatically analyzing abstracts from PubMed and processing them through Google's Gemini LLM, this pipeline mathematically demonstrates the "illusion of competence"—the phenomenon where AI oversimplifies complex biological mechanisms, stripping away the technical friction required for genuine academic comprehension.

## Methodology
1. **Data Acquisition:** Utilized `Biopython` (Entrez API) to automatically fetch 50 recent peer-reviewed abstracts relating to the "insulin signaling pathway" from the NCBI PubMed database.
2. **Baseline Scoring:** Applied the `textstat` library to calculate the Flesch-Kincaid Grade Level of the original literature, establishing the baseline cognitive load (years of education required).
3. **LLM Processing:** Constructed an automated, rate-limited pipeline using the `google-genai` SDK to process all 50 abstracts through the `gemini-3.5-flash` model, prompting it to generate simplified explanations.
4. **Comparative Analysis:** Recalculated readability metrics on the AI outputs and visualized the delta using `pandas` and `seaborn`.

## Key Findings
* **Original PubMed Abstracts:** Averaged a **19.7 Grade Level** (requiring post-graduate education to fully comprehend).
* **AI-Generated Summaries:** Averaged a **14.8 Grade Level** (equivalent to early undergraduate/high school reading levels).
* **Conclusion:** The pipeline proved a mathematically significant **4.9 grade-level drop** in reading complexity. This confirms that while LLMs make primary literature highly accessible, they aggressively remove the dense mechanistic terminology necessary for rigorous biomedical research.

## Technical Stack
* **Language:** Python 3
* **APIs:** NCBI E-Utilities (PubMed), Google Gemini API (`gemini-3.5-flash`)
* **Libraries:** `pandas` (Data manipulation), `biopython` (NCBI querying), `textstat` (NLP readability metrics), `seaborn` & `matplotlib` (Data visualization), `tqdm` (Pipeline tracking)

## Repository Structure
* `readability_analysis.ipynb`: The primary Jupyter Notebook containing the full execution pipeline and visualizations.
* `insulin_readability_gap.csv`: The exported dataset containing the PMIDs, original texts, AI summaries, and comparative scores.
* `requirements.txt`: Environment dependencies for reproducibility.

## How to Run
1. Clone this repository.
2. Install dependencies via `pip install -r requirements.txt`.
3. Provide your own Google Gemini API key and NCBI Entrez email address in the notebook's designated authentication blocks.
4. Run the Jupyter Notebook sequentially.