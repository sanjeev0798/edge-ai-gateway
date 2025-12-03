# Edge AI Gateway Pipeline (ESP32 → MQTT → Linux)

This project implements a simple **edge intelligence pipeline**:

`[ESP32] -- MQTT --> [Linux Gateway] -- Python (Anomaly Detection) --> Plot`

## Components

- **ESP32**  
  - Reads an analog sensor value (or floating pin noise)  
  - Normalizes it and publishes JSON payloads via MQTT  

- **Linux Gateway**  
  - Runs an MQTT broker (e.g. Mosquitto)  
  - Python subscriber receives the stream  
  - Maintains a rolling window and performs z-score based anomaly detection  
  - Visualizes the stream and anomalies with matplotlib  

## Structure

```text
edge-ai-gateway-esp32/
├── README.md
├── esp32/
│   └── esp32_mqtt_publisher.ino
└── gateway/
    ├── requirements.txt
    └── subscriber_anomaly.py
