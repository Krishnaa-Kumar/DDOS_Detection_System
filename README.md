# DDoS Detection System

A desktop traffic monitor that captures IP packets, summarizes traffic by protocol, and raises an alert when a source IP exceeds the configured packet threshold.

## Features

- Live packet rate and traffic charts
- Top source IPs and protocol breakdown
- Alerts for source IPs exceeding the threshold
- Alert details with approximate network and location information
- Password setup and an inactivity lock

The app keeps flagged addresses in its own in-memory list. It does not add firewall rules or block traffic at the operating-system level.

## Requirements

- Python 3
- Packet-capture permissions (run with administrator privileges on Windows or `sudo` on Linux/macOS)
- Dependencies from `requirements.txt`

## Setup

```bash
python -m pip install -r requirements.txt
```

Run the application:

```bash
python app.py
```

On Linux or macOS, use:

```bash
sudo python3 app.py
```

The first launch asks you to set an app password. The app stores its password hash and alert database in the current working directory.

## IP information and privacy

When an alert is raised, the app performs reverse DNS and sends the observed source IP to the `ip-api.com` service for approximate network and location details. The service lookup may not return information for private or local addresses. Location and device estimates can be inaccurate.

## Configuration

The packet counting window and alert threshold are set near the top of `app.py` as `TIME_WINDOW` and `THRESHOLD`.

## License

This project is licensed under the MIT License. See [LICENSE](LICENSE).