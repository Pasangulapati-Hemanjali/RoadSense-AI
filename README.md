# RoadSense-AI
RoadSense AI: Vision-Based Multi-Hazard Risk Assessment

## 1. Project Overview

RoadSense AI is an RGB camera-based multi-hazard risk assessment and driving decision-support system designed for road environments.

Modern Advanced Driver Assistance Systems (ADAS) can detect individual road users and hazards such as pedestrians, vehicles, cyclists, and potholes. However, detecting individual hazards does not necessarily provide an understanding of which hazard should receive immediate attention when multiple hazards occur simultaneously.

RoadSense AI investigates an integrated vision-based pipeline that combines multi-hazard detection, object tracking, relative distance estimation, pothole severity estimation, risk scoring, hazard prioritization, and driving decision support.

The system uses a standard RGB dashboard camera and does not perform autonomous vehicle control.



## 2. Research Problem

Existing vision-based road safety systems can detect individual road hazards with high accuracy. However, multiple hazards may occur simultaneously in real traffic conditions.

A detection-only system may produce separate outputs such as:

* Pedestrian detected
* Vehicle detected
* Cyclist detected
* Pothole detected

Such detections do not directly answer:

> Which hazard should receive priority, and what driving action should be recommended?

RoadSense AI therefore investigates whether detection, tracking, relative distance, motion information, and pothole severity can be integrated into a unified risk assessment and decision-support framework.

---

## 3. Research Question

### Primary Research Question

Can an RGB camera-based system that integrates multi-hazard detection, object tracking, relative distance estimation, pothole severity estimation, and risk scoring generate more actionable and prioritized driving alerts than a detection-only approach in multi-hazard road scenarios?

### Supporting Research Questions

1. How effectively can YOLOv11 detect pedestrians, vehicles, cyclists, and potholes in RGB road scenes?

2. How effectively can ByteTrack maintain object identities across consecutive frames for detected road users?

3. How accurately can relative distance and motion information be estimated from RGB video using bounding-box and perspective-based information?

4. Can combining hazard type, relative distance, motion, and pothole severity produce meaningful risk prioritization?

5. Can the resulting risk priorities be converted into predefined driving decision-support actions?

---

## 4. Research Hypothesis

### H1

Integrating object tracking, relative distance estimation, motion information, and pothole severity with object detection can provide more prioritized and actionable hazard alerts than using object detection alone in multi-hazard road scenarios.

The hypothesis will be evaluated experimentally and may be supported, partially supported, or not supported depending on the obtained results.

---

## 5. Research Gap

The literature indicates substantial work in individual components of vision-based road safety, including road-object detection, pothole detection, object tracking, distance estimation, and ADAS warning systems.

However, these components are often evaluated separately or for individual hazard categories.

RoadSense AI investigates their integration into a unified pipeline in which multiple detected hazards are:

1. Detected
2. Tracked
3. Associated with relative spatial information
4. Assigned a risk score
5. Prioritized
6. Converted into a driving decision-support recommendation

The project therefore focuses on the integration of multi-hazard perception and risk-aware decision support rather than object detection alone.

---

## 6. Proposed System

```text
RGB Dashboard Camera / Video
             |
             v
       YOLOv11 Detector
             |
             v
 Multi-Hazard Detection
             |
             v
        ByteTrack
             |
             v
 Object Tracking / Motion Information
             |
             +----------------------+
             |                      |
             v                      v
 Relative Distance          Pothole Severity
 Estimation                  Estimation
             |                      |
             +----------+-----------+
                        |
                        v
                 Risk Scoring
                    Module
                        |
                        v
               Hazard Prioritization
                        |
                        v
             Decision Support Engine
                        |
                        v
    Brake / Slow Down / Change Lane /
       Maintain Lane / Proceed
```

---

## 7. Target Hazard Classes

The initial target classes are:

* Pedestrian
* Vehicle
* Cyclist
* Pothole

---

## 8. Major Components

### 8.1 Object Detection

YOLOv11 is planned as the primary object detector. Transfer learning will be used to adapt the detector to the selected road-hazard classes.

### 8.2 Object Tracking

ByteTrack will be used to maintain object identities across consecutive video frames and support motion-related analysis.

### 8.3 Relative Distance Estimation

