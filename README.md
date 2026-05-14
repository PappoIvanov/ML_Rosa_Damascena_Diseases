# Disease Detection and Treatment Recommendation for Rosa damascena Using Machine Learning

## Abstract

This project applies machine learning to support disease management decisions
in Rosa damascena (oil-bearing rose) cultivation. Using leaf photographs and
historical weather data from a field site in Krasnovo, Plovdiv Province, Bulgaria,
the system detects foliar diseases and insect damage, predicts outbreak risk from
meteorological conditions, and recommends appropriate treatment (fungicide,
insecticide, or no action). The project combines computer vision and tabular ML
into a unified decision-support pipeline.

---

## Research Questions

1. Can a convolutional neural network accurately distinguish between fungal diseases,
   insect damage, and healthy tissue on Rosa damascena leaves from field photographs?

2. Are meteorological variables (temperature, humidity, precipitation) sufficient
   to predict the risk of fungal disease outbreak for Rosa damascena under Bulgarian
   field conditions?

3. Does combining image-based disease classification with weather-based risk scoring
   improve the quality of fungicide treatment recommendations compared to either
   approach alone?

---

## Hypotheses

**H1 — Image Classification:**
A CNN model with MobileNet transfer learning will achieve greater than 80% classification
accuracy across 8 target classes (4 fungal diseases, Rose Mosaic Virus, 2 insect damage
classes, healthy) on Rosa damascena leaf images from combined public and field datasets.

**H2 — Weather-Based Risk Prediction:**
Temperature, relative humidity, and precipitation recorded in the 7 days prior to
observation are statistically significant predictors of fungal disease outbreak risk
for Rosa damascena at the Krasnovo field site.

**H3 — Treatment Recommendation:**
A treatment recommendation model combining image classification output with weather
risk score will reduce unnecessary spray applications compared to a calendar-based
spraying schedule, while maintaining disease control effectiveness.

---

## Target Classes

| Class | Type | Treatment |
|---|---|---|
| Black Spot (*Diplocarpon rosae*) | Fungal disease | Fungicide |
| Rose Rust (*Phragmidium mucronatum*) | Fungal disease | Fungicide |
| Powdery Mildew (*Podosphaera pannosa*) | Fungal disease | Fungicide |
| Downy Mildew (*Peronospora sparsa*) | Fungal disease | Fungicide |
| Rose Mosaic Virus | Viral disease | No chemical treatment |
| Rose Sawfly / Rose Slug | Insect damage | Insecticide |
| Insect Hole | Insect damage | Insecticide |
| Healthy | — | No treatment |

---

## Datasets

### Image Data
| Dataset | Source | Images | Format |
|---|---|---|---|
| rose_leaf_disease_dataset | Kaggle | 14,910 | Classification |
| rose_leaves_disease_detection | Kaggle | 917 | Classification |
| Multifaceted Rose Leaf Disease Dataset | Mendeley | 13,306 | Classification |
| rose leaf diseases.v4i.yolov11 | Roboflow | 3,702 | YOLO → converted |
| rose leaf detection.v1i.yolov11 | Roboflow | 2,174 | YOLO → converted |
| **Personal field dataset** | Krasnovo farm, Plovdiv Province | in progress | Classification |

### Tabular Data
| Dataset | Source | Records | Description |
|---|---|---|---|
| krasnovo_weather_2015_2024.csv | Open-Meteo API (ERA5) | 3,653 | Daily weather, 2015–2024 |
| gbif_rosa_diseases_europe.csv | GBIF API | 18,927 | Disease occurrence records, Europe |

---

## Methodology

The project is structured as a sequential pipeline across 8 notebooks:

| Notebook | Platform | Description |
|---|---|---|
| 01_data_preparation | Jupyter | API data download; image preprocessing (YOLO conversion, deduplication, resizing) |
| 02_dataset_evaluation | Jupyter | Image quality assessment (blur detection, resolution, duplicate analysis) |
| 03_eda | Jupyter | Exploratory analysis of all datasets |
| 04_traditional_ml | Google Colab | Logistic Regression and SVM from scratch (gradient descent, kernel functions) |
| 05_neural_network_scratch | Google Colab | Neural network from scratch using NumPy (backpropagation, chain rule) |
| 06_cnn_transfer_learning | Google Colab | CNN with MobileNet fine-tuning (transfer learning) |
| 07_weather_risk | Google Colab | Tabular ML: weather → disease risk prediction |
| 08_mlflow | Google Colab | Experiment tracking and model comparison |

---

## Project Structure

ML_Rosa_Damascena_Diseases/
├── data/
│   ├── raw/
│   │   ├── weather/
│   │   ├── gbif/
│   │   └── images/
│   └── processed/
│       ├── images/
│       └── weather/
├── notebooks/
├── models/
├── .gitignore
├── requirements.txt
└── README.md


---

## Field Site

- **Location:** Krasnovo, Plovdiv Province, Bulgaria
- **Coordinates:** 42.46667°N, 24.48333°E, elevation 363 m
- **Crop:** Rosa damascena (oil-bearing rose)
- **Weather source:** Open-Meteo Archive API (ERA5 reanalysis)

---

## Current Status

- [x] 01_data_preparation.ipynb — API data downloaded; image preprocessing in progress
- [x] 02_dataset_evaluation.ipynb — complete
- [ ] 03_eda.ipynb
- [ ] 04_traditional_ml.ipynb
- [ ] 05_neural_network_scratch.ipynb
- [ ] 06_cnn_transfer_learning.ipynb
- [ ] 07_weather_risk.ipynb
- [ ] 08_mlflow.ipynb

---

## Requirements

See `requirements.txt` for full dependency list.
Key libraries: `numpy`, `pandas`, `scikit-learn`, `opencv-python`,
`matplotlib`, `torch` / `tensorflow`, `mlflow`.

---

## Author

SoftUni Machine Learning Course Project  
Field site: Krasnovo, Plovdiv Province, Bulgaria

---

## References

### Datasets

[1] Basak, S. K. *Rose Leaf Disease Dataset*. Kaggle, 2023.  
https://www.kaggle.com/datasets/shuvokumarbasak4004/rose-leaf-disease-dataset

[2] Chauhan, C. *Rose Leaves Disease Detection*. Kaggle, 2023.  
https://www.kaggle.com/datasets/warcoder/rose-leaves-disease-detection

[3] Ahmad, M. H. *Multifaceted Rose Leaf Disease Dataset for AI-Driven*  
*Plant Health Monitoring*, Version 3. Mendeley Data, 2025.
https://doi.org/10.17632/8jtfk9szbg.3

[4] Rose Leaf Diseases. *Rose Leaf Diseases Dataset v4*. Roboflow Universe, 2023.  
https://universe.roboflow.com/rose-leaf-diseases/rose-leaf-diseases/dataset/4

[5] Rose Diseases. *Rose Leaf Detection Dataset v1*. Roboflow Universe, 2023.  
https://universe.roboflow.com/rose-diseases/rose-leaf-detection/dataset/1

### Weather Data

[6] Zippenfenig, P. *Open-Meteo.com Weather API*. Zenodo, 2023.  
https://doi.org/10.5281/zenodo.7970649

### Biodiversity Data

[7] GBIF.org. *Global Biodiversity Information Facility*. Accessed 2025.  
https://www.gbif.org

### Literature

*(to be completed as project progresses)*

