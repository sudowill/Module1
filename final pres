#!/usr/bin/env python3
"""
LogSleuth – Python Log Analyzer for Incident Response
"""

import argparse
import os
import re
import json
import csv
from datetime import datetime
from collections import defaultdict

# Configuration (can be externalized later)

DEFAULT_CONFIG = {
    "logs": [
        "auth.log",
        "syslog",
        "access.log"
    ],
    "ioc_file": "iocs.txt",
    "rules": {
        "bruteforce_threshold": 5,
        "suspicious_agents": ["sqlmap", "curl", "nmap", "nikto"]
    },
    "outputs": {
        "alerts_json": "alerts.json",
        "report_txt": "report.txt",
        "events_csv": "events.csv",
        "timeline_txt": "timeline.txt"
    }
}


# Core Engine

class LogEngine:
    def __init__(self, config):
        self.config = config
        self.logs = config["logs"]
        self.ioc_file = config["ioc_file"]
        self.rules = config["rules"]
        self.outputs = config["outputs"]

        self.iocs = set()
        self.events = []
        self.failed_logins = defaultdict(int)

        self._load_iocs()
        self._init_output_files()

    def _init_output_files(self):
        # Truncate alerts.json at start
        try:
            with open(self.outputs["alerts_json"], "w") as f:
                f.write("")
        except Exception as e:
            print(f"[ERROR] Could not initialize alerts file: {e}")

    def _load_iocs(self):
        if not os.path.exists(self.ioc_file):
            print(f"[WARNING] IOC file not found: {self.ioc_file}")
            return

        try:
            with open(self.ioc_file, "r") as f:
                for line in f:
                    line = line.strip()
                    if line:
                        self.iocs.add(line)
            print(f"[INFO] Loaded {len(self.iocs)} IOCs.")
        except Exception as e:
            print(f"[ERROR] Could not load IOC file: {e}")

    def run(self):
        for log_path in self.logs:
            if not os.path.exists(log_path):
                print(f"[WARNING] Log file missing: {log_path}")
                continue

            print(f"[INFO] Analyzing log: {log_path}")
            try:
                with open(log_path, "r", errors="ignore") as f:
                    for line in f:
                        self._apply_rules(line)
            except Exception as e:
                print(f"[ERROR] Failed to read {log_path}: {e}")

    def _apply_rules(self, line):
        self._detect_failed_logins(line)
        self._detect_iocs(line)
        self._detect_user_agents(line)
        self._detect_web_attacks(line)

    # Detection Rules

    def _detect_failed_logins(self, line):
        pattern = r"Failed password for .* from (\d+\.\d+\.\d+\.\d+)"
        match = re.search(pattern, line)

        if match:
            ip = match.group(1)
            self.failed_logins[ip] += 1

            if self.failed_logins[ip] >= self.rules["bruteforce_threshold"]:
                self._log_event(
                    "BRUTE_FORCE",
                    f"Brute-force detected from {ip}",
                    {"ip": ip, "count": self.failed_logins[ip], "source": "auth.log"}
                )

    def _detect_iocs(self, line):
        for ioc in self.iocs:
            if ioc in line:
                self._log_event(
                    "IOC_MATCH",
                    f"IOC detected: {ioc}",
                    {"ioc": ioc, "line": line.strip()}
                )

    def _detect_user_agents(self, line):
        for agent in self.rules["suspicious_agents"]:
            if agent.lower() in line.lower():
                self._log_event(
                    "SUSPICIOUS_USER_AGENT",
                    f"Suspicious user-agent: {agent}",
                    {"agent": agent, "line": line.strip()}
                )

    def _detect_web_attacks(self, line):
        patterns = {
            "SQL_INJECTION": r"(\%27)|(\')|(\-\-)|(\%23)|(#)|(\bOR\b\s+1=1)",
            "LFI": r"\.\./\.\./",
            "XSS": r"<script>|%3Cscript",
            "PATH_TRAVERSAL": r"\.\./"
        }

        for attack, pattern in patterns.items():
            if re.search(pattern, line, re.IGNORECASE):
                self._log_event(
                    attack,
                    f"Possible {attack} attack detected",
                    {"line": line.strip()}
                )

    # Event Logging

    def _log_event(self, event_type, message, details):
        event = {
            "timestamp": datetime.utcnow().isoformat(),
            "type": event_type,
            "message": message,
            "details": details
        }

        self.events.append(event)

        try:
            with open(self.outputs["alerts_json"], "a") as f:
                f.write(json.dumps(event) + "\n")
        except Exception as e:
            print(f"[ERROR] Failed to write alert: {e}")

        print(f"[ALERT] {event_type}: {message}")

# Reporting

class Reporter:
    def __init__(self, engine: LogEngine):
        self.engine = engine
        self.outputs = engine.outputs

    def generate_all_reports(self):
        self._generate_text_report()
        self._generate_csv_report()
        self._generate_timeline()

    def _generate_text_report(self):
        try:
            with open(self.outputs["report_txt"], "w") as f:
                f.write("=== LogSleuth Incident Report ===\n")
                f.write(f"Generated: {datetime.utcnow()}\n\n")

                f.write("Suspicious Events:\n")
                for event in self.engine.events:
                    f.write(f"- {event['timestamp']} | {event['type']} | {event['message']}\n")

                f.write("\nFailed Login Summary:\n")
                for ip, count in self.engine.failed_logins.items():
                    f.write(f"- {ip}: {count} failed attempts\n")

            print(f"[INFO] Text report generated: {self.outputs['report_txt']}")
        except Exception as e:
            print(f"[ERROR] Failed to generate text report: {e}")

    def _generate_csv_report(self):
        try:
            with open(self.outputs["events_csv"], "w", newline="") as f:
                writer = csv.writer(f)
                writer.writerow(["timestamp", "type", "message", "details"])

                for event in self.engine.events:
                    writer.writerow([
                        event["timestamp"],
                        event["type"],
                        event["message"],
                        json.dumps(event["details"])
                    ])

            print(f"[INFO] CSV report generated: {self.outputs['events_csv']}")
        except Exception as e:
            print(f"[ERROR] Failed to generate CSV report: {e}")

    def _generate_timeline(self):
        try:
            sorted_events = sorted(self.engine.events, key=lambda x: x["timestamp"])

            with open(self.outputs["timeline_txt"], "w") as f:
                f.write("=== Attack Timeline ===\n\n")
                for event in sorted_events:
                    f.write(f"{event['timestamp']} - {event['type']} - {event['message']}\n")

            print(f"[INFO] Timeline generated: {self.outputs['timeline_txt']}")
        except Exception as e:
            print(f"[ERROR] Failed to generate timeline: {e}")


# CLI / Main

def load_config(path: str | None):
    if path is None:
        print("[INFO] No config file provided, using default config.")
        return DEFAULT_CONFIG

    if not os.path.exists(path):
        print("[WARNING] Config file not found, using default config.")
        return DEFAULT_CONFIG

    try:
        with open(path, "r") as f:
            cfg = json.load(f)
        print(f"[INFO] Loaded config from {path}")
        return cfg
    except Exception as e:
        print(f"[ERROR] Failed to load config, using default. Error: {e}")
        return DEFAULT_CONFIG


def main():
    parser = argparse.ArgumentParser(description="LogSleuth - Incident Response Log Analyzer")
    parser.add_argument("--config", help="Path to config.json (optional)")
    args = parser.parse_args()

    config = load_config(args.config)

    engine = LogEngine(config)
    engine.run()

    reporter = Reporter(engine)
    reporter.generate_all_reports()


if __name__ == "__main__":
    main()
