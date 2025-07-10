# Task Summary: Re-Identification in a Single Feed
## Objective: 
You are given a 15-second video showing a football  game.

Your task is to:
1. Detect each player in the video.
2. Assign an ID to each player at the start.
3. Track each player through the video.
4. If a player leaves the frame and comes back later, assign the same ID — that’s called re-identification.

## How We Solve This:
1. Use the Provided YOLOv11 Model

**Pre-trained Model:** https://drive.google.com/file/d/1-5fOSHOSB9UXyP_enOoZNAMScrePVcMD/view
- A pre-trained YOLOv11 object detection model is given.
- It detects players and balls in each frame of the video.

2. Track Players Using DeepSORT
- We integrate DeepSORT, a tracking algorithm that:
  - Follows objects across frames.
  - Maintains consistent IDs even after short disappearances.
  - Matches players using their appearance and movement.
 
3. Re-Identification Logic
- DeepSORT tracks objects even if they briefly leave and re-enter the frame.
- It uses internal logic (bounding box + visual features) to match the returning player to their original ID.

# How to Set Up and Run the Code
Run in Google Colab:

* Step 1: Create a notebook/project in Google Colab
* Step 2: Upload your model and video files when prompted
* Step 3: Run all cells in Re-Identification in a Single Feed.ipynb

# Dependencies and Environment Required
| Package                  | Version / Notes                           |
| ------------------------ | ----------------------------------------- |
| `ultralytics`            | for YOLOv11 model inference               |
| `opencv-python-headless` | for video processing (Colab safe)         |
| `deep_sort_realtime`     | for object tracking and re-identification |

✅ Install all in Colab:

`!pip install ultralytics`

`!pip install opencv-python-headless`

`!pip install deep_sort_realtime`

### Key Features
* Uses YOLOv11 for player detection
* Uses DeepSORT for ID assignment and re-identification
* Handles reappearance of players after occlusion
* Export final video with tracked player IDs

### Exported final video
![Video](https://github.com/Bornarekrishna/Re-Identification-in-a-Single-Feed/blob/main/tracked_output%20.mp4)
