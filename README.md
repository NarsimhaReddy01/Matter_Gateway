# Matter Gateway — Milestone 1

### 🔹 Overview
This repository contains the **base Matter Gateway implementation** and the **first virtual device (On/Off Lamp)**.  
It establishes the foundational architecture for simulating Matter-compliant smart devices that can be controlled via REST APIs.

---

## Milestone 1 Features

| Component | Description |
|------------|-------------|
| **Base Gateway** | Core framework to register, manage, and interact with virtual devices. |
| **On/Off Lamp** | First functional virtual device supporting power ON/OFF control. |
| **REST API** | FastAPI-powered endpoints for listing, reading, and updating device states. |
| **Commissionable Bridge (Scaffold)** | Gateway acts as a bridge exposing endpoints for future Matter integration. |
| **Persistence Scaffold** | Placeholder for saving/restoring device state (coming in Milestone 3). |

---

## Project Structure
Matter_Gateway/
├── api/
│ ├── init.py
│ └── rest_api.py
├── core/
│ ├── init.py
│ ├── device_base.py
│ ├── gateway.py
│ └── persistence.py
├── devices/
│ ├── init.py
│ └── onoff_lamp.py
├── requirements.txt
└── run_gateway.py



---

## Setup & Run Instructions

### Create Virtual Environment
```bash
python -m venv venv
source venv/bin/activate        # On Windows: venv\Scripts\activate
pip install -r requirements.txt

# To the run the gateway
python run_gateway.py

--> Server starts at:
 http://localhost:8000

--> REST API Endpoints
Method	Endpoint	Description
GET	/devices	List all registered virtual devices
GET	/devices/{name}	Read device state
POST	/devices/{name}/{attribute}?value={bool}	Update device state


--> Testing the On/Off Lamp
curl http://localhost:8000/devices
curl -X POST "http://localhost:8000/devices/LivingRoomLamp/power?value=true"
curl http://localhost:8000/devices/LivingRoomLamp
curl -X POST "http://localhost:8000/devices/LivingRoomLamp/power?value=false"