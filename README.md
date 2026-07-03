## Kavach-R: Real-Time Ransomware Monitoring & Early Detection System

An AI-powered ransomware early warning system that continuously monitors process behaviour, detects anomalous file activities using machine learning, provides real-time risk analysis through an interactive monitoring dashboard and blocks them immediately as it crosses the threshold.

### Architecture Diagram -

```
┌──────────────┐      risk score     ┌──────────────┐
│  Detection   │ ────────▶────────▶ │  Dashboard   │
│  Engine (ML) │                     │  (CLI live)  │
└──────┬───────┘                     └──────────────┘
       │ threshold crossed
       ▼
┌──────────────┐                     ┌──────────────┐
│    Alerts    │◀────  demo.py  ───▶│  Simulator   │
│  (terminal)  │   orchestrates      │  (safe fake  │
└──────────────┘                     │  ransomware) │
                                     └──────────────┘
```

### Process Flow -

1. Model Training on Existing Files (before attack)

<div align='left'>
  <img src = 'images/Train Model.jpeg' height="300px" width="500px">
</div>

2. Ransomware Attack & Resolution

   - Shows the safe-state 
   - Starts live dashboard in the background
   - Launches simulator to mimic a ransomware attack
   - Ramps up the risk score & trigger alerts when it crosses `0.8`
   - Cools down & returns to safe state

<div align='left'>
  <img src = 'images/Dashboard (Unsecure).jpeg' height="265px" width="500px">
  <img src = 'images/Dashboard (Secure).jpeg' height="300px" width="500px">
</div>
<br>

3. Display of Flagged Files & System Logs

<div align='center'>
  <img src = 'images/Flagged Processes.jpeg' height="300px" width="500px">
  <img src = 'images/System Log.jpeg' height="300px" width="500px">
</div>

### Project Structure - 

```
kavach-r/
├── kavach/               # Detection engine (ML model, feature extraction)
│   ├── detector.py
│   ├── events.py
│   ├── feature_engine.py
│   ├── kavach_main.py
│   └── model.py
├── simulator.py          # Safe ransomware behaviour simulator
├── alerts.py             # Terminal alert display
├── dashboard.py          # Live CLI risk-score dashboard
├── demo.py               # End-to-end demo orchestrator
├── utils.py              # Shared helper functions
├── test_folder/          # Dummy files consumed by the simulator
└── README.md
```

### Project Setup Guide -

 1. Clone the repo: ```git clone <repo-url> && cd Kavach-R```
 2. Install optional dependency: ```pip install colorama```
 3. Ensure test_folder has dummy files (already included): ```ls test_folder/```
 4. Run the complete projevt: ```python demo.py```
 5. Run individual files (optional): ```python dashboard.py``` (dashboard only), ```simulator.py``` (simulator only), ```alerts.py``` (alert samples)
