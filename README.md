![Python](https://img.shields.io/badge/Python-3.13.7-blue?logo=python&logoColor=white)
![Scikit-learn](https://img.shields.io/badge/scikit--learn-F7931E?logo=scikit-learn&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-150458?logo=pandas&logoColor=white)
![Streamlit](https://img.shields.io/badge/Streamlit-FF4B4B?logo=streamlit&logoColor=white)
![XGBoost](https://img.shields.io/badge/XGBoost-337AB7?logo=xgboost&logoColor=white)
![SHAP](https://img.shields.io/badge/SHAP-FF6B6B?logo=python&logoColor=white)


# 🫀 Love Your Heart: Interactive Heart Risk Predictor with Machine Learning

An end-to-end machine learning project that predicts heart disease risk using clinical, lifestyle, and demographic data. The system combines a calibrated voting classifier with SHAP-based explainability and an AI-powered chatbot to provide personalized, actionable health insights.

**Final Project** | WBS Data Science Bootcamp | 2.5 Weeks  
**Team:** [theHPhub](https://github.com/theHPhub), [NadineJac](https://github.com/NadineJac)

## 🎯 Project Overview
This project builds an ML-powered heart disease risk prediction system deployed as an interactive Streamlit web application. Users input their health profile and receive:
- **Risk probability score** (0-100%) with optimized threshold-based risk categories
- **Personalized explanations** via SHAP values showing which factors drive their risk
- **AI chatbot assistance** using RAG (Retrieval-Augmented Generation) for tailored lifestyle guidance

The model prioritizes **high recall** to minimize false negatives—ensuring high-risk individuals are identified—while maintaining acceptable precision through careful threshold optimization (0.19 cutoff).

🔗 [**Live App**](https://loveyourheart.streamlit.app) | 📄 [**Full Documentation**](DOCUMENTATION.md)

## 📊 Dataset & Sources
- **Data source:** [BRFSS 2020 Heart Disease Dataset](https://zenodo.org/records/15364962)  
- **Dataset size:** 320,000+ records with 18 features  
- **Key features:** 
  - Demographics: Age, Sex, Race, BMI
  - Medical history: Stroke, Diabetes, Kidney Disease, Asthma, Skin Cancer
  - Lifestyle factors: Smoking, Alcohol, Physical Activity, Sleep Time
  - Health metrics: Physical Health days, Mental Health days, Difficulty Walking, General Health
- **Challenge:** Severe class imbalance (~8% positive cases)
- **Preprocessing:** Train-test split (80-20, stratified), OneHotEncoder for categoricals, StandardScaler for numericals, SMOTE oversampling, probability calibration

## 🚀 Key Findings & Results
- **Final Model:** Voting Classifier ensemble (Logistic Regression + Random Forest + XGBoost + CatBoost)
- **Performance:** 
  - Average Recall: [add]
  - Optimized threshold: 0.19 (balances high recall with manageable false positives)
  - Significantly improved minority class detection vs. individual models
- **Top Risk Factors (via SHAP):**
  - Age, General Health, Stroke history
  - Smoking, Diabetic status, Difficulty Walking
  - BMI, Physical Health days
- **Explainability:** SHAP KernelExplainer provides transparent, feature-level explanations with "What-If" scenario analysis
- **Chatbot:** RAG-powered assistant using Groq's Llama 3.3 70B + multilingual embeddings, grounded in cardiovascular health guidelines

## 🛠️ Technologies Used
- **Programming Language:** Python 3.13  
- **ML Libraries:** scikit-learn, XGBoost, CatBoost, imbalanced-learn (SMOTE), SHAP  
- **Data Processing:** pandas, numpy  
- **Visualization:** seaborn, matplotlib, plotly  
- **Deployment:** Streamlit  
- **AI/NLP:** Groq API (Llama 3.3 70B), sentence-transformers, vector database  
- **Tools:** Jupyter Notebook, Git

## 📁 Project Structure
```
app/                           # Streamlit web application
data/
├── heart_2020_cleaned.csv     # Preprocessed BRFSS dataset
images/                        # EDA visualizations and model performance plots
models/                        # Trained voting classifier and preprocessing pipeline
notebooks/
│ ├── 01_EDA.ipynb            # Exploratory data analysis
│ └── 02_modeling.ipynb       # Model training, tuning, and evaluation
presentation/                  # Final project presentation
requirements.txt
LICENSE
README.md
DOCUMENTATION.md              # Comprehensive technical documentation
```

## 🔗 How to Use This Project

### Access the Live App
Visit [loveyourheart.streamlit.app](https://loveyourheart.streamlit.app) to use the deployed application immediately.

### Local Setup
1. **Clone this repository**  
```bash
   git clone https://github.com/theHPhub/LoveYourHeart.git
   cd LoveYourHeart
```

2. **Install dependencies**
```bash
   pip install -r requirements.txt
```

3. **Set up API keys** (for chatbot functionality)
   
   **For local notebook usage:**
   Create a `keys.py` file in the root directory with:
```python
   GROQ_API_KEY = "your_groq_api_key_here"
   HF_TOKEN = "your_huggingface_token_here"
```
   
   **For Streamlit app:**
   Create a `.streamlit/secrets.toml` file with:
```toml
   GROQ_API_KEY = "your_groq_api_key_here"
   HF_TOKEN = "your_huggingface_token_here"
```

4. **Run the notebooks**
   - Start with [heart_risk_model_improve2.ipynb](notebooks/heart_risk_model_improve2.ipynb) for model development
   - The used mdel is in [heart_risk_votingModel.ipynb](notebooks/heart_risk_votingModel.ipynb)

5. **Launch the Streamlit app locally**
```bash
   streamlit run app/main.py
```

All generated plots and results will be saved in the `images/` folder.


## 🚀 Future Work
- **Enhance clinical features:** Integrate lab results (cholesterol, blood pressure), medication history, and genetic risk factors
- **Time-series monitoring:** Track longitudinal health trends (weight, activity, vitals) for dynamic risk updates
- **Medical imaging integration:** Incorporate ECG or imaging-derived biomarkers for improved accuracy
- **Mobile app development:** Build API and native app with wearable device integration
- **Population calibration:** Adapt model for German/European populations beyond US-based BRFSS data
- **Continuous learning:** Implement model monitoring and retraining pipelines with real-world feedback

## ⚠️ Limitations
- **Data source:** Based on self-reported US survey data (BRFSS 2020), which may not generalize well to other populations
- **False positives:** Optimized for high recall, resulting in some overestimation of risk
- **Snapshot prediction:** Cross-sectional data provides associations, not causal relationships
- **Missing clinical data:** Lacks lab results, imaging, and medication information that would improve accuracy

## 📜 License
This project is released under the [MIT License](LICENSE).

---

**Note:** This tool is for educational and informational purposes only. It does not replace professional medical advice, diagnosis, or treatment. Always consult with a qualified healthcare provider regarding your heart health.
