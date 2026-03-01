# 🔎 Moogle! — TF-IDF Search Engine with Blazor UI

![Language](https://img.shields.io/badge/Language-C%23-239120?logo=csharp&logoColor=white)
![Framework](https://img.shields.io/badge/Framework-Blazor%20Server-512BD4?logo=blazor)
![.NET](https://img.shields.io/badge/.NET-6.0-512BD4?logo=dotnet)
![Report](https://img.shields.io/badge/Report-LaTeX-008080)
![Status](https://img.shields.io/badge/Status-Complete-brightgreen)

**Moogle!** is a search engine for `.txt` document collections. Implements the **TF-IDF vector space model** with cosine similarity for document ranking, **Levenshtein distance** for query spell-check suggestions, and **snippet extraction** for result previews. Features a responsive **Blazor Server** web interface and includes a comprehensive LaTeX academic report.

---

## 📑 Table of Contents

- [Features](#features)
- [Tech Stack](#tech-stack)
- [Project Structure](#project-structure)
- [How to Build & Run](#how-to-build--run)
- [How It Works](#how-it-works)
- [Academic Context](#academic-context)

---

## ✨ Features

- **TF-IDF Vectorial Model** — Each document and query represented as weighted term vectors
- **Cosine Similarity Ranking** — Documents ranked by angle between query and document vectors
- **Levenshtein Distance** — "Did you mean?" suggestions for misspelled query terms
- **Snippet Extraction** — Relevant text excerpts shown alongside each search result
- **Blazor Web Interface** — Modern, responsive single-page application for searching
- **LaTeX Academic Report** — Formal documentation of algorithms, design, and results

---

## 🛠 Tech Stack

| Component       | Technology          |
|-----------------|---------------------|
| Language         | C#                 |
| Web Framework    | Blazor Server      |
| Runtime          | .NET 6             |
| IR Model         | TF-IDF + Cosine    |
| Documentation    | LaTeX              |

---

## 📁 Project Structure

```
Moogle-PRO-2023/
├── MoogleEngine/              # Search engine core
│   ├── Moogle.cs              # Main search orchestrator
│   ├── TF-IDF classes         # Term frequency and inverse document frequency
│   ├── Levenshtein.cs         # Edit distance for query suggestions
│   └── Snipet.cs              # Snippet extraction from documents
├── MoogleServer/              # Blazor Server web application
│   ├── Pages/                 # Razor pages (search UI)
│   └── Program.cs             # Web host entry point
├── Informe/
│   └── Informe.tex            # LaTeX academic report
└── Content/                   # .txt document corpus
```

---

## 🚀 How to Build & Run

### Prerequisites

- .NET 6 SDK

### Build & Run

```bash
dotnet run --project MoogleServer
```

Then open your browser at `https://localhost:5001` (or the displayed URL).

### Compile Report

```bash
cd Informe && pdflatex Informe.tex
```

---

## ⚙️ How It Works

### Indexing Phase

1. **Document Loading** — Reads all `.txt` files from the content directory.
2. **Tokenization** — Splits each document into terms (words), normalizing case and removing punctuation.
3. **TF Calculation** — Computes term frequency for each term in each document.
4. **IDF Calculation** — Computes inverse document frequency across the entire corpus: $IDF(t) = \log\frac{N}{df(t)}$
5. **TF-IDF Vectors** — Each document is represented as a vector of $TF \times IDF$ weights.

### Query Phase

1. **Query Vectorization** — The user's query is tokenized and converted to a TF-IDF vector.
2. **Cosine Similarity** — The angle between the query vector and each document vector is computed:

$$\cos(\theta) = \frac{\vec{q} \cdot \vec{d}}{|\vec{q}| \cdot |\vec{d}|}$$

3. **Ranking** — Documents are sorted by descending similarity score.
4. **Snippet Extraction** — For each top result, the most relevant text passage is extracted.
5. **Suggestions** — If a query term is not found, Levenshtein distance finds the closest known term as a "Did you mean?" suggestion.

---

## 🎓 Academic Context

> **Course Project** — Programming, University of Havana, 2023
