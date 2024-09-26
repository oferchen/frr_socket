Here is the `README.md` file for your `BGPDCommunicator` Python program:

```markdown
# BGPDCommunicator

## Description

`BGPDCommunicator` is a Python utility designed to send commands to the BGP daemon (`bgpd`) via a Unix socket and receive responses. The utility connects to the BGP socket at `/var/run/frr/bgpd.vty` (by default) and supports communication with the BGP daemon by sending commands and processing responses. The program is useful for interacting with FRR's BGP services programmatically.

## Features

- Connect to BGP daemon through Unix socket (`/var/run/frr/bgpd.vty`).
- Send BGP commands to the `bgpd` and receive responses.
- Configurable socket path and timeout.
- Handles BGP error codes with detailed error messages.
- Simple command-line interface (CLI) to send commands.
- Automatic command validation and status code checking.

## Requirements

- Python 3.x
- `socket` and `os` standard libraries (already included in Python).
- Ensure the user running the script has permission to access the BGP socket (`/var/run/frr/bgpd.vty`).

## Installation

No special installation steps are required. Just ensure that Python 3.x is installed and run the script.

To install Python 3.x on your system, follow these steps:

### Ubuntu/Debian:

```bash
sudo apt update
sudo apt install python3
```

### Fedora/CentOS/RedHat:

```bash
sudo dnf install python3
```

### MacOS:

```bash
brew install python
```

### Windows:

Download and install Python from [https://www.python.org/downloads/](https://www.python.org/downloads/).

## Usage

This program can be executed from the command line. It requires one argument: the BGP command you want to send to the `bgpd` daemon.

### Basic Syntax

```bash
python bgpd_communicator.py [OPTIONS] <BGP_COMMAND>
```

### Options:

- `--socket`: Path to the bgpd socket (default: `/var/run/frr/bgpd.vty`).
- `--timeout`: Timeout value for the socket in seconds (default: `5`).

### Example Commands

Send the command to show the BGP IPv4 routes:

```bash
python bgpd_communicator.py "show ip bgp"
```

Send the command to show the BGP IPv6 routes:

```bash
python bgpd_communicator.py "show bgp ipv6"
```

Specify a custom socket path:

```bash
python bgpd_communicator.py --socket /custom/path/bgpd.vty "show ip bgp"
```

### Error Handling

The program provides detailed error messages if the connection fails or if the BGP daemon returns an error. It uses predefined error codes for BGP-related issues and displays a human-readable explanation.

### Example Output

```bash
BGP table version is 1000, local router ID is 192.0.2.1
Status codes: s suppressed, d damped, h history, * valid, > best, i - internal,
              r RIB-failure, S Stale, R Removed
```
