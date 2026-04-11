import socket
import sys
from datetime import datetime

# Simple TCP Port Scanner

def scan_host(target, ports):
    print(f"\n=== Scanning {target} ===")
    try:
        target_ip = socket.gethostbyname(target)
        print(f"Resolved IP: {target_ip}")
    except socket.gaierror:
        print("Could not resolve hostname.")
        return

    print(f"Scan started at: {datetime.now()}\n")

    for port in ports:
        s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
        s.settimeout(0.5)

        result = s.connect_ex((target_ip, port))
        if result == 0:
            print(f"[OPEN] Port {port}")
        s.close()

    print(f"Scan finished at: {datetime.now()}\n")


if __name__ == "__main__":
    # Ports to scan (you can add more)
    ports_to_scan = [22, 80, 443, 8080, 3306, 3389]

    # Authorized targets
    targets = [
        "scanme.nmap.org",
        "teameffort.work",
        "127.0.0.1"
    ]

    for t in targets:
        scan_host(t, ports_to_scan)

        #sniffer.py
from scapy.all import sniff, TCP, IP

def packet_callback(packet):
    if packet.haslayer(TCP) and packet.haslayer(IP):
        ip_layer = packet[IP]
        tcp_layer = packet[TCP]

        print(f"{ip_layer.src}:{tcp_layer.sport}  -->  {ip_layer.dst}:{tcp_layer.dport}  Flags={tcp_layer.flags}")

sniff(filter="tcp", prn=packet_callback, store=0)
