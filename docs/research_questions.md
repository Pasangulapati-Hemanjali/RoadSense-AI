Research Questions and Hypothesis
Primary Research Question

Can an RGB camera-based system that integrates multi-hazard detection, object tracking, relative distance estimation, pothole severity estimation, and risk scoring generate more actionable and prioritized driving alerts than a detection-only approach in multi-hazard road scenarios?

Supporting Research Questions
RQ1 — Detection

How effectively can YOLOv11 detect pedestrians, vehicles, cyclists, and potholes in RGB road scenes?

RQ2 — Tracking

How effectively can ByteTrack maintain object identities across consecutive frames for detected road users?

RQ3 — Spatial Information

How accurately can relative distance and motion-related information be estimated from RGB video using bounding-box and perspective-based information?

RQ4 — Risk Assessment

Can hazard type, relative distance, estimated motion, and pothole severity be combined into a meaningful risk score for multiple simultaneously occurring hazards?

RQ5 — Decision Support

Can risk-ranked hazards be mapped to predefined driving decision-support actions such as Brake Immediately, Slow Down, Change Lane, Maintain Lane, and Proceed?

Research Hypothesis
H1

Integrating object tracking, relative distance estimation, motion information, and pothole severity with object detection can provide more prioritized and actionable hazard alerts than using object detection alone in multi-hazard road scenarios.

Null/Alternative Interpretation

The experimental results will determine whether the hypothesis is supported.

A negative or inconclusive result will not be treated as an implementation failure. It may indicate that one or more components, such as distance estimation, tracking, risk thresholds, or decision rules, do not provide the expected improvement under the tested conditions.

Baseline

The baseline system will use:

RGB Video
    ↓
YOLOv11
    ↓
Object Detection
    ↓
Detection Output

The proposed system will use:

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

The comparison between the baseline and proposed system will be used to investigate the research question.
