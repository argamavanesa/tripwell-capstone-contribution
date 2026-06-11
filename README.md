# TripWell — AI-Powered Inclusive Tourism Portal

> **Coding Camp 2026 powered by DBS Foundation × Dicoding — Capstone Project**

TripWell is a Deep Learning-powered inclusive tourism platform designed to help users identify whether a tourist destination is accessible for people with mobility limitations — including wheelchair users, elderly visitors, and families with strollers.

The AI system automatically classifies Indonesian tourism reviews into:
- ✅ **Ramah Disabilitas** (Disability-Friendly)
- ⚠️ **Akses Terbatas** (Limited Accessibility)

---

## 🔗 Live Deployments

| Platform | Link |
|---|---|
| 🌐 Website | [tripwellcaps.vercel.app](https://tripwellcaps.vercel.app/) |
| 📊 Dashboard | [dashboard-tripwell.streamlit.app](https://dashboard-tripwell.streamlit.app/) |
| 🤖 Model API | [tripwellcaps.up.railway.app](https://tripwellcaps.up.railway.app/) |

📄 [Final Pitch Deck](https://drive.google.com/file/d/123wdfgAIN8KDqKtx804_yZ4fgUF47T35/view?usp=sharing)

---

## 🧩 Problem Statement

Tourism in Indonesia remains largely inaccessible for people with disabilities due to two core barriers:
1. **Limited physical infrastructure** at destinations (ramps, accessible toilets, parking, etc.)
2. **Lack of accessible pre-trip information** — users cannot assess a destination's accessibility before visiting

TripWell addresses the second barrier by automatically surfacing and classifying accessibility-related insights from existing public tourism reviews using NLP.

---

## 🤖 AI Model

The classification model uses a **Bidirectional LSTM (BiLSTM)** architecture built with TensorFlow Functional API:

```
Embedding → SpatialDropout1D → BiLSTM → BiLSTM → GlobalMaxPooling1D → Dense → Dropout → Output
```

- **Dataset:** ~12,000 Indonesian tourism reviews with 3 accessibility labels (positive, neutral, negative)
- **Training strategy:** Neutral labels excluded; class weights applied to address imbalance; synonym swap augmentation
- **Final accuracy:** 83% with balanced precision (0.83) for both classes — no significant bias toward majority class

---

## 🏗️ Architecture & Tech Stack

| Layer | Technology |
|---|---|
| Frontend | Next.js + NextAuth |
| Backend | Flask RESTful API |
| Database | PostgreSQL |
| AI Model | TensorFlow / Keras (BiLSTM) |
| Dashboard | Streamlit |
| Deploy (FE) | Vercel |
| Deploy (API) | Railway |
| Dev Tools | GitHub, Figma, Google Colab, VS Code |

---

## 👥 Team

| Name | Role |
|---|---|
| Muhammad Hasbi Ramadhani | Data Scientist |
| Annisa Sahindar | Full-Stack |
| Okky Puspa Ningrum | AI Engineer |
| Laily Khoiriyah Isnaini | AI Engineer |
| Rumaisya | Full-Stack |
| Argama Vanesa Nauli Sijabat | Data Scientist |

---

## 👩‍💻 My Role — Data Analysis & Preprocessing

**Argama Vanesa Nauli Sijabat** · Data Scientist

### Data Wrangling
- Sourced dataset from [Kaggle: ABSA Natural Tourist Attractions Review](https://www.kaggle.com/datasets/dzzlr07/absa-natural-tourist-attractions-review)
- Assessed raw data quality via Google Colab
- Resolved missing values, removed duplicates
- Applied label encoding for `accessibility`, `facility`, and `activity` columns using ordinal encoding (positive > neutral > negative)

![Data Wrangling Preview](images/data-wrangling-preview-fixed.png)

### Text Preprocessing (for BiLSTM Modelling)
- Lowercasing, noise cleaning, punctuation removal
- Slang normalization using custom dictionary
- Quality checks to ensure data is fit for sequence modelling
- Filtering: neutral labels excluded, binary classification retained

### Exploratory Data Analysis

![EDA Overview](images/eda-preview.png)

- Distribution analysis of accessibility labels (majority neutral → class imbalance identified)
- Destination-level breakdown of sentiment proportions
- Temporal trend analysis (2019–2023) of review volume and sentiment
- c-TF-IDF discriminative keyword analysis per class
- Data visualization for team and stakeholder communication

---

## 💡 Key Insights

### 📍 Top Negative Accessibility Location
**Curug Malela** is a significant outlier with the highest proportion of negative accessibility reviews (**52.5%**), the only destination where negative sentiment is dominant. The next-lowest locations (Bukit Senyum, Curug Layung, Stone Garden, Sanghyang Heuleut) are dominated by neutral reviews (77–81%), with average ratings of 4.39–4.56 vs. the dataset average of 4.5.

### 🔤 Discriminative Linguistic Patterns (c-TF-IDF)
Negative reviews are driven by infrastructure keywords: `jalan` (road), `akses` (access), and bigrams like `kurang bagus` (not good), `masih jelek` (still bad), `saat hujan` (during rain). Positive reviews cluster around convenience: `sangat mudah` (very easy), `lokasi mudah` (easy location). Notably, `tiket masuk` (entrance ticket) appears across both classes as a polarized sentiment driver.

### 📅 Temporal & Seasonal Trends (2019–2023)
Accessibility sentiment proportions and monthly average ratings remained largely stable with no clear seasonal patterns. A sharp drop in review volume occurred in mid-2022 (~1,850 → ~200 reviews/month), likely reflecting post-pandemic effects, which introduced higher statistical volatility in sentiment proportions through 2022–2023.

---

## 🚀 Getting Started

```bash
# 1. Clone the repository
git clone https://github.com/lailykhoiriyah/capstoneproject.git
cd capstoneproject

# 2. Install dependencies
npm install

# 3. Run development server
npm run dev

# 4. Build for production
npm run build
```

---

## 🛠️ Tools

![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![TensorFlow](https://img.shields.io/badge/TensorFlow-FF6F00?style=for-the-badge&logo=tensorflow&logoColor=white)
![Streamlit](https://img.shields.io/badge/Streamlit-FF4B4B?style=for-the-badge&logo=streamlit&logoColor=white)
![Google Colab](https://img.shields.io/badge/Google_Colab-F9AB00?style=for-the-badge&logo=googlecolab&logoColor=black)
