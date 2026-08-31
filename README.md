# Network Anomaly Detector

A Python-based network anomaly detection tool that captures live network
traffic and identifies unusual activity using the Isolation Forest algorithm.

The project uses Scapy for packet capture and scikit-learn for machine
learning. Detected anomalies are stored in a CSV file for further analysis.


## Features

- Live network packet capture using Scapy
- Network packet feature extraction
- Unsupervised anomaly detection using Isolation Forest
- Configurable network interface
- Configurable packet capture limit
- CSV output for detected anomalies
- Modular project structure


## Project Structure

Network_anamolity_detector/
|
├── config/
│   └── settings.py
|
├── core/
│   ├── model.py
│   ├── packet_sniffer.py
│   └── utils.py
|
├── data/
│   └── anomalies.csv
|
├── main.py
├── requirements.txt
└── README.md


## File Description

config/settings.py
    Contains application configuration such as the network interface,
    output file path, and packet capture settings.

core/model.py
    Contains the Isolation Forest model and anomaly detection logic.

core/packet_sniffer.py
    Captures network packets and extracts relevant features.

core/utils.py
    Contains utility and helper functions used by the application.

data/anomalies.csv
    Stores detected network anomalies.

main.py
    Main entry point of the application.

requirements.txt
    Contains the required Python dependencies.


## How It Works

The application follows the following workflow:

    Network Interface
           |
           v
    Packet Capture
           |
           v
    Feature Extraction
           |
           v
    Isolation Forest
           |
           v
    Anomaly Detection
           |
           v
    anomalies.csv


1. Packet Capture

   Scapy captures packets from the configured network interface.


2. Feature Extraction

   Relevant information is extracted from each packet and converted into
   numerical features for analysis.


3. Anomaly Detection

   The extracted features are analyzed using the Isolation Forest algorithm.

   Isolation Forest is an unsupervised machine learning algorithm that
   identifies data points that differ significantly from normal patterns.


4. Anomaly Logging

   Detected anomalies are written to:

       data/anomalies.csv


## Requirements

- Python 3.6+
- Scapy
- scikit-learn
- pandas


## Installation

### 1. Clone the repository

    git clone <repository-url>
    cd Network_anamolity_detector


### 2. Create a virtual environment

Linux / macOS:

    python3 -m venv venv
    source venv/bin/activate

Windows:

    python -m venv venv
    .\venv\Scripts\activate


### 3. Install dependencies

    pip install -r requirements.txt


## Configuration

Edit the following file:

    config/settings.py

Configure the network interface and other application settings.

Example:

    INTERFACE = "eth0"
    OUTPUT_PATH = "data/anomalies.csv"
    PACKET_LIMIT = 1000

The available configuration options depend on the implementation in
config/settings.py.


## Finding the Network Interface

Linux:

    ip link

or:

    ifconfig

macOS:

    ifconfig

Windows:

    ipconfig

Set the appropriate interface in config/settings.py.


## Usage

Run the application:

    python main.py

On Linux/macOS, packet capture may require elevated privileges:

    sudo ./venv/bin/python main.py


## Output

Detected anomalies are saved to:

    data/anomalies.csv

The output can be analyzed using Pandas, Excel, Jupyter Notebook, or
other data analysis tools.

The exact CSV fields depend on the features extracted by the packet
sniffer.


## Isolation Forest

This project uses Isolation Forest for unsupervised anomaly detection.

The algorithm works by isolating individual observations within the
dataset. Observations that are easier to isolate are considered more
likely to be anomalous.

This approach allows the detector to identify unusual network patterns
without requiring predefined signatures for every type of activity.

An anomaly does not necessarily indicate malicious activity. Legitimate
network traffic can also produce anomalous results.


## Customization

The project can be extended by modifying the following components:

Packet Features
    Modify core/packet_sniffer.py to add or change the features extracted
    from network packets.

Detection Model
    Modify core/model.py to adjust the Isolation Forest configuration
    and detection logic.

Configuration
    Modify config/settings.py to change packet capture and output
    settings.

Output
    The logging functionality can be extended to support additional
    formats such as JSON or database storage.


## Future Improvements

- Real-time monitoring dashboard
- Network flow analysis
- Traffic visualization
- Configurable anomaly thresholds
- JSON output support
- Historical traffic analysis
- Email and webhook alerts
- SIEM integration
- Automated testing
- Docker support


## Security Notice

Network packet capture may contain sensitive information.

Only use this tool on networks and systems that you own or have explicit
permission to monitor.

Protect generated logs and captured data appropriately.


## Disclaimer

This project is intended for educational, research, and authorized
network monitoring purposes.

It is not intended to replace a production-grade IDS, IPS, SIEM, or
network security monitoring platform.

Machine learning-based anomaly detection may produce false positives
and false negatives. Detected anomalies should be investigated using
additional network context.


## License

MIT License

See the LICENSE file for details.
