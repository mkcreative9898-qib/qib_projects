# 🚗 Vehicle Speed Tracker (Computer Vision & Telemetry System)

A modular, real-time Computer Vision system designed to track vehicular movement, accurately calculate vehicle speeds through visual calibration, detect traffic threshold infractions, and transmit secure data packets directly to an automated telemetry web server portal backend.

This system is built entirely using **Python**, featuring an architecture tailored for edge computing processing deployment (e.g., standard servers or local computing stations) alongside scalable cloud or local hosting APIs.

---

## 🏛️ System Architecture Workflow

The system is split into two independent processing layers:

1. **Edge Simulator Node (`mock_video_stream.py`):**
   * Uses **OpenCV** to stream spatial video tracking.
   * Tracks unique vehicle identity coordinates across multi-frame sequences.
   * Employs a calibrated **Pixels-to-Meters Mapping Engine** to compute moving objects' real-world speeds over defined virtual gate lines (\(Speed = \frac{\Delta Distance}{\Delta Time}\)).
   * Packages telemetry into structural JSON payloads and transmits metrics over HTTP client channels.

2. **Ingestion API Server (`server_portal.py`):**
   * High-performance processing gateway powered by **FastAPI** & **Uvicorn**.
   * Validates incoming schema boundaries through strict **Pydantic models**.
   * Logs incoming telemetry structures instantly into a relational **SQLite database (`telemetry_logs.db`)**.
   * Flags speeding infractions over predefined regional velocity speed limits (e.g., > 100 km/h).

---

## 🛠️ Project Stack & Tooling

* **Language Engine:** Python 3.10+
* **Computer Vision Processing:** OpenCV Python, NumPy
* **Core API Framework:** FastAPI
* **Development Server Network:** Uvicorn Engine
* **Validation Subsystem:** Pydantic
* **Persistent Data Layer:** SQLite3

---

## 📁 Repository Directory Structure

Ensure your file trees match the following hierarchy within your local workspace directory:

```text
D:/QIB-PROJECTS/car_speed_tracker/
│
├── server_portal.py        # FastAPI Gateway API Server & Database Management
├── mock_video_stream.py    # Multi-Object CV Speed Tracker Engine & Video Box
├── requirements.txt        # Universal Project Dependency Libraries Configurations
└── README.md               # System Documentation & Reference Guides
```

---

## 🚀 Execution & Quick-Start Guide

Follow these steps within your integrated development terminal environment to spin up the local ecosystem testing frame loops:

### 1. Initialize Workspace Environment & Dependencies
```bash
# Navigate to the workspace path directory
cd "D:\QIB-PROJECTS\car_speed_tracker"

# Install all necessary python libraries
pip install -r requirements.txt
```

### 2. Launch the Telemetry Ingestion Server Backend
```bash
python server_portal.py
```
*The service will start broadcasting locally on **`http://localhost:8000`**. You can view the fully interactive swagger API documentation platform sandbox panel via browser at `http://localhost:8000/docs`.*

### 3. Initialize the Video Stream Simulator Node
Open up a **secondary concurrent terminal tab instance** and execute:
```bash
python mock_video_stream.py
```
*A graphic UI window frame pane will pop onto the desktop monitor tracking synthetic traffic objects. Press **`q`** inside the active canvas frame pane to safely terminate execution loops.*

### 4. Fetch Traffic Violations Logging Analytics
To inspect all recorded historical tracking arrays and infractions captured inside your persistent SQLite DB engine layer, access this local web gateway route endpoint directly inside any browser tab page:
👉 **[http://localhost:8000/api/v1/telemetry/logs](http://localhost:8000/api/v1/telemetry/logs)**

---

## 🌐 Deploying into Git & GitHub Repository

To commit this codebase module straight into your existing remote repository named **`qib_projects`**, execute the following command series via Git CLI inside your local terminal application window:

```bash
# 1. Initialize local repository profile settings if not yet set up
git init

# 2. Add files to the staging cache index
git add .

# 3. Create a clean history checkpoint commit message block
git commit -m "feat: implement modular vehicle speed tracking vision framework with sqlite logging"

# 4. Link up your personal remote repository target path configuration settings
git remote add origin https://github.com<YOUR-USERNAME>/qib_projects.git

# 5. Push clean code branches up to the main branch network cleanly
git branch -M main
git push -u origin main
```
