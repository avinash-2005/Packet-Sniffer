# Packet-Sniffer
A Python-based mini packet sniffer using Scapy. Captures live network traffic, displays IPs, ports, protocol details, and packet length. Auto-stops after a set number of packets and saves them as a .pcap file for analysis in Wireshark. Supports TCP/UDP/ICMP filtering.
How to Run
1. Install Python

Download and install Python 3.x from python.org
.

Make sure to check “Add Python to PATH” during installation.

Verify installation:

python --version

2. Install Wireshark & Npcap

Download Wireshark from wireshark.org/download

Install Npcap when prompted (required for packet capturing on Windows).

3. Setup Project Folder

Create a folder, e.g.:

C:\Users\<your name>\Documents\PacketSniffer


Place your sniffer_scapy.py file inside this folder.

4. Setup Virtual Environment

Open VS Code as Administrator, then in terminal:

# Create virtual environment
python -m venv venv

# Activate virtual environment (PowerShell)
.\venv\Scripts\Activate

5. Install Dependencies

Install Scapy:

pip install scapy

6. Run the Sniffer

Run your script:

# Capture all packets
python sniffer_scapy.py

# Capture only TCP packets
python sniffer_scapy.py tcp

# Capture only UDP packets
python sniffer_scapy.py udp

# Capture HTTP traffic (port 80)
python sniffer_scapy.py "port 80"

# Capture traffic to/from a specific host
python sniffer_scapy.py "host 8.8.8.8"


The sniffer auto-stops after 60 packets by default.

Packet details and a summary will appear in the terminal.

7. View Captured Packets in Wireshark

After the sniffer stops, it saves captured packets to:

C:\Users\<your name>\Documents\PacketSniffer\capture.pcap


Open Wireshark.

Go to File → Open, navigate to the above folder, and select capture.pcap.

The Wireshark interface will show three main panels:

Packet List Pane: shows each captured packet with Time, Source, Destination, Protocol, Length, Info.

Packet Details Pane: click a packet to expand and view header details (Ethernet, IP, TCP/UDP layers).

Packet Bytes Pane: raw hex and ASCII representation of packet data.

Use display filters to focus on specific packets, e.g.:

tcp → only TCP packets

udp → only UDP packets

ip.addr == 192.168.1.10 → packets to/from a specific IP

tcp.port == 80 → packets on HTTP port

This allows you to analyze the captured network traffic visually and understand communication between devices.
