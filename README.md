<picture>
  <source media="(prefers-color-scheme: dark)" srcset="./assets/banner-dark.svg">
  <img src="./assets/banner-light.svg" alt="Huy Nguyen: biomedical computer vision and agentic LLM systems" width="100%">
</picture>

I work on two things that turn out to need the same discipline: computer vision for embryo and chromosome imaging at **ICIP Lab (Saigon University)**, and agentic LLM systems that people actually use. In both, the rule is the same: measure it, and make every claim traceable to its evidence.

<table>
<tr>
<td width="50%" valign="top">

**Research**

Oriented object detection, self-supervised encoders, and constraint-aware post-processing for medical imaging. Work with Hung Vuong Hospital, published in a Scopus Q1 journal.

</td>
<td width="50%" valign="top">

**Engineering**

Agentic RAG with fine-tuned retrieval, human-in-the-loop procurement agents, and the serving layer underneath: vLLM, Triton, PostgreSQL, Terraform. Two systems are live.

</td>
</tr>
</table>

<p>
  <a href="https://doi.org/10.1007/s10278-026-02269-4"><img src="https://img.shields.io/badge/Paper-JIIM%2C%20Scopus%20Q1-43ff9b?style=for-the-badge&labelColor=0b1322" alt="Paper in JIIM, Scopus Q1"></a>
  <a href="https://litmesh.n1giahuy.com/"><img src="https://img.shields.io/badge/Live-LitMesh-5b8cff?style=for-the-badge&labelColor=0b1322" alt="LitMesh live demo"></a>
  <a href="https://erp.n1giahuy.com/"><img src="https://img.shields.io/badge/Live-PurchaseFlow-ff4d8d?style=for-the-badge&labelColor=0b1322" alt="PurchaseFlow live demo"></a>
  <a href="https://www.linkedin.com/in/n1giahuy/"><img src="https://img.shields.io/badge/LinkedIn-n1giahuy-35e8ff?style=for-the-badge&labelColor=0b1322" alt="LinkedIn"></a>
  <a href="mailto:nlgiahuy10@gmail.com"><img src="https://img.shields.io/badge/Email-nlgiahuy10%40gmail.com-ffbf4d?style=for-the-badge&labelColor=0b1322" alt="Email"></a>
</p>

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="./assets/divider-dark.svg">
  <img src="./assets/divider-light.svg" alt="" width="100%">
</picture>

## Featured work

### LitMesh

