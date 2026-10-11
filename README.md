# 🐾 PawCare AI — Dog Skin Disease Knowledge RAG Assistant

An AI-powered question-answering system that uses **Retrieval-Augmented Generation (RAG)** to provide information about dog skin conditions from a structured Markdown knowledge base.

## Project Overview

PawCare AI is a knowledge-based assistant designed to help users access information about dog skin diseases, possible symptoms, warning signs, and veterinary guidance.

The system retrieves relevant information from its knowledge base and uses a language model to generate an answer based on the retrieved content. It also displays the source file to help users verify where the information came from.

This project is an educational prototype and does not replace professional veterinary diagnosis or treatment.

## Objectives

- Build a question-answering system using RAG.
- Organize domain-specific information using Open Knowledge Format (OKF)-style Markdown notes.
- Retrieve relevant information using semantic similarity.
- Generate context-based answers using a small language model.
- Display source filenames alongside generated answers.
- Provide a simple user interface using Gradio.
- Measure and improve response time and answer quality.

## 🛠️ Technologies Used

| Technology | Purpose |
|---|---|
| Python | Core implementation |
| Google Colab | Development and experimentation |
| Qwen2.5-0.5B-Instruct | Answer generation |
| all-MiniLM-L6-v2 | Semantic retrieval using text embeddings |
| Sentence Transformers | Embedding generation |
| Gradio | Interactive user interface |
| Markdown and YAML | Knowledge organization and metadata |
| Git and GitHub | Version control and project hosting |

## 🧠 System Architecture

The system follows a Retrieval-Augmented Generation workflow:

1. **User Input:** The user enters a question about dog skin health.
2. **Knowledge Loading:** Python loads Markdown files from the `knowledge/` directory.
3. **Chunking:** Each note is divided into smaller sections using Markdown `##` headings.
4. **Semantic Retrieval:** `all-MiniLM-L6-v2` helps retrieve relevant knowledge chunks.
5. **Answer Generation:** Qwen2.5-0.5B-Instruct generates a response using the retrieved information as context.
6. **Source Display:** The application displays the answer and its source filename.
7. **Trust Check:** Metadata can be checked for draft status, missing verification information, and outdated notes.

## 📂 Project Structure

```text
PawCare-AI-RAG/
│
├── Dog_Skin_Disease_RAG.ipynb
├── README.md
│
└── knowledge/
    ├── skin/
    │   ├── allergic-dermatitis.md
    │   ├── bacterial-infections.md
    │   ├── fungal-infections.md
    │   └── warning-signs.md
    │
    └── care/
        └── veterinary-guidance.md
```

*Note: Update the notebook filename in this structure if your actual filename is different.*

## 📚 Knowledge Base and OKF

The knowledge base contains five Markdown files covering:

- Allergic dermatitis
- Bacterial skin infections
- Fungal skin infections
- Warning signs
- Veterinary guidance

Each note uses a structured format with YAML metadata and Markdown headings.

Example:

```yaml
---
type: Notes
title: Allergic Dermatitis
description: Information about allergic dermatitis
status: stable
---
```

The note content is organized into sections using `##` headings. This allows the application to split documents into smaller chunks for retrieval.

The project also includes a trust-check mechanism that flags notes requiring review.

## ⚙️ Installation and Setup

### Option 1: Run in Google Colab

1. Open the project notebook in Google Colab.
2. Save a copy to your Google Drive.
3. Run the setup cells in order.
4. Load the knowledge files from the `knowledge/` directory.
5. Run the semantic retrieval and answer-generation cells.
6. Launch the Gradio interface.
7. Open the generated Gradio link to test the application.

### Option 2: Install dependencies locally

Create a Python environment and install the required packages:

```bash
pip install gradio transformers sentence-transformers torch numpy pandas matplotlib pyyaml
```

Additional dependencies may be needed depending on the notebook implementation.

Make sure the knowledge files are available at the expected paths before running the application.

## Example Usage

**Example question:**

"What are possible signs of allergic dermatitis?"

**Expected workflow:**

- Retrieve the most relevant section from the knowledge base.
- Pass the retrieved content and question to the language model.
- Generate an answer based on the supplied context.
- Display the answer and source filename.

The exact answer depends on the contents of the knowledge notes and the model output.

## Response Time Optimization

Potential improvements include:

- Loading the language model only once.
- Reusing precomputed embeddings for knowledge chunks.
- Limiting the number of generated tokens.
- Measuring retrieval and generation time separately.
- Avoiding unnecessary model reinitialization.

Actual performance depends on the hardware, model initialization, and runtime environment.

## Evaluation

The system should be tested using questions that are both covered and not covered by the knowledge base.

Evaluation should record:

- Whether the correct knowledge chunk was retrieved.
- Whether the generated answer is supported by the retrieved note.
- Whether the correct source file is displayed.
- Retrieval time and answer-generation time.
- Cases where retrieval or generation fails.

Add your actual evaluation results after running the tests. Do not report unmeasured accuracy or response-time improvements.

## Limitations

- The current knowledge base is small.
- Retrieval may select an irrelevant or incomplete chunk.
- The language model may generate unsupported information.
- Response time depends on the available hardware and model loading.
- Knowledge notes require verification and periodic maintenance.
- The application is not a diagnostic tool and should not be used as a substitute for veterinary care.

## Future Enhancements

- Expand the knowledge base with verified veterinary resources.
- Improve retrieval quality and evaluate alternative embedding models.
- Add a more conversational chat interface.
- Improve response speed through model and inference optimization.
- Add automated evaluation and source-grounding checks.
- Deploy the application for reliable, persistent access.

## Project Status

**Status:** Working prototype under development.

The project includes a structured knowledge base, semantic retrieval, language-model answer generation, and a planned or developing Gradio interface. Further testing is needed to establish retrieval quality, answer reliability, and response-time performance.

## Disclaimer

PawCare AI provides educational information about dog skin health. It cannot diagnose diseases or prescribe treatment. Consult a qualified veterinarian for medical concerns, persistent symptoms, or emergencies.

## License

Choose and add an appropriate open-source license before distributing this project. Check the licenses of all models, datasets, and dependencies separately.
