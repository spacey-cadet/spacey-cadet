<div align="center">
<img src="banner.svg" width="100%" alt="Theo Korir — Full-Stack · AI/ML · Applied Research · Nairobi"/>
> I build things end-to-end: ML pipelines, Android automations, Android apps, production APIs, web apps.<br/>
> Speech models fine-tuned in PyTorch. Platforms shipped solo. Pipelines running on nothing but a phone.
</div>

## Open Source Projects

### [Infra Risk Guardian — Terraform Plan Gatekeeper](https://github.com/spacey-cadet/infra-cost)
Decision API that reviews every Terraform plan and returns a deterministic `auto_apply` or `hold`, built to never auto-apply a change that quietly loosens security, especially a widened GitHub Actions OIDC trust condition. It parses the JSON plan and runs a glob-aware diff on the trust policy, and a plain-Python rule matrix fails closed on any IAM change, OIDC diff, cost jump of $2/mo or 40%, unseen resource type, or unparseable plan. It runs as a SigV4-signed Lambda Function URL called by a pip-installable CLI that exits 0 for auto-apply and 2 for hold, with an optional AI explainer and classifier that add review context but can never override the verdict.

`Python` `Strands Agents` `Terraform` `AWS Lambda` `SQS` `SNS` `DynamoDB` `S3` `GitHub Actions OIDC` `Infracost` `Docker` `pytest`

---

### [Scoopz](https://github.com/spacey-cadet/scoopz)
TikTok share-to-caption pipeline, rebuilt from a Termux script pair into a native Android app (Kotlin, Jetpack Compose): share a link and queued background workers download the video in HD and write a ready-to-post caption. On-device ML Kit picks the sharpest frame (faces, on-screen text), and free-tier NVIDIA models with a backup, rate limiting and retries generate the caption at zero cost. Failures turn into plain-language causes and fixes, and the original Termux pipeline (async workers, FastAPI) stays as a working legacy path.

**Impact:** the Termux version cut content processing ~58% (2 hrs → 50 min for 40 videos); the app makes the same flow a single tap.

`Python` `Kotlin` `Android` `FastAPI` `OpenAI API` `ffmpeg` `Termux`

---

### [Knee MRI Abnormality Detection](https://github.com/spacey-cadet/knee-abnormality-detection)

Kaggle RSNA challenge to detect 12 knee abnormalities from MRI when only 58 of 4,407 studies have human labels. Qwen3-8B and a rule-based labeler turn multilingual radiology reports into training labels (0.85 mean AUC against the gold set), which train a multi-plane attention model validated across scanners.

`Python` `PyTorch` `timm` `pydicom` `Qwen3` `Kaggle`

---

### [Churn Escalation Detector — End-to-End MLOps Pipeline](https://github.com/spacey-cadet/churn-escalation)
Churn-risk scoring pipeline that runs unchanged in two modes, local Docker/SQLite and AWS Lambda/DynamoDB/S3, with identical training, gating and serving code in both. A calibrated XGBoost model routes each prediction into auto-resolve, review-queue or senior-escalation tiers, while data-quality gates and a champion-challenger check block bad data and any retrain that regresses PR-AUC. It also runs hourly drift monitoring (KS, PSI), backfills metrics once labels land after 21 days, and deploys through GitHub Actions OIDC with canary rollouts.

`Python` `XGBoost` `FastAPI` `Docker` `AWS Lambda` `DynamoDB` `S3` `GitHub Actions`

---

### [Click-Fraud & Churn Risk Scoring Platform (ad-platform-ml)](https://github.com/spacey-cadet/ad-fraud)
Two real-time scoring services, click-fraud detection and churn prediction, share one feature base and deploy as either a free local Docker stack or a serverless AWS stack under ~$15/month. A streaming pipeline (Redpanda + Faust locally; SQS → Lambda → DynamoDB in production) computes rolling per-user click windows for live fraud scoring. The AWS side is all Terraform with no always-on services, with MLflow experiment tracking and an ADR for every local-vs-cloud trade-off.

`Python` `LightGBM` `Redis/Feast` `Redpanda/Faust` `SQS` `DynamoDB` `Terraform` `Docker` `MLflow`

---

### [Speech Emotion Recognition — WavLM Fine-Tuning](https://github.com/spacey-cadet)
Fine-tuned a 24-layer Transformer for 8-class emotion recognition across RAVDESS, IEMOCAP, and CREMA-D. 77.3% accuracy in-distribution; cross-corpus testing exposed a 16–23pp generalisation drop, diagnosed via arousal/valence failure analysis — a known limit of self-supervised speech embeddings. Scoped fixes: adversarial domain adaptation, speaker disentanglement, Kenya-specific DAPT corpus.

