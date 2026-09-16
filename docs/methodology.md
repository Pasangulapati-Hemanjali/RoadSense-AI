Research Methodology
1. Input

The system accepts RGB video from a dashboard-camera viewpoint.

RGB Dashboard Camera
          ↓
     Video Frames
2. Object Detection

YOLOv11 will be fine-tuned using transfer learning for the target classes:

Pedestrian
Vehicle
Cyclist
Pothole
Video Frame
     ↓
YOLOv11
     ↓
Bounding Boxes + Class + Confidence
3. Object Tracking

ByteTrack will associate detections across consecutive frames.

Frame t
  ↓
Detections
  ↓
ByteTrack
  ↓
Object IDs

Frame t+1
  ↓
Detections
  ↓
ByteTrack
  ↓
Same Object IDs where association is successful

Tracking provides temporal information required for motion-related analysis.

4. Relative Distance Estimation

Relative distance will be estimated from visual information such as bounding-box characteristics and perspective geometry.

The method and assumptions used for distance estimation will be documented and evaluated experimentally.

5. Pothole Severity Estimation

Detected potholes will be assigned severity categories based on defined visual criteria.

The severity definition and thresholds will be documented before final evaluation.

6. Risk Scoring

The risk module will combine relevant information such as:

Hazard type
Relative distance
Estimated motion
Pothole severity

A unified risk score will be calculated for detected hazards.

Conceptually:

Hazard Information
        ↓
Distance
Motion
Type
Severity
        ↓
Risk Scoring
        ↓
Risk Level

The exact scoring rules and thresholds will be defined and tested as part of the experimental methodology.

7. Hazard Prioritization

When multiple hazards are detected, hazards will be ranked according to their calculated risk.

Hazard A → Risk 0.82
Hazard B → Risk 0.45
Hazard C → Risk 0.21

Priority:
A → B → C
8. Decision Support

The highest-priority hazard and its risk conditions will be mapped to one of the predefined decision-support outputs:

Brake Immediately
Slow Down
Change Lane
Maintain Lane
Proceed

These are advisory outputs and do not directly control a vehicle.

9. Baseline Comparison

The proposed system will be compared with a detection-only baseline.

Baseline
YOLOv11 → Detection
Proposed
YOLOv11
→ ByteTrack
→ Distance/Motion/Severity
→ Risk Scoring
→ Priority
→ Decision Support
10. Evaluation

The system will be evaluated using:

Precision
Recall
F1-Score
mAP@50
mAP@50-95
Appropriate tracking metrics
Distance estimation error
Decision-support scenario evaluation
Inference speed/FPS

The target of greater than 15 FPS is an experimental performance target and will be reported together with the hardware and software configuration used.
