# YOLO Dataset Editor

## Overview
YOLO Dataset Editor is a standalone Windows application for editing and annotating YOLO-format datasets. It allows users to upload datasets, configure class names, annotate images with bounding boxes, mark images as checked, and export the updated dataset. The app is packaged as a single executable (`YOLO Dataset Editor.exe`) for easy distribution and use without requiring Python or other dependencies.

This tool is ideal for computer vision tasks, such as preparing datasets for object detection models like YOLO. It supports loading previous work, navigating through images, and tracking progress with checked images.

## Features
- **Dataset Upload**: Upload a ZIP file containing `images/` and `labels/` folders.
- **Class Configuration**: Define class names dynamically, mapped to IDs starting from 0.
- **Annotation Interface**:
  - Draw new bounding boxes with mouse.
  - Edit box classes via dropdown.
  - Delete boxes.
  - Save annotations automatically on navigation.
- **Navigation**: Prev/Next buttons to browse images, with auto-save and "mark as checked" on Next.
- **Progress Tracking**: Mark images as checked; visual indicator on the button.
- **Export**: Download the updated dataset as a ZIP.
- **Project Management**: On startup, choose to load the current dataset or start a new project (which resets everything).
- **Persistent State**: Saves last viewed image and checked status for resuming work.

## System Requirements
- Windows OS (tested on Windows 10/11).
- No additional software needed—the .exe is self-contained.
- Disk space for datasets (stored in a `storage/` folder next to the .exe).

## Installation
1. Download the `YOLO Dataset Editor.exe` from the [GitHub Releases](https://github.com/yourusername/YOLO-Dataset-Editor/releases](https://github.com/ChamudithaEkanayake/YOLO-Dataset-Editor-YDE-/blob/main/YOLO%20Dataset%20Editor.exe) page.
2. Place the .exe in a folder where you have write permissions (it creates a `storage/` subfolder for data).
3. Double-click the .exe to run. A console window will open, showing the server starting.
4. Open a web browser and go to `http://127.0.0.1:5000` (or the address shown in the console).

**Note**: The app runs a local web server. Close the console window to stop the app.

## Usage Guide

### 1. Starting the App
- Run the .exe.
- In your browser, you'll see the **Project Choice** screen:
  - **Load Current Working Dataset**: Resumes from where you left off (if a previous dataset exists). Loads the last viewed image and preserves checked status.
  - **Create New Project**: Deletes any existing data and starts fresh.

### 2. Creating a New Project
- Select **Create New Project**.
- You'll be taken to the **Upload Dataset** page.
- Prepare a ZIP file with:
  ```
  your_dataset.zip
  ├── images/
  │   └── image1.jpg (etc.)
  └── labels/
      └── image1.txt (YOLO format: class_id x_center y_center width height)
  ```
- Upload the ZIP and click **Upload and Proceed**.

### 3. Configuring Classes
- After upload, enter class names in a textarea, separated by commas (e.g., `0,1,2,A,B,airforce,army,navy,sri`).
- These are mapped to IDs (0 for first, 1 for second, etc.).
- Click **Submit Classes and Proceed** to enter the annotation interface.

### 4. Annotation Interface
- **Controls (Left Panel)**:
  - **Prev/Next**: Navigate images. Next also saves annotations and marks the current image as checked.
  - **Annotate**: Toggle to draw/edit boxes.
    - Click and drag to draw a new box, then select class from dropdown.
    - Click on a box to edit its class.
  - **Delete**: Toggle to remove boxes by clicking on them.
  - **Mark as Checked**: (Integrated into Next) Marks the image as reviewed (button turns green when checked).
  - **Save**: Manually save current annotations.
  - **Export ZIP**: Save and download the dataset.
  - **Go To Home**: Reset and return to project choice.
- **Main Panel**: Displays the image with overlay canvas for boxes.
- **Progress**: Shows current image number and filename.
- Boxes are saved in YOLO format in the labels/ folder.

### 5. Resuming Work
- On restart, choose **Load Current Working Dataset**.
- It loads the previous dataset, classes, and jumps to the last viewed image.
- Checked images are highlighted (green button).

### 6. Exporting
- Click **Export ZIP** to download a ZIP with updated `images/` and `labels/`.

### 7. Resetting
- From the annotation page, use **Go To Home** to reset.
- Confirms before deleting data.

## Troubleshooting
- **App Not Starting**: Ensure no other app uses port 5000. Change port in app.py if needed (advanced).
- **Browser Issues**: Use Chrome/Firefox. Refresh if UI glitches.
- **Large Datasets**: May be slow; process in batches.
- **Errors**: Check console for logs. Common: Invalid ZIP structure—ensure `images/` and `labels/` are at root.
- **No Data on Load**: If `storage/` is empty or corrupted, start a new project.

## Development
- Built with Flask, Pillow, and JavaScript.
- Source code available on GitHub.
- To build from source: `pip install -r requirements.txt`, then `python app.py`.

## License
MIT License. See LICENSE file for details.

## Contact
For issues, open a GitHub issue or contact [chamuditha.hde@gmail.com].

--- 