`PyTorch` `HuggingFace` `WavLM` `SpeechBrain` `Transfer Learning`

---

### [WavLM SER — Production Inference Pipeline (Deployment)](https://github.com/spacey-cadet/ser-inference)
Rebuilt a single-endpoint emotion-recognition demo into a production-grade serving pipeline (FastAPI + Docker on HuggingFace Spaces) covering calibration, drift monitoring, rollout and latency, all on free-tier infrastructure. Calibration and a two-threshold confidence cascade let uncertain predictions degrade gracefully instead of returning an overconfident wrong label, and a consent-gated logging pipeline feeds a KS-test drift monitor and a low-confidence review queue. Canary routing is checked offline on PR-AUC and per-class F1 before rollout, and p50/p99 latency gates each release through GitHub Actions.

`FastAPI` `Docker` `HuggingFace Spaces` `GitHub Actions` `Great Expectations`

---

### Pay Hero &nbsp;·&nbsp; *1st Place, Kenya Buildathon 2024*
Scalable B2B communication platform helping businesses engage customers at scale. Shipped under hackathon time pressure with a 2-person team, full-stack, and won against the full field.

`Scalable Architecture` `B2B` `Rapid Deployment` `Full-Stack`

---

### Production Web Platforms
Three production platforms — full lifecycle ownership, architecture to deployment to support.

