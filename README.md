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

### Automated Biodiversity Monitoring via YOLOv8 & Royle-Nichols Statistical Modeling

## Latest Project Milestones
We have successfully expanded the system's analytical capabilities beyond simple detection to provide actionable ecological insights:
* **Kilometer Grid Analysis:** Implemented population density and abundance statistics based on a standardized **1km × 1km grid** scale.
* **Seasonal Dynamics:** Generated and compared **seasonal heatmaps** to visualize how wild boar distribution shifts across Spring, Summer, Autumn, and Winter.
* **Interannual Trends:** Conducted **multi-year comparative analysis** to quantify population growth or decline over different years, providing a scientific basis for ecological management.

## System Workflow
1.  **Detection:** A lightweight **YOLOv8n** model filters infrared camera footage to identify wild boars with high precision (95.5%).
2.  **Data Transformation:** AI detection logs are converted into a **time-space presence matrix** (Detection History).
3.  **Statistical Inference:** The **RN (Royle-Nichols) Model** processes the matrix using Poisson and Bernoulli probabilistic formulations to estimate true abundance from detection frequency.
4.  **Spatial Mapping:** Results are projected onto a **kilometer grid**, generating heatmaps that visualize population density and temporal changes.

## Accomplishments & Results
-   **Grid-Based Insights:** Successfully calculated density within 1km² units, allowing for targeted ecological interventions.
-   **Spatiotemporal Analysis:** Our multi-season and multi-year comparisons revealed distinct migration patterns and long-term population trends, providing data-driven support for conservation strategies.

## Future Vision
* **Edge Deployment:** Running the full pipeline on edge computing devices for real-time field monitoring.
* **Predictive Modeling:** Integrating environmental factors (vegetation, water sources, climate) to shift from "historical assessment" to "future trend prediction."
* **Biodiversity Expansion:** Adapting the framework for other key species to support comprehensive, automated biodiversity protection.

---

## Tech Stack
`Python` | `YOLOv8` | `PyTorch` | `RN Model (Royle-Nichols)` | `GIS Heatmapping` | `AI-Assisted Workflow (Cursor)`
