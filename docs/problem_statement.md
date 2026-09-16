Research Problem and Motivation
Problem Statement

Modern vision-based Advanced Driver Assistance Systems can detect road users and surface hazards such as pedestrians, vehicles, cyclists, and potholes from camera data.

However, when multiple hazards occur simultaneously, independent object detections do not directly indicate which hazard should receive priority or what driving response may be appropriate.

For example, a camera may simultaneously detect:

Pedestrian → 12 m
Vehicle    → 20 m
Cyclist    → 8 m
Pothole    → 5 m

A detection-only system identifies these objects but does not necessarily provide a unified assessment of their relative risk.

RoadSense AI therefore investigates an integrated vision-based framework that combines:

Detection
   +
Tracking
   +
Relative Distance
   +
Motion Information
   +
Pothole Severity
   +
Risk Scoring
   +
Hazard Prioritization
   +
Decision Support

The research focuses on determining whether this integration can provide more actionable and prioritized alerts than object detection alone.

Motivation

Driving environments can contain multiple simultaneous hazards. Presenting every detected object with equal importance may increase the amount of information that a driver must interpret.

The project therefore investigates a system that converts visual perception into prioritized risk information and predefined driving recommendations.

The intended output is not autonomous vehicle control. It is a decision-support layer that provides information such as:

HIGH RISK
Pedestrian – approximately 8 m

Recommended action:
Brake Immediately

The actual effectiveness of this approach will be determined through experiments.

Scope

The project uses RGB video captured using a dashboard-camera viewpoint under normal daytime conditions.

The initial hazard classes are:

Pedestrian
Vehicle
Cyclist
Pothole

The project does not include:

Autonomous vehicle control
Thermal imaging
Custom sensing hardware
Direct vehicle actuation
Research Focus

The central research focus is the integration of multi-hazard perception with risk assessment and decision support rather than object detection alone.
