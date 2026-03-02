# Snort Detection Rule – CVE-2025-55182 (React2Shell RCE)

## 📌 Overview 

This repository contains a custom Snort IDS rule developed to detect exploitation attempts related to **CVE-2025-55182**, a Remote Code Execution (RCE) vulnerability in Node.js applications leveraging the `child_process` module.

The detection focuses on identifying malicious payload patterns that attempt to spawn a shell using `/bin/sh`.

---

- **CVE ID:** CVE-2025-55182
- **Type:** Remote Code Execution (RCE)
- **Affected Technology:** Node.js
- **Attack Vector:** Abuse of `child_process.spawn()` leading to shell execution

Example malicious pattern:

```javascript
require('child_process').spawn('/bin/sh')

# ⚙️ How to Add Rule in Snort

Linux default path:

- /etc/snort/rules/local.rules

Add the rules

- sudo nano /etc/snort/rules/CVE-2025-55182.rules

Add must include it inside snort.conf using:

- /etc/snort/rules/react2shell.rules
  - include $RULE_PATH/CVE-2025-55182.rules

# Test Configuration

sudo snort -T -c /etc/snort/snort.conf

# Run Snort

sudo snort -A console -q -c /etc/snort/snort.conf -i eth0
