# Changelog

All notable changes to this repository are documented here. Dates are ISO-8601.

## [Unreleased]

### Changed
- CAD Rev B, front and back panels (`MMP.00.00.00.001`, `MMP.00.00.00.002`) for the 2.0
  sensor set; the previous CAD is kept in release v0.0.1.
  - Front panel: Gemini 336L slot (123 x 31 mm) on the centreline with four ⌀5.5 mount holes;
    the old camera holes (4x ⌀3.4) are removed.
  - Front and back panels: one ⌀29.46 MaxSonar hole on the centreline with two ⌀5.5 holes, and
    two TF-Luna windows (30 x 23 mm, y ±130 mm) with ⌀5.5 bracket holes 44 mm apart; the old
    ⌀18.5 / ⌀19 holes at y ±130 mm are removed.
  - New STEP and DXF for both panels; the native SLDPRT and SLDDRW files are removed for now.
    The PDF drawings are still Rev A.
- Full assembly STEP updated to OpenAMRobot platform v0.2 (`openamr_platform_v0.2`): Gemini 336L
  10° up on the camera mount, four TF-Luna and two MaxSonar on their printed mounts, the RPLIDAR S3 on
  the 20 mm spacer.
- LiDAR spacer is now the 20 mm printed spacer MMP.07.00.00.002 (was the 7.1 mm plate on
  10 mm standoffs).

### Added
- 3D-printed parts (PETG, STEP and STL): MMP.01.00.00.003 Camera mount (Gemini 336L slot,
  10° up), MMP.00.00.00.005 TF-Luna mount (x4), MMP.00.00.00.006 Ultrasonic mount (x2),
  MMP.07.00.00.002 LiDAR mount spacer (20 mm). Listed in `manufacturing/bom/mechanical-bom.md`.
- Real-robot audit findings integrated into the hardware docs: Pi 5 thermal throttling
  (no cooler, 83 °C) + 5 V/5 A bring-up brown-out; ZBLD motor-driver LED fault-code reference;
  encoder velocity-error profile; measured velocity floors; DC power wire colours; battery
  voltage thresholds.
- `LICENSE` (MIT for docs, (c) 2026 OpenAMRobot), `NOTICE.md`, `AUTHORS.md`, `SECURITY.md`,
  `CONTRIBUTING.md` (were empty).

### Fixed
- Drivetrain dimensions in the BOM: corrected the wheel size to the firmware-measured
  ⌀ 0.2 m / track 0.46 m and removed an incorrect "measured 0.046533 m radius" that was a
  CAD-export artifact (axle height), with a note flagging the matching sim (`robot.sdf`) bug.

### To do before release
- CAD Rev B (v0.2) open items:
  - Spacers and heat-set inserts (M4, 2-4 per printed mount) are not modelled yet; they will be
    added with their exact lengths in the drawings and in `manufacturing/bom/mechanical-bom.md`.
  - IMU (ICM-42688-P) and its mounting plate are not designed yet; `imu_link` in the robot
    model stays a placeholder until then.
  - Assembly mates: the TF-Luna mounts are tilted (sensors at 16.2° front, 13.8° rear instead
    of the 10° mount face).
  - Camera mount holes are ⌀4.7 (M3 insert size); M4 inserts need about ⌀5.6.
  - Panel PDF drawings are still Rev A; the panel DXFs are face outlines, not flat patterns.
- Populate or clearly scope the empty `mechanical/`, CAD, and PCB directories.
- Physically verify the track (tape measure) to reconcile firmware 0.46 m vs CAD 0.4075 m.
