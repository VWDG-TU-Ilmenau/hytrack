# HYTRACK - Hybrid Full-Body Tracking

*This repository accompanies our paper “HYTRACK: A Modular Hybrid Full-Body Tracking Architecture for Virtual Reality”, accepted at the GI Workshop on Virtual and Augmented Reality (VR/AR 2026). Workshop: https://vrar2026.cs.hs-rm.de*

HYTRACK is a modular hybrid full-body tracking prototype for virtual reality.
The system combines Meta Quest 3 head and hand tracking with interchangeable camera-based lower-body tracking modules.

Abstract: *Consumer virtual reality headsets commonly track the head and hands but provide only limited information about the lower body. We present HYTRACK, a proof-of-concept hybrid tracking architecture that combines Meta Quest 3 tracking with an interchangeable camera-based lower-body module. The lower-body source can be implemented using Microsoft Kinect v2, MediaPipe Pose Landmarker, or MeTRAbs. A common joint representation, shared calibration procedure, and decoupled inverse-kinematics pipeline allow the active source to be exchanged without modifying the downstream avatar-control logic. We describe the architecture and its three implementations and demonstrate them through representative postures and a leg-based interaction scenario. The prototype shows the technical feasibility of combining heterogeneous tracking sources within one avatar pipeline and exposes practical challenges involving coordinate alignment, monocular depth estimation, occlusion, jitter, and floor contact. The work provides an extensible basis for future quantitative tracking evaluations and user studies.*

The current implementation supports:
- Microsoft Kinect v2
- MediaPipe Pose Landmarker
- MeTRAbs
- Meta Quest 3 via OpenXR
- Unity-based avatar integration using inverse kinematics

## System Overview
HYTRACK separates upper- and lower-body tracking into independent modules. Meta Quest 3 provides head and hand tracking, while the active lower-body module provides hip, knee, and ankle positions.
All lower-body sources are converted into a shared hip-relative representation before being mapped to the avatar. This allows Kinect, MediaPipe, and MeTRAbs to use the same downstream IK and avatar-control pipeline.
The RGB-based modules run as external Python processes and transmit joint positions to Unity over UDP using a common packet format. Kinect data are read directly through the Kinect SDK and converted into the same internal joint representation.

## Repository Structure
Unity/

├── Assets/Scripts/

├── Assets/Scenes/

└── Assets/Scripts/UserStudy/

Python/

└── Tools/

## Requirements
	•	Unity 6
	•	Meta Quest 3
	•	OpenXR / Meta XR SDK
	•	Python environment for RGB-based tracking
	•	Webcam for MediaPipe or MeTRAbs
	•	Optional: Microsoft Kinect v2 and Kinect SDK

## Usage
	1	Open the Unity project.
	2	Connect and configure the Meta Quest 3.
	3	Select the desired lower-body tracking source.
	4	For RGB-based tracking, start either the MediaPipe or MeTRAbs Python process.
	5	Perform the initial spatial calibration.
	6	Start the VR application.


The lower-body source can be exchanged without modifying the downstream avatar-control logic.

This project is released under the MIT License.

If this work is helpful or inspires your work, please cite our paper:
<section class="section" id="BibTeX">
  <div class="container is-max-desktop content">
    <h2 class="title">BibTeX</h2>
    <pre><code>@article{hytrack,
    author  = {Hamza Saeed Khan, Andy Schleising and Wolfgang Broll},
    title   = {HYTRACK: A Modular Hybrid Full-Body Tracking Architecture for Virtual Reality},
    booktitle = {Proceedings of the 23rd GI Workshop on Virtual and Augmented Reality},
    year    = {2026},
    publisher = {Gesellschaft für Informatik e.V.}
}</code></pre>
  </div>
</section>