A research assistant for scientific papers that retrieves evidence, synthesizes grounded answers, and attaches verifiable citations to every claim. Source is private; the system is live at [litmesh.n1giahuy.com](https://litmesh.n1giahuy.com/).

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="./assets/litmesh-dark.svg">
  <img src="./assets/litmesh-light.svg" alt="LitMesh pipeline: question, plan, retrieve, expand, rerank, synthesize, cited answer. Retrieval metrics on QASPER before and after fine-tuning." width="100%">
</picture>

The interesting engineering is in the retrieval layer. The agent plans multi-step retrieval and expands context through document-structure links instead of firing more semantic queries. Fine-tuning Qwen3-Embedding-0.6B with LoRA and InfoNCE on QASPER lifted NDCG@5 from 0.477 to 0.676. A zero-shot reranker made things worse (NDCG@5 dropped to 0.563), so I fine-tuned bge-reranker-v2-m3 on mined hard negatives and recovered 0.716 NDCG@5 and 0.814 MRR. On the QASPER dev set the system reaches 62.63 Evidence F1, about twice the original paper's LED-large baseline of 31.25.

### PurchaseFlow

Procurement automation that turns a chat request into a supplier-acknowledged purchase order. The agent only drafts; approvals, RFQs, and orders require a person or a system event. Source is private; the system is live at [erp.n1giahuy.com](https://erp.n1giahuy.com/).

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="./assets/purchaseflow-dark.svg">
  <img src="./assets/purchaseflow-light.svg" alt="PurchaseFlow state machine from chat request to supplier acknowledgement, with human gates marked." width="100%">
</picture>

Multi-day RFQ workflows run on a PostgreSQL state machine with a SKIP LOCKED scheduler that closes deadlines, flags silent suppliers, and escalates stalled decisions. Every state change sends its email exactly once through a transactional outbox and idempotent Resend delivery. Department-scoped RBAC lives in one authorization module shared by the API, the UI, and the agent's 16 role-scoped tools. The whole flow takes five human clicks.

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="./assets/divider-dark.svg">
  <img src="./assets/divider-light.svg" alt="" width="100%">
</picture>

## Research

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="./assets/research-dark.svg">
  <img src="./assets/research-light.svg" alt="Three research threads at ICIP Lab: embryo time-lapse microscopy, chromosome analysis, copy-number constrained classification." width="100%">
</picture>

**Deep Learning-Based Imaging Informatics for Automated Detection of Cytoplasmic Strings in Embryo Time-Lapse Microscopy.** Journal of Imaging Informatics in Medicine, Scopus Q1. [doi:10.1007/s10278-026-02269-4](https://doi.org/10.1007/s10278-026-02269-4)

## Open source

| Repository | What it does | Numbers |
| --- | --- | --- |
| [industrial-inspection-platform](https://github.com/n1giahuy/industrial-inspection-platform) | Unsupervised defect detection for manufacturing (EfficientAD), with a Streamlit UI, FastAPI backend, and a Prometheus + Grafana monitoring stack, all Dockerized | image AUROC 0.97, pixel AUROC 0.81, about 10 ms per image on GPU |

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="./assets/divider-dark.svg">
  <img src="./assets/divider-light.svg" alt="" width="100%">
</picture>

## Stack

| | |
| --- | --- |
| **Computer vision** | PyTorch, Hugging Face Transformers and PEFT, Ultralytics YOLO (incl. OBB), OpenCV, scikit-learn, CVAT. Classification, detection, segmentation, anomaly detection; supervised, self-supervised, and unsupervised learning |
| **LLMs and agents** | LlamaIndex, Google ADK, Gemini on Vertex AI, RAG, LoRA fine-tuning, Qdrant, pgvector, DeepEval |
| **Serving and MLOps** | vLLM, NVIDIA Triton, ONNX Runtime, Docker, GitHub Actions, Prometheus, Grafana |
| **Backend and cloud** | FastAPI, PostgreSQL, Redis, SQLAlchemy, GCP (Cloud Run, Firestore), Firebase, Terraform, Cloudflare, Nginx |

<p>
  <img src="https://img.shields.io/badge/PyTorch-0b1322?style=for-the-badge&logo=pytorch&logoColor=ff4d8d" alt="PyTorch">
  <img src="https://img.shields.io/badge/Hugging%20Face-0b1322?style=for-the-badge&logo=huggingface&logoColor=ffbf4d" alt="Hugging Face">
  <img src="https://img.shields.io/badge/OpenCV-0b1322?style=for-the-badge&logo=opencv&logoColor=43ff9b" alt="OpenCV">
  <img src="https://img.shields.io/badge/vLLM-0b1322?style=for-the-badge&logoColor=35e8ff" alt="vLLM">
  <img src="https://img.shields.io/badge/Triton-0b1322?style=for-the-badge&logo=nvidia&logoColor=43ff9b" alt="NVIDIA Triton">
  <img src="https://img.shields.io/badge/ONNX-0b1322?style=for-the-badge&logo=onnx&logoColor=eaf0fb" alt="ONNX">
  <img src="https://img.shields.io/badge/LlamaIndex-0b1322?style=for-the-badge&logoColor=5b8cff" alt="LlamaIndex">
  <img src="https://img.shields.io/badge/Qdrant-0b1322?style=for-the-badge&logo=qdrant&logoColor=ff4d8d" alt="Qdrant">
  <img src="https://img.shields.io/badge/FastAPI-0b1322?style=for-the-badge&logo=fastapi&logoColor=43ff9b" alt="FastAPI">
  <img src="https://img.shields.io/badge/PostgreSQL-0b1322?style=for-the-badge&logo=postgresql&logoColor=5b8cff" alt="PostgreSQL">
  <img src="https://img.shields.io/badge/Redis-0b1322?style=for-the-badge&logo=redis&logoColor=ff4d8d" alt="Redis">
  <img src="https://img.shields.io/badge/Docker-0b1322?style=for-the-badge&logo=docker&logoColor=35e8ff" alt="Docker">
  <img src="https://img.shields.io/badge/Terraform-0b1322?style=for-the-badge&logo=terraform&logoColor=b48cff" alt="Terraform">
  <img src="https://img.shields.io/badge/GCP-0b1322?style=for-the-badge&logo=googlecloud&logoColor=ffbf4d" alt="Google Cloud">
  <img src="https://img.shields.io/badge/Cloudflare-0b1322?style=for-the-badge&logo=cloudflare&logoColor=ffbf4d" alt="Cloudflare">
  <img src="https://img.shields.io/badge/Prometheus-0b1322?style=for-the-badge&logo=prometheus&logoColor=ff4d8d" alt="Prometheus">
  <img src="https://img.shields.io/badge/Grafana-0b1322?style=for-the-badge&logo=grafana&logoColor=ffbf4d" alt="Grafana">
</p>

## Competitions and community

- Top 50, AI Riser Vietnam 2026 by Google Developer Groups, out of more than 750 AI projects nationwide
- Top 7 finalist, AI and Data Science track, Skilio SEA TechSkills Challenge 2025
- Google Developer Group on Campus Lead at Saigon University, since 10/2025
- Information Technology, Saigon University. GPA 3.49, Dean's Merit Scholarship for four semesters

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="./assets/footer-dark.svg">
  <img src="./assets/footer-light.svg" alt="Measure it. Cite it. Ship it." width="100%">
</picture>
