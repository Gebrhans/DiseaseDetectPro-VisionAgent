# 🌿 DiseaseDetectPro VisionAgent

**DiseaseDetectPro VisionAgent** is an agentic computer-vision system for explainable crop disease detection. It combines OpenCV-based visual perception, EfficientNet-CBAM classification, Grad-CAM++ explainability, and an agentic decision layer to support rapid and responsible crop disease screening.

The system is designed for farmers, agricultural extension workers, researchers, and plant-health experts who need fast preliminary disease screening with transparent visual evidence.

---

## 🚀 Key Features

- **OpenCV-based image perception**
  - Image-quality assessment
  - Blur, brightness, saturation, and contrast analysis
  - Leaf-region segmentation
  - Region-of-interest extraction
  - Image enhancement and denoising

- **Agentic decision-making**
  - Accepts suitable images for classification
  - Rejects blurry, dark, overexposed, or non-leaf images
  - Requests additional evidence for uncertain predictions
  - Escalates moderate-confidence cases for human review

- **EfficientNet-CBAM classification**
  - EfficientNet-B0 backbone
  - Channel and spatial attention using CBAM
  - Supports custom crop-disease classes

- **Explainable AI**
  - Grad-CAM++ visual explanations
  - Highlights image regions influencing the prediction

- **Web demonstration**
  - Gradio-based upload interface
  - Displays prediction, confidence, agent trace, and Grad-CAM++ output

- **AWS-ready architecture**
  - Designed for deployment using Amazon EC2, S3, API Gateway, Lambda, CloudWatch, and IAM
  - Includes optional S3 artifact-upload utilities

---

## 🧠 System Workflow

```text
User uploads crop-leaf image
            ↓
OpenCV Perception Module
            ↓
VisionAgent evaluates image quality and leaf coverage
            ↓
Unsuitable image → Request new image
Suitable image ↓
EfficientNet-CBAM Disease Classification
            ↓
Grad-CAM++ Explanation
            ↓
VisionAgent evaluates confidence
            ↓
Diagnosis / Human Review / Request Additional Evidence
            ↓
Gradio Web Interface
```

---

## 🛠️ Technologies Used

| Component | Technology |
|---|---|
| Image perception | OpenCV |
| Deep-learning model | PyTorch, timm |
| Classification backbone | EfficientNet-B0 |
| Attention mechanism | CBAM |
| Explainability | Grad-CAM++ |
| Agent orchestration | Custom Python VisionAgent |
| Web interface | Gradio |
| Cloud readiness | AWS S3, EC2, API Gateway, Lambda, CloudWatch, IAM |

---

## 📁 Project Structure

```text
DiseaseDetectPro-VisionAgent/
│
├── README.md
├── requirements.txt
├── DiseaseDetectPro_VisionAgent_Colab.ipynb
│
├── src/
│   ├── perception_opencv.py
│   ├── model_efficientnet_cbam.py
│   ├── explainability_gradcam.py
│   └── vision_agent.py
│
├── app/
│   └── gradio_app.py
│
├── docs/
│   ├── architecture.md
│   ├── aws_deployment.md
│   └── evaluation_plan.md
│
└── .gitignore
```

---

## 📓 Google Colab Prototype

The complete runnable prototype is provided in:

```text
DiseaseDetectPro_VisionAgent_Colab.ipynb
```

The notebook includes:

1. Dependency installation  
2. EfficientNet-CBAM model creation  
3. Optional training on a custom crop-disease dataset  
4. OpenCV image-quality and leaf-region analysis  
5. VisionAgent decision logic  
6. Grad-CAM++ explanation generation  
7. Gradio web application  
8. Optional AWS S3 integration  

---

## 📦 Installation

```bash
git clone [https://github.com/Gebrhans/DiseaseDetectPro-VisionAgent.git](https://github.com/Gebrhans/DiseaseDetectPro-VisionAgent.git)
cd DiseaseDetectPro-VisionAgent
pip install -r requirements.txt
```

---

## ▶️ Running the Web Application

```bash
python app/gradio_app.py
```

Then open the local Gradio URL shown in the terminal.

---

## 🌾 Dataset Format

To train the model on your own dataset, organize the images as follows:

```text
dataset/
│
├── Healthy/
├── Bacterial_leaf_blight/
├── Brown_spot/
├── Leaf_smut/
├── Tomato_Late_blight/
└── Tomato_Early_blight/
```

Each folder name becomes a class label. Replace the class folders with your actual crop-disease categories.

---

## 🤖 Agent Decision Rules

| Condition | Agent Action |
|---|---|
| Image is blurry, too dark, overexposed, or has insufficient leaf tissue | `REQUEST_NEW_IMAGE` |
| Image passes OpenCV quality checks | Proceed to EfficientNet-CBAM classification |
| Confidence ≥ 60% | `RETURN_DIAGNOSIS` |
| Confidence between 45% and 59% | `HUMAN_REVIEW` |
| Confidence < 45% | `REQUEST_ADDITIONAL_EVIDENCE` |

---

## ☁️ Planned AWS Architecture

```text
Web Application
      ↓
Amazon API Gateway
      ↓
AWS Backend / Amazon EC2
      ↓
VisionAgent
      ↓
OpenCV → EfficientNet-CBAM → Grad-CAM++
      ↓
Amazon S3
      ↓
CloudWatch Monitoring
      ↓
Result / Request New Image / Human Review
```

AWS services support scalable inference, secure storage, API access, monitoring, and least-privilege access control.

---

## ⚠️ Responsible Use

This system provides **AI-assisted preliminary screening**, not a final plant-pathology diagnosis. Farmers and extension workers should confirm important treatment decisions with qualified agricultural experts, especially for uncertain or high-impact cases.

---

## 👤 Author

**Gebrhans Weldegebriel Weldergs**  
Computer Science Lecturer | AI Researcher | Software Developer  

- GitHub: [https://github.com/Gebrhans](https://github.com/Gebrhans)
- ORCID: [https://orcid.org/0009-0006-9602-4104](https://orcid.org/0009-0006-9602-4104)

---

## 📄 License

This project is released under the MIT License.
