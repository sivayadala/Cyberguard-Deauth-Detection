# 📁 Recommended Repository Structure
# cyberguard-deauth-detection/

cyberguard-deauth-detection/
│
├── data/
│   ├── normal_traffic.csv          # Captured normal traffic features
│   └── attack_traffic.csv          # Captured attack traffic features
│
├── model/
│   ├── train_model.py              # Train Random Forest classifier
│   ├── evaluate_model.py           # Generate metrics, confusion matrix, ROC
│   └── random_forest_model.pkl     # Saved trained model (add to .gitignore or Git LFS)
│
├── capture/
│   ├── packet_capture.py           # Live Scapy-based packet sniffing
│   └── feature_extraction.py      # Extract features from time windows
│
├── prevention/
│   └── prevention_module.py        # Send corrective auth/re-assoc packets
│
├── dashboard/
│   ├── app.py                      # Flask + WebSocket backend
│   ├── templates/
│   │   └── index.html              # Dashboard HTML
│   └── static/
│       ├── style.css               # Dashboard styling
│       └── script.js               # WebSocket client logic
│
├── notebooks/
│   └── analysis.ipynb              # EDA, model experiments, visualizations
│
├── screenshots/                    # Add dashboard/result screenshots here
│   ├── normal_traffic.png
│   ├── under_attack.png
│   ├── confusion_matrix.png
│   └── roc_curve.png
│
├── requirements.txt                # Python dependencies
├── .gitignore                      # Files to exclude from Git
├── LICENSE                         # MIT License
└── README.md                       # Project documentation
