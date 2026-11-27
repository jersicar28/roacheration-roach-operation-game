# Roacheration: Roach Operation Game

## Overview
Final project for BE3090: Modeling, Analysis, and Design I. An Operation-style game in which a roach leg performs "surgery" on a laser-cut roach body. The script tracks the tip of the leg with a Grove Vision AI V2 module and shows the tracking live in a browser.

## Methods
- `roach_track.py`
  - Talks to the Grove Vision AI V2 over serial at 921600 baud, sending an `AT+INVOKE` command each loop and parsing the JSON detection boxes and image it returns.
  - Keeps detections with score ≥ 40 and computes how much of each of 3 rectangular target zones (T1–T3) the leg box overlaps. Counts the frames in which each target is hit.
  - Logs time, leg position, score and per-target overlap to `leg_track.csv`.
  - Serves a page at `http://localhost:8000` showing the camera frame, the target boxes (green when hit) and the leg's trail.

## Tools
Python, pyserial, Python `http.server`, HTML canvas / JavaScript, Grove Vision AI V2.

## Status
Complete.

**Data:** none included. The script writes `leg_track.csv` locally while running; it is git-ignored.

**Usage:** `python roach_track.py <serial-port>`

**Notes:** this file was exported from Google Colab, but it runs as a plain local script because it needs the serial port.
