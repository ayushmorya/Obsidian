In Linux, different commands are used to monitor **VM (Virtual Memory) stats** and **Network (NET) stats**. Here’s a breakdown of the most commonly used ones:

---

## **VM Stats (Virtual Memory Statistics) Commands**

These commands help monitor memory usage, swap usage, and process performance.

### 1️⃣ `vmstat` – Reports memory, CPU, and I/O statistics

```bash
vmstat 1 5  # Refresh every 1 second, 5 times
```

- **r**: Number of processes waiting for CPU
- **b**: Blocked processes
- **swpd**: Swap memory usage
- **free**: Free RAM
- **si/so**: Swap-in and swap-out
- **bi/bo**: Disk I/O

### 2️⃣ `free` – Displays available and used memory

```bash
free -h  # Human-readable format
```

- Shows **total, used, free, and swap memory**.

### 3️⃣ `top` / `htop` – Real-time process and memory monitoring

```bash
top  # Press 'M' to sort by memory
htop  # More interactive (if installed)
```

- Shows which processes are consuming the most **CPU and memory**.

### 4️⃣ `sar` – Historical memory & CPU usage analysis

```bash
sar -r 5 10  # Memory usage every 5 seconds, 10 times
```

- Needs `sysstat` package installed.

### 5️⃣ `/proc/meminfo` – Detailed system memory info

```bash
cat /proc/meminfo
```

- Displays in-depth memory statistics.

---

## **NET Stats (Network Statistics) Commands**

These commands help monitor network traffic, connections, and performance.

### 1️⃣ `netstat` – Displays network connections, routing tables, and stats

```bash
netstat -tulnp  # Show active listening ports with process names
```

- **t**: TCP connections
- **u**: UDP connections
- **l**: Listening ports
- **n**: Show numerical addresses
- **p**: Show associated process

_(Note: `netstat` is deprecated, use `ss` instead.)_

### 2️⃣ `ss` – Faster alternative to `netstat`

```bash
ss -tulwn  # Show open ports and active connections
```

- More efficient than `netstat`.

### 3️⃣ `ifconfig` / `ip a` – Show network interface details

```bash
ifconfig  # Deprecated, use 'ip a'
ip a  # Show all IP addresses
```

### 4️⃣ `ip` – Advanced network configuration

```bash
ip link show  # Show network interfaces
ip route show  # Show routing table
```

### 5️⃣ `ping` – Check network connectivity

```bash
ping google.com  # Test network reachability
```

### 6️⃣ `traceroute` – Trace packet path to a destination

```bash
traceroute google.com
```

### 7️⃣ `nslookup` / `dig` – DNS lookup

```bash
nslookup google.com  # Resolve domain name
dig google.com  # Detailed DNS info
```

### 8️⃣ `nmap` – Scan network for open ports

```bash
nmap -p 22,80,443 192.168.1.1  # Scan specific ports
```

_(Needs `nmap` installed.)_

---

### **Summary**

|Type|Command|Usage|
|---|---|---|
|**VM Stats**|`vmstat`|Overall memory and CPU usage|
||`free -h`|Available and used RAM|
||`top` / `htop`|Process and memory monitoring|
||`sar -r`|Historical memory stats|
||`cat /proc/meminfo`|Detailed memory info|
|**NET Stats**|`netstat` / `ss`|Network connections and ports|
||`ip a` / `ifconfig`|Show network interfaces|
||`ip route show`|Show routing table|
||`ping`|Check connectivity|
||`traceroute`|Trace packet route|
||`nslookup` / `dig`|DNS lookup|
||`nmap`|Scan open ports|

These commands are useful for system administrators and DevOps engineers to monitor VM performance and troubleshoot network issues. 🚀