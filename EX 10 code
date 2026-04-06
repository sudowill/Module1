mport socket
import ssl

def connect_tcp(host, port, use_tls=False):
    print(f"\n[*] Connecting to {host}:{port} (TLS={use_tls})")

    # Create TCP socket
    sock = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
    sock.settimeout(5)

    try:
        sock.connect((host, port))
        print("[+] TCP connection established")

        # Wrap in TLS if needed
        if use_tls:
            context = ssl.create_default_context()
            sock = context.wrap_socket(sock, server_hostname=host)
            print("[+] TLS handshake completed")

        # Send HTTP GET request
        request = f"GET / HTTP/1.1\r\nHost: {host}\r\nConnection: close\r\n\r\n"
        sock.send(request.encode())

        # Receive response
        response = sock.recv(1024).decode(errors="ignore")
        print("[+] Received response:")
        print(response.split("\r\n")[0])  # Print only the status line

    except Exception as e:
        print(f"[!] Connection failed: {e}")

    finally:
        sock.close()


 #required port 80 link
# 1) HTTP (port 80) — Instructor-provided website
connect_tcp("uniquebeautifulgrandlight.neverssl.com", 80, use_tls=False)

#MY CHOICE (HTTPS)
# 2) HTTPS (port 443)
connect_tcp("google.com", 443, use_tls=True)
connect_tcp("microsoft.com", 443, use_tls=True)
connect_tcp("github.com", 443, use_tls=True)

import socket
import random
import struct

def build_dns_query(domain):
    # Transaction ID (random 16-bit)
    tid = random.randint(0, 65535)

    # Flags: standard query, recursion desired
    flags = 0x0100

    # QDCOUNT = 1 (one question)
    qdcount = 1
    ancount = 0
    nscount = 0
    arcount = 0

    header = struct.pack(">HHHHHH", tid, flags, qdcount, ancount, nscount, arcount)

    # Build QNAME (split domain into labels)
    qname = b""
    for part in domain.split("."):
        qname += struct.pack("B", len(part)) + part.encode()
    qname += b"\x00"  # end of QNAME

    # QTYPE = 1 (A record), QCLASS = 1 (IN)
    question = qname + struct.pack(">HH", 1, 1)

    return tid, header + question


def parse_dns_response(data):
    # Skip header (12 bytes)
    header = data[:12]
    tid, flags, qdcount, ancount, _, _ = struct.unpack(">HHHHHH", header)

    # Skip question section
    offset = 12
    for _ in range(qdcount):
        while data[offset] != 0:
            offset += 1 + data[offset]
        offset += 5  # null byte + QTYPE + QCLASS

    # Parse answers
    ips = []
    for _ in range(ancount):
        # Skip name pointer (2 bytes), type (2), class (2), TTL (4)
        offset += 10
        rdlength = struct.unpack(">H", data[offset:offset+2])[0]
        offset += 2

        # If A record (IPv4)
        if rdlength == 4:
            ip = ".".join(str(b) for b in data[offset:offset+4])
            ips.append(ip)

        offset += rdlength

    return ips


def dns_lookup(domain):
    print(f"\n[*] Resolving: {domain}")

    tid, query = build_dns_query(domain)

    sock = socket.socket(socket.AF_INET, socket.SOCK_DGRAM)
    sock.settimeout(3)

    # Send to Google DNS
    sock.sendto(query, ("8.8.8.8", 53))

    try:
        data, _ = sock.recvfrom(512)
        ips = parse_dns_response(data)
        print(f"[+] {domain} resolved to: {ips}")
    except Exception as e:
        print(f"[!] DNS lookup failed: {e}")

    sock.close()


#Perform DNS lookups for 3 websites
dns_lookup("google.com")
dns_lookup("microsoft.com")
dns_lookup("github.com")