Relative distance will be estimated using visual information such as bounding-box characteristics and perspective geometry.

### 8.4 Pothole Severity Estimation

Visual characteristics of detected potholes will be investigated to estimate severity categories suitable for downstream risk analysis.

### 8.5 Risk Scoring

A risk score will combine relevant factors such as:

* Hazard type
* Relative distance
* Estimated motion
* Pothole severity

The resulting score will be used to prioritize detected hazards.

### 8.6 Decision Support

The system will map risk conditions to predefined decision-support outputs:

* Brake Immediately
* Slow Down
* Change Lane
* Maintain Lane
* Proceed

These outputs are recommendations only. The system does not control the vehicle.

---

## 9. Research Baseline

A detection-only baseline will be used for comparison.

### Baseline

```text
RGB Video
   ↓
YOLOv11
   ↓
Object Detection
   ↓
Detection Alerts
```

### Proposed System

```text
RGB Video
   ↓
YOLOv11
   ↓
ByteTrack
   ↓
Distance / Motion / Pothole Severity
   ↓
Risk Scoring
   ↓
Hazard Prioritization
   ↓
Decision Support
```

The comparison will help determine the contribution of the additional risk-assessment components.

---

## 10. Dataset

The project will investigate publicly available datasets for:

* Pedestrians
* Vehicles
* Cyclists
* Potholes

Curated Indian road footage will additionally be considered for validation under realistic traffic conditions.

Dataset sources, licenses, class distributions, annotation formats, and train/validation/test splits will be documented before use.

---

## 11. Evaluation

### Object Detection Metrics

* Precision
* Recall
* F1-Score
* mAP@50
* mAP@50-95

### Tracking Evaluation

Tracking performance will be evaluated using appropriate tracking measures where suitable ground-truth information is available.

### Distance Estimation

Estimated relative distance will be compared against available reference/approximate distance information using an appropriate error measure.

### Decision Support

Predefined road scenarios will be used to evaluate whether the risk-scoring and decision-support rules produce the intended priority and recommendation.

### Real-Time Performance

Inference performance will be measured in FPS under the tested hardware and software configuration.

A target of more than 15 FPS is planned for the tested real-time configuration; actual performance will be reported from experiments rather than assumed in advance.

---

## 12. Technology Stack

* Python
* PyTorch
* Ultralytics YOLO
* YOLOv11
* OpenCV
* NumPy
* Pandas
* ByteTrack
* Streamlit
* CUDA, where compatible GPU hardware is available

---

## 13. Project Scope

### Included

* RGB dashboard-camera input
* Pedestrian detection
* Vehicle detection
* Cyclist detection
* Pothole detection
* Object tracking
* Relative distance estimation
* Motion-related analysis
* Pothole severity estimation
* Risk scoring
* Hazard prioritization
* Driving decision support
* Real-time visualization

### Not Included

* Autonomous vehicle control
* Thermal imaging
* Custom sensing hardware
* Direct vehicle actuation
* Night-time performance as a primary evaluation condition

---

## 14. Current Research Status

### Review 1

* [ ] Research problem defined
* [ ] Research question formulated
* [ ] Hypothesis formulated
* [ ] Research gap identified
* [ ] Literature taxonomy prepared
* [ ] Closest prior work identified
* [ ] Experimental plan defined
* [ ] GitHub repository established
* [ ] Initial project skeleton created

---

## 15. Future Work

1. Finalize datasets and data preparation.
2. Train and evaluate the YOLOv11 detector.
3. Integrate ByteTrack.
4. Implement relative distance estimation.
5. Develop pothole severity estimation.
6. Implement risk scoring.
7. Develop decision-support rules.
8. Conduct baseline and proposed-system experiments.
9. Evaluate performance.
10. Analyze limitations and research findings.

---

## 16. Team

| Team Member | Primary Responsibility      |
| ----------- | --------------------------- |
| Member 1    | Research and Literature     |
| Member 2    | Dataset and Detection       |
| Member 3    | Tracking, Distance and Risk |
| Member 4    | Application and Evaluation  |

---

## 17. Repository Structure

```text
RoadSenseAI/
├── README.md
├── requirements.txt
├── .gitignore
├── docs/
├── data/
├── src/
├── experiments/
├── models/
├── tests/
└── app.py
```