| Platform | Description |
|---|---|
| **[Lisa Luxury Homes](https://lisaluxuryhomes.co.ke)** | Real-estate platform with dynamic routing, SEO optimisation, and WhatsApp conversion flow. |
| **[FunFiesta Kenya](https://funfiestakenya.com)** | Booking platform for a kids' events business. Mobile-first, end-to-end. |
| **[Rafi](https://rafi.co.ke)** | Student mental-health platform: wellbeing tracking, risk detection, counsellor routing. |

`Next.js` `React` `Node.js` `REST APIs` `Vercel` `SEO`

---

## Stack

<div align="center">

**AI / ML**&nbsp;&nbsp;
![HuggingFace](https://img.shields.io/badge/HuggingFace-111827?style=flat-square&logo=huggingface&logoColor=f59e0b)
![PyTorch](https://img.shields.io/badge/PyTorch-111827?style=flat-square&logo=pytorch&logoColor=ee4c2c)
![WavLM](https://img.shields.io/badge/WavLM-111827?style=flat-square&logoColor=white)
![Whisper](https://img.shields.io/badge/Whisper-111827?style=flat-square&logoColor=white)
![DAPT](https://img.shields.io/badge/DAPT-111827?style=flat-square&logoColor=white)
![SpeechBrain](https://img.shields.io/badge/SpeechBrain-111827?style=flat-square&logoColor=white)
![OpenAI API](https://img.shields.io/badge/OpenAI%20API-111827?style=flat-square&logo=openai&logoColor=white)
![Strands Agents](https://img.shields.io/badge/Strands%20Agents-111827?style=flat-square&logoColor=white)
 
**Classical ML**&nbsp;&nbsp;
![XGBoost](https://img.shields.io/badge/XGBoost-111827?style=flat-square&logoColor=ff6600)
![LightGBM](https://img.shields.io/badge/LightGBM-111827?style=flat-square&logoColor=00b7c2)
![scikit-learn](https://img.shields.io/badge/scikit--learn-111827?style=flat-square&logo=scikit-learn&logoColor=f89939)
![pandas](https://img.shields.io/badge/pandas-111827?style=flat-square&logo=pandas&logoColor=e70488)
![NumPy](https://img.shields.io/badge/NumPy-111827?style=flat-square&logo=numpy&logoColor=4dabcf)

**Languages**&nbsp;&nbsp;
![Python](https://img.shields.io/badge/Python-111827?style=flat-square&logo=python&logoColor=3b82f6)
![JavaScript](https://img.shields.io/badge/JavaScript-111827?style=flat-square&logo=javascript&logoColor=facc15)
![TypeScript](https://img.shields.io/badge/TypeScript-111827?style=flat-square&logo=typescript&logoColor=38bdf8)
![Kotlin](https://img.shields.io/badge/Kotlin-111827?style=flat-square&logo=kotlin&logoColor=a78bfa)
![Java](https://img.shields.io/badge/Java-111827?style=flat-square&logo=openjdk&logoColor=f97316)
![C++](https://img.shields.io/badge/C++-111827?style=flat-square&logo=cplusplus&logoColor=6366f1)

**Frontend**&nbsp;&nbsp;
![React](https://img.shields.io/badge/React-111827?style=flat-square&logo=react&logoColor=38bdf8)
![Next.js](https://img.shields.io/badge/Next.js-111827?style=flat-square&logo=next.js&logoColor=white)
![TypeScript](https://img.shields.io/badge/TypeScript-111827?style=flat-square&logo=typescript&logoColor=38bdf8)
![Tailwind CSS](https://img.shields.io/badge/Tailwind-111827?style=flat-square&logo=tailwindcss&logoColor=38bdf8)
![ReactFlow](https://img.shields.io/badge/ReactFlow-111827?style=flat-square&logoColor=white)

**Backend**&nbsp;&nbsp;
![Node.js](https://img.shields.io/badge/Node.js-111827?style=flat-square&logo=node.js&logoColor=4ade80)
![FastAPI](https://img.shields.io/badge/FastAPI-111827?style=flat-square&logo=fastapi&logoColor=34d399)
![Django](https://img.shields.io/badge/Django-111827?style=flat-square&logo=django&logoColor=6ee7b7)
![GraphQL](https://img.shields.io/badge/GraphQL-111827?style=flat-square&logo=graphql&logoColor=e10098)
![WebSockets](https://img.shields.io/badge/WebSockets-111827?style=flat-square&logoColor=white)

**Mobile & DevOps**&nbsp;&nbsp;
![Android](https://img.shields.io/badge/Android-111827?style=flat-square&logo=android&logoColor=86efac)
![Termux](https://img.shields.io/badge/Termux-111827?style=flat-square&logoColor=white)
![AWS](https://img.shields.io/badge/AWS-111827?style=flat-square&logo=amazonaws&logoColor=fb923c)
![Terraform](https://img.shields.io/badge/Terraform-111827?style=flat-square&logo=terraform&logoColor=a78bfa)
![Docker](https://img.shields.io/badge/Docker-111827?style=flat-square&logo=docker&logoColor=38bdf8)
![GitHub Actions](https://img.shields.io/badge/GitHub%20Actions-111827?style=flat-square&logo=githubactions&logoColor=white)
![Vercel](https://img.shields.io/badge/Vercel-111827?style=flat-square&logo=vercel&logoColor=white)
![Git](https://img.shields.io/badge/Git-111827?style=flat-square&logo=git&logoColor=f87171)
![Figma](https://img.shields.io/badge/Figma-111827?style=flat-square&logo=figma&logoColor=f472b6)
![ffmpeg](https://img.shields.io/badge/ffmpeg-111827?style=flat-square&logoColor=white)

</div>

---

## Experience

**Machine Learning Engineer Intern · JHUB Africa** &nbsp;·&nbsp; *May – Aug 2024*
- Integrated ML models into production systems (React + FastAPI), owning the connection between model outputs and the UI.
- Designed RESTful APIs bridging backend inference pipelines with frontend components.
- Reviewed code and presented technical work to non-technical stakeholders on an async, remote-distributed team.

**Full-Stack Developer · Independent Clients (Freelance)** &nbsp;·&nbsp; *2024 – 2025*
- Architected, deployed, and maintained 3 production web applications solo, 100% on-time delivery.
- Owned the full workflow: REST API design, version control, Vercel deployment, SEO, post-launch support.

---

## Education

**BSc Computer Science** — Jomo Kenyatta University of Agriculture & Technology *(Expected 2026)*
Data Structures & Algorithms · Artificial Intelligence · Operating Systems · System Design · OOP · Cryptography · Probability & Statistics · Internet Application Programming

---

## Contact

<div align="center">

[![Email](https://img.shields.io/badge/theo.korirchbng@gmail.com-111827?style=flat-square&logo=gmail&logoColor=f87171)](mailto:theo.korirchbng@gmail.com)
&nbsp;
[![LinkedIn](https://img.shields.io/badge/Theo%20Korir-111827?style=flat-square&logo=linkedin&logoColor=38bdf8)](https://linkedin.com/in/theo-korir)
&nbsp;
[![GitHub](https://img.shields.io/badge/spacey--cadet-111827?style=flat-square&logo=github&logoColor=white)](https://github.com/spacey-cadet)
&nbsp;
![Location](https://img.shields.io/badge/Nairobi%2C%20Kenya-111827?style=flat-square&logo=googlemaps&logoColor=4ade80)

</div>

---

<div align="center">
<br/>
<sub>Nairobi, Kenya</sub>
</div>
