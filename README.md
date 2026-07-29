# Concrete Bridge Deck Crack Detection

Binary image classification app (Cracked vs Non-cracked) built for **GET 324 — Laboratory
Exercise 10 (Mini-Project): Cloud Computing and AI Model Deployment for Engineering Applications**.

## Problem statement
Bridge decks and other concrete structures develop surface cracks over time. This project trains
a Convolutional Neural Network to automatically classify an image of a concrete surface as
**Cracked** or **Non-cracked**, then deploys the model as a Streamlit web application.

## Dataset
"Concrete Crack Images for Classification" — Ozgenel, C.F. & Gonenc Sorguc, A. (2018),
Mendeley Data, V2, DOI: 10.17632/5y9wdsg2zt.2 (also mirrored on Kaggle as
`arunrk7/surface-crack-detection`). 40,000 real photographs (227x227 px) of concrete surfaces
from METU campus buildings, evenly split between cracked and non-cracked classes. No synthetic
data was used.

## Models trained
1. **Custom CNN** — 3 convolutional blocks with batch normalisation and max-pooling, trained from
   scratch.
2. **MobileNetV2 (transfer learning)** — ImageNet-pretrained backbone, frozen then fine-tuned.

Both models are trained, evaluated, and compared inside
`notebooks/GET324_Crack_Detection_MiniProject.ipynb` using accuracy, precision, recall, a
confusion matrix, and ROC-AUC on a held-out test split. The better-performing model is exported
to `model/crack_detector.keras` and used by the app.

## Repository structure
```
concrete-crack-detector/
├── app.py                  # Streamlit application
├── requirements.txt        # Python dependencies
├── README.md
├── model/
│   └── crack_detector.keras
└── notebooks/
    └── GET324_Crack_Detection_MiniProject.ipynb
```

## Running locally
```bash
git clone https://github.com/<your-username>/concrete-crack-detector.git
cd concrete-crack-detector
pip install -r requirements.txt
streamlit run app.py
```
Then open the local URL Streamlit prints (usually http://localhost:8501).

## Using the app
1. Open the deployed app URL (or the local URL above).
2. Upload a photo of a concrete surface (`.jpg`, `.jpeg`, or `.png`).
3. The app displays the predicted class (**Cracked** / **Non-cracked**) and a confidence score.

## Deployment
Deployed on **Streamlit Community Cloud**: `https://<your-app-name>.streamlit.app`
(replace with your actual deployed URL before submission).

 Git, GitHub, and Streamlit Cloud deployment (CLO7)
Run these commands on your local machine or in a terminal (not required to execute inside Colab) after downloading app.py, requirements.txt, the model/ folder, and this notebook.

11.1 Recommended repository structure
concrete-crack-detector/
├── app.py
├── requirements.txt
├── README.md
├── model/
│   └── crack_detector.keras
└── notebooks/
    └── GET324_Crack_Detection_MiniProject.ipynb
11.2 Initialise Git and push to GitHub
git init
git add .
git commit -m "Initial commit: concrete crack detection app"
git branch -M main
git remote add origin https://github.com/<your-username>/concrete-crack-detector.git
git push -u origin main
11.3 Deploy on Streamlit Community Cloud
Go to https://share.streamlit.io and sign in with GitHub.
Click New app, choose your repository, branch main, and main file path app.py.
Click Deploy. Streamlit installs requirements.txt and starts the app automatically.
Copy the generated public URL (e.g. https://concrete-crack-detector.streamlit.app) — this is your deliverable #3.
If the model file is too large for GitHub's normal limits, use Git LFS (git lfs track "*.keras") or host the model on Google Drive / Hugging Face and download it inside app.py at startup with gdown or huggingface_hub.

## Team
See the notebook header for the full list of team members, registration numbers, and individual
contributions.

## Citation
Ozgenel, C.F. (2019), "Concrete Crack Images for Classification", Mendeley Data, V2,
doi: 10.17632/5y9wdsg2zt.2. Licensed under CC BY 4.0.


from google.colab import files
files.download('README.md')
