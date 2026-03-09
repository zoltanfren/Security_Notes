# Basic System Information

## Windows Command Execution Path
- Commands can only run if they exist in directories listed in the **PATH environment variable**.
- The `set` command shows environment variables including Path.
- The **Path variable** lists directories where Windows searches for executables.

Example:
Path=C:\Windows\system32;C:\Windows;C:\Windows\System32\Wbem;...

## Checking the Windows Version
- The `ver` command displays the **Windows OS version**.

## Getting System Information
- The `systeminfo` command shows detailed system information:
  - Host name
  - OS name and version
  - OS manufacturer
  - System configuration
  - Processor and memory details

## Handling Long Output
- Use `| more` to display long outputs page by page.

Example:
driverquery | more

Navigation:
- Spacebar → next page
- CTRL + C → exit

## Useful Commands
- `help` → shows help for commands
- `cls` → clears the Command Prompt screen

# Network Configuration

## `ipconfig`
Displays the **basic network configuration** of the system.

---

## `ipconfig /all`
Displays **detailed network configuration information**.

---

# Network Troubleshooting

## `ping`
Used to **test connectivity between two hosts**.

### Syntax
`ping target_name`

### How It Works
- Sends **ICMP Echo Request packets**
- Receives **ICMP Echo Reply packets**

### Information Returned
- Packet loss
- Round-trip time
- Minimum, maximum, and average latency

### Example
`ping example.com`

Result:
- 4 packets sent
- 4 received
- 0% packet loss
- Average latency ≈ **78 ms**

---

## `tracert`
Displays the **network path (route)** taken to reach a destination.

### Syntax
`tracert target_name`

### How It Works
- Uses packets with increasing **TTL (Time To Live)**
- Each router that drops a packet reports its address
- Reveals the **sequence of routers (hops)** to the destination

### Example
`tracert example.com`

Result:
- Shows each router hop
- Displays latency for each hop
- Example route reached the destination after **~15 hops**

---

# DNS Querying

## `nslookup`
Queries **DNS servers** to resolve a domain name to its IP address.

### Default DNS Server
`nslookup example.com`

Uses the system's configured DNS server.

### Specific DNS Server
`nslookup example.com 1.1.1.1`

Uses a specific DNS server (Cloudflare in this example).

### Output Includes
- DNS server used
- Domain name
- IPv4 and IPv6 addresses

---

# Network Connections Monitoring

## `netstat`
Displays **active network connections and listening ports**.

### Basic Command
`netstat`

Displays:
- Protocol (TCP/UDP)
- Local address
- Foreign address
- Connection state

### Advanced Netstat Options
- `-a` → Shows all listening ports and connections  
- `-b` → Displays the executable responsible for each connection  
- `-o` → Shows the **Process ID (PID)**  
- `-n` → Displays addresses and ports numerically  

### Combined Command
`netstat -abon`

### Information Revealed
- Listening services
- Associated executable
- Process IDs
- Active connections

### Example Insight
`sshd.exe` listening on **port 22** indicates the system accepts **SSH connections**.

---

# Key Takeaways
Important Windows networking commands:

| Command | Purpose |
|------|------|
| `ipconfig` | View basic network configuration |
| `ipconfig /all` | View detailed network configuration |
| `ping` | Test connectivity to another host |
| `tracert` | Trace the network route to a host |
| `nslookup` | Resolve domain names via DNS |
| `netstat` | View active network connections and ports |

These tools are essential for **network troubleshooting, diagnostics, and system administration**.

# Windows Command Line – Working With Directories and Files

## Working With Directories

### cd
Used to display or change the current directory.

- `cd` → shows the current directory (equivalent to asking *Where am I?*)
- `cd directory_name` → move into a directory
- `cd ..` → move one level up

Example: `cd Users`

---

### dir
Lists the contents of a directory, including files and subdirectories.

Information displayed:
- directory names
- file names
- file sizes
- available disk space

Useful options:
- `dir /a` → display hidden and system files
- `dir /s` → display files in the current directory and all subdirectories

---

### tree
Displays a visual hierarchy of directories and subdirectories.

Example structure:
C:
├── Desktop  
├── Documents  
├── Downloads  
├── Favorites  
├── Links  
├── Music  
├── Pictures  
├── Saved Games  
└── Videos  

---

### mkdir
Creates a new directory.

Example: `mkdir backup_files`

---

### rmdir
Deletes a directory.

