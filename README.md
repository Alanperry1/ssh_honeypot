Welcome to the SSH Honeypot project. This repository contains a simple SSH Honeypot setup designed to capture unauthorized SSH login attempts and gather intelligence on potential attackers.

## Introduction

An SSH Honeypot is a decoy system that mimics an SSH server to lure and log unauthorized access attempts. By doing so, it helps in understanding attack patterns, methods used by malicious actors, and can assist in identifying sources of potential security threats.

This project implements a simple, configurable SSH Honeypot that captures authentication attempts and logs them for further analysis.

## Features

- Captures and logs SSH login attempts, including usernames and passwords.
- Provides insights into the source IP addresses of attackers.
- Can be run in a safe, isolated environment.
- Easy setup and configuration.
- Customizable to simulate different SSH services.

## Requirements

- Python 3.6+ (with `pip` for package management)
- OpenSSH or equivalent for simulating the SSH server
- Linux-based system (recommended for networking tools and security measures)

## Installation

To set up the SSH Honeypot, follow the steps below:

1. **Clone the repository:**

    ```bash
    git clone https://github.com/yourusername/ssh-honeypot.git
    cd ssh-honeypot
    ```

2. **Install dependencies:**

    Create a virtual environment (optional but recommended):
    
    ```bash
    python3 -m venv venv
    source venv/bin/activate
    ```

    Install required Python packages:

    ```bash
    pip install -r requirements.txt
    ```

## Usage

Once installed and configured, you can start the SSH Honeypot by running:

```bash
python ssh_honeypot.py
```

The honeypot will start listening on port `2223`, logging all SSH login attempts, and blocking or allowing access based on the IP filtering rules.

You can also run the honeypot in the background using a process manager like `nohup` or `systemd`:

```bash
nohup python ssh_honeypot.py &
```

## Logs and Monitoring

Logs of login attempts, including the attacker’s IP address, time of the attempt, and the credentials they tried, are stored in the file specified in `config.json` (default: `/var/log/ssh_honeypot.log`).

You can monitor the logs in real-time using `tail`:

```bash
tail -f /var/log/ssh_honeypot.log
```

## Security Considerations

While SSH honeypots are useful for gathering intelligence, they can also expose your system to risks. Please consider the following:

- **Isolate the honeypot**: Run the honeypot in a container or virtual machine to prevent attackers from accessing your real system.
- **Never use the real SSH service on the same port**: Ensure your actual SSH service is running on a different port to avoid interference.
- **Legal considerations**: Ensure you are compliant with local laws and regulations regarding monitoring and logging unauthorized access attempts.

## Contributing

Contributions are welcome! Feel free to open issues, submit pull requests, or provide feedback to improve the SSH Honeypot.

### To contribute:

1. Fork the repository.
2. Create a new branch for your feature or bug fix.
3. Submit a pull request with a detailed description of your changes.
