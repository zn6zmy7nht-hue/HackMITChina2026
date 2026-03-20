# Intelligent Wild Boar Population Assessment System

## Project Overview
This project is an intelligent assessment system that combines computer vision and ecological statistics to automate wild boar population estimation.  
At this stage, we have completed YOLOv8 model training. Next, at the competition venue, we will finish data transformation and final population estimation.

## Inspiration
Our inspiration comes from real-world ecological issues in Baixi Nature Reserve, Zijin County, Guangdong.  
In recent years, due to the lack of natural predators and rapid reproduction, wild boars have overpopulated in some mountainous regions, causing frequent human-wildlife conflicts and major agricultural losses.

Traditional population surveys are time-consuming, labor-intensive, and often inaccurate. In addition, wild boars lack clear unique individual features, making traditional mark-recapture methods ineffective.  
Therefore, we aim to build an automated modern system that can solve this ecological management problem scientifically and efficiently, without requiring individual identification.

## What It Does
The system analyzes images captured by field infrared cameras.

1. Users input raw footage/images.
2. Our trained YOLOv8 model automatically filters invalid photos and detects wild boars.
3. At the competition venue, detection results are transformed into a time-space presence matrix (whether wild boars appeared at specific times and locations).
4. The matrix is fed into the RN (Royle-Nichols) ecological model.
5. Based on appearance frequency and observation structure, the model estimates the true total wild boar population and outputs an intuitive population distribution heatmap.

## How We Built It
The project has two phases:

### Phase One (Completed)
- Collected and cleaned 4,000+ infrared camera photos.
- Performed strict manual annotation.
- Trained a lightweight YOLOv8n model on a dual-GPU environment (RTX A6000).
- Achieved 95.5% detection accuracy.

### Phase Two (On-Site)
- Build data conversion scripts to transform AI detection logs into the matrix format required by ecological statistics.
- Run the RN model using Poisson and Bernoulli-based probabilistic formulations.
- Infer true population size from image-based observation data.

## Individual Contributions
Our 5-person team has clear role division:

- **Siyi Qin (Team Leader):** Designed overall system architecture and researched the RN model mathematical framework for on-site deployment.
- **Jiaxuan Liang (Data Engineering):** Collected, cleaned, and manually annotated large-scale field camera images to produce high-quality training data.
- **Lingrui Cao (Deep Learning):** Configured hardware environment, ran YOLOv8 training, tuned parameters, and achieved 95.5% accuracy.
- **Xihan Xu (Pipeline Development):** Developed data processing scripts to convert AI outputs into RN-compatible standard format.
- **Mo Chen (Visualization & Strategy):** Prepared project documentation and designed visual presentation strategies, including population heatmaps.

## Challenges We Ran Into
- Early-stage challenge: processing massive image volume with incomplete/missing data.
- On-site challenge: accurately and efficiently connecting front-end AI detection with back-end statistical modeling under strict time constraints, while ensuring stable and error-free data flow.

## Accomplishments We’re Proud Of
- Achieved 95.5% detection accuracy on a challenging real-world field dataset with lightweight YOLOv8n.
- Went beyond object detection and tackled the core ecological problem: estimating true population size from fragmented observation footage by integrating an advanced statistical model.

## What We Learned
- We validated that lightweight computer vision models can still deliver strong field performance with high-quality data engineering.
- During implementation, we adopted an AI-era development workflow: by using AI-assisted coding tools (such as Cursor), we reduced boilerplate coding effort and focused more on system architecture, data sanitization, and pipeline logic.
- This AI-supported workflow significantly improved productivity and gave us confidence for large-scale on-site data processing.
- For the RN model, given our limited mathematical background, we learned a practical strategy: first make input-output pipelines work reliably, then progressively deepen theoretical understanding.

## What’s Next
- Immediate goal: run the RN model successfully at the competition venue and convert AI visual outputs into meaningful population estimation results.
- Next step: extend from static estimation to future population trend prediction.
- Long-term vision: deploy the full pipeline on edge computing devices connected to field cameras for automated biodiversity monitoring, supporting ecological protection and agricultural loss reduction with scientific data.
