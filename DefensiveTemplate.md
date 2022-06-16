# Blue Team: Summary of Operations

## Table of Contents
- Network Topology
- Description of Targets
- Monitoring the Targets
- Patterns of Traffic & Behavior
- Suggestions for Going Further

### Network Topology
_TODO: Fill out the information below._

The following machines were identified on the network:
- Capstone
  - **Operating System**: Linux
  - **Purpose**: Forwards Filebeat, Packetbeat and Metricbeat logs that are installed on the machine to the ELK server
  - **IP Address**: 192.168.1.105
- ELK
  - **Operating System**: Linux
  - **Purpose**: Collects filebeat, metricbeat and packetbeat log data from the Capstone and Target 1 servers
  - **IP Address**: 192.168.1.100
- Kali
  - **Operating System**: Linux
  - **Purpose**: Kali machine that is used to conduct pentration testing on Target 1
  - **IP Address**: 192.168.1.90
- Target 1
  - **Operating System**: Linux
  - **Purpose**: Vulnerable WordPress Host
  - **IP Address**: 192.168.1.110


### Description of Targets
_TODO: Answer the questions below._

The target of this attack was: `Target 1` (192.168.1.110).

Target 1 is an Apache web server and has SSH enabled, so ports 80 and 22 are possible ports of entry for attackers. As such, the following alerts have been implemented:

### Monitoring the Targets

Traffic to these services should be carefully monitored. To this end, we have implemented the alerts below:

#### Excessive HTTP Errors
Alert 1 is implemented as follows:
  - **Metric**: WHEN count() GROUPED OVER top 5 'http.response.status_code'
  - **Threshold**: ABOVE 400 FOR THE LAST 5 minutes
  - **Vulnerability Mitigated**: Bruteforce and Enumeration
  - **Reliability**: High reliability, detects only reponse codes that are higher than 400. This means that it only shows when an error takes place. This alert is useful a error codes are taking place at a higher rate because of a bruteforce attack or enumeration. Since the timeframe in threshold is short there is a low chance of false positives.

#### HTTP Request Size Monitor
Alert 2 is implemented as follows:
  - **Metric**: WHEN sum() of http.request.bytes OVER all documents
  - **Threshold**: ABOVE 3500 FOR THE LAST 1 minute
  - **Vulnerability Mitigated**: Cross Site Scripting/Cross Site Request Forgery
  - **Reliability**: Medium reliability, the total bytes of a request header can range form ~200 bytes to over 2000 bytes. Therefore, there is a potential for many false positives.

#### CPU Usage Monitor
Alert 3 is implemented as follows:
  - **Metric**: WHEN max() OF system.process.cpu.total.pct OVER all documents
  - **Threshold**: ABOVE 0.5 FOR THE LAST 5 minutes
  - **Vulnerability Mitigated**: Malicious software being used on the machine
  - **Reliability**: Highly Reliable. Normal CPU usage is typically between 10% to 30% and there can be instances where the usage can reach an even higher percentage and immediately drop back down to normal with certain processes. This alert can show when someone is using a malicious software on the machine or if CPU usage can be improved on the machine



### Suggestions for Going Further (Optional)
_TODO_: 
- Each alert above pertains to a specific vulnerability/exploit. Recall that alerts only detect malicious behavior, but do not stop it. For each vulnerability/exploit identified by the alerts above, suggest a patch. E.g., implementing a blocklist is an effective tactic against brute-force attacks. It is not necessary to explain _how_ to implement each patch.

The logs and alerts generated during the assessment suggest that this network is susceptible to several active threats, identified by the alerts above. In addition to watching for occurrences of such threats, the network should be hardened against them. The Blue Team suggests that IT implement the fixes below to protect the network:
- Vulnerability 1
  - **Patch**: TODO: E.g., _install `special-security-package` with `apt-get`_
  - **Why It Works**: TODO: E.g., _`special-security-package` scans the system for viruses every day_
- Vulnerability 2
  - **Patch**: TODO: E.g., _install `special-security-package` with `apt-get`_
  - **Why It Works**: TODO: E.g., _`special-security-package` scans the system for viruses every day_
- Vulnerability 3
  - **Patch**: TODO: E.g., _install `special-security-package` with `apt-get`_
  - **Why It Works**: TODO: E.g., _`special-security-package` scans the system for viruses every day_
