# 📁 Repository Structure
```
cyberguard-deauth-detection/
│
├── model/
│   ├── train_model.py            # Train Random Forest classifier
│   ├── test_model.py             # Evaluate and test the model
│   └── deauth_detector.pkl       # Saved trained model
│
├── capture/
│   ├── capture_attack.py         # Capture attack traffic
│   └── capture_normal.py         # Capture normal traffic
│
├── dashboard/
│   ├── app.py                    # Flask backend
│   ├── templates/
│   │   └── 1index.html           # Main dashboard HTML
│   └── static/
│       ├── 1script.js            # Frontend JS
│       └── 1style.css            # Frontend CSS
│
├── screenshots/
│   └── Screenshot_2025-08-24.png # Dashboard screenshot
│
├── requirements.txt
├── .gitignore
└── README.md
```