Example: `rmdir backup_files`

---

# Working With Files

## type
Displays the contents of a text file directly in the terminal.

Example: `type file.txt`

Best used for small files.

---

## more
Displays long text files page by page.

Navigation:
- Space → next page
- Enter → next line

Useful when file output exceeds the terminal window.

---

## copy
Copies files from one location to another.

Example: `copy test.txt test2.txt`

---

## move
Moves a file to another directory.

Example: `move test2.txt ..`

---

## del / erase
Deletes files.

Example: `erase test2.txt`

---

# Wildcards

## *
The wildcard `*` allows operations on multiple files.

Example: `copy *.md C:\Markdown`

This copies all files with the `.md` extension to the `C:\Markdown` directory.

---

# Key Commands Summary

| Command | Purpose |
|------|------|
| `cd` | Change or display current directory |
| `dir` | List directory contents |
| `tree` | Show directory structure |
| `mkdir` | Create directory |
| `rmdir` | Remove directory |
| `type` | Display file contents |
| `more` | View long text files |
| `copy` | Copy files |
| `move` | Move files |
| `del` / `erase` | Delete files |
| `*` | Wildcard for multiple files |

# Windows Command Line – Managing Processes

## Overview
Windows command line allows users to **view and manage running processes**, similar to the functionality provided by **Task Manager** in the GUI.

---

# Listing Running Processes

## `tasklist`
Displays all currently running processes.

Example: `tasklist`

Typical information shown:
- **Image Name** → Name of the process executable
- **PID (Process ID)** → Unique identifier for the process
- **Session Name**
- **Session Number**
- **Memory Usage**

Because many processes run simultaneously, the output can be **very long**.

---

# Filtering Processes

## `tasklist /FI`
Used to **filter the task list** to find specific processes.

Syntax:
`tasklist /FI "filter"`

Example:
`tasklist /FI "imagename eq sshd.exe"`

Explanation:
- `/FI` → filter option
- `imagename eq sshd.exe` → show only processes with that image name

To view all available filtering options:
`tasklist /?`

---

# Terminating Processes

## `taskkill`
Used to **terminate (kill) a running process**.

Syntax:
`taskkill /PID process_id`

Example:
`taskkill /PID 4567`

Explanation:
- `/PID` specifies the **process ID**
- The command stops the process associated with that PID

---

# Key Commands Summary

| Command | Purpose |
|------|------|
| `tasklist` | Lists all running processes |
| `tasklist /FI "imagename eq process"` | Filters processes by name |
| `taskkill /PID pid_number` | Terminates a process |
| `tasklist /?` | Displays help and filter options |

---

# Key Takeaway
Using the command line, administrators can:
- Monitor running processes
- Search for specific applications
- Terminate problematic or non-responsive processes

These commands provide **Task Manager–like functionality directly in the terminal**.

# Windows Command Line – Managing Processes

## Overview
Windows provides command-line tools to manage running processes, similar to the functionality of **Task Manager**. These tools allow users to list processes, filter them, and terminate them directly from the terminal.

---

## Listing Running Processes

### `tasklist`
The `tasklist` command displays all currently running processes.

Example: `tasklist`

The output typically includes:
- **Image Name** – The executable name of the process
- **PID (Process ID)** – Unique identifier for each process
- **Session Name**
- **Session Number**
- **Memory Usage**

Because many processes run on a system, the list can be quite long.

---

## Filtering Processes

### `tasklist /FI`
Filtering helps locate specific processes within the long task list.

Syntax: `tasklist /FI "filter"`

Example:  
`tasklist /FI "imagename eq sshd.exe"`

Explanation:
- `/FI` → applies a filter
- `"imagename eq sshd.exe"` → shows only processes named **sshd.exe**

This command returns only the matching processes along with their **PIDs**, which are required for managing them.

To see all available filter options:  
`tasklist /?`

---

## Terminating Processes

### `taskkill`
The `taskkill` command is used to stop a running process.

Syntax:  
`taskkill /PID process_id`

Example:  
`taskkill /PID 4567`

Explanation:
- `/PID` specifies the **Process ID**
- The command terminates the process associated with that PID.

---

## Key Commands Summary

| Command | Purpose |
|--------|--------|
| `tasklist` | List all running processes |
| `tasklist /FI "imagename eq process"` | Filter processes by name |
| `taskkill /PID pid_number` | Terminate a process |
| `tasklist /?` | Display help and filter options |
