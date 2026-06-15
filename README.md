# Automated Human-in-the-Loop (HiTL) Quality Audit Engine

An asynchronous "Check the Checker" (CTC) quality assurance pipeline designed to audit distributed human workforce annotations. Built using the **LangChain Expression Language (LCEL)** framework and **Gemini 2.5 Flash**, this system programmatically verifies data classifications and structural HTML/XML node layouts against a formal taxonomy rubric used for email content extraction via human defined xpath.

## 🛠️ The Operational Context
In high-volume human-in-the-loop data pipelines, manual quality sampling scales poorly and struggles to flag precise technical errors. This project automates row-by-row data verification by passing labeling outputs through an LLM constraint layer, catching critical misalignments—such as when an annotator correctly identifies text semantics but provides an incorrect or overly narrow structural **XPath selector**.

### Key Pipeline Capabilities:
* **Context-Aware Taxonomy Mapping:** Validates human classifications against rigid enterprise domain criteria (e.g., separating semantic business unit entities from boilerplate text noise).
* **Deterministic Structured JSON Generation:** Employs Pydantic schema wrappers to suppress verbose, conversational AI responses, forcing guaranteed machine-readable outputs.
* **Automated Root-Cause Analysis:** Appends actionable operational reasoning directly back into the output dataset for seamless triage.

## 🧱 Technical Architecture Flow
The processing sequence strings sequential data manipulation elements together via an immutable runtime pipeline:
`Raw Excel Rows ➔ Pandas Serialization ➔ LangChain PromptTemplate ➔ Zero-Temperature LLM Engine ➔ Pydantic Output Parser ➔ Final Audit Workbook`

## 🚀 How to Run the Project
1. Clone or download this repository.
2. Install the core Python environment requirements:
   ```bash
   pip install langchain langchain-google-genai pandas openpyxl pydantic
   Open llm-ctc-audit-pipeline.ipynb within a Jupyter Notebook environment.

Provide your developer API credentials within the initialization cells and run the steps sequentially to evaluate human_labeled_emails.xlsx.
