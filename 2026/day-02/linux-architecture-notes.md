# Linux Architecture, Processes & systemd – Short Notes

## 1. Core Components of Linux

### **Kernel**
- Core of the operating system  
- Manages CPU, memory, storage, network, and hardware  
- Provides system calls for applications  
- Acts as a bridge between hardware and user space  

### **User Space**
- Everything outside the kernel  
- Includes shells (bash, zsh), utilities (ls, cp), and applications  
- Users interact with Linux through user space programs  

### **Init System (systemd)**
- First process started by the kernel (`PID 1`)  
- Starts and stops services  
- Handles system boot and shutdown  
- Manages logs (via `journalctl`)  
- Uses cgroups for resource control  

---

## 2. How Linux Creates & Manages Processes

### **Process Creation**
- Processes are created using:
  - `fork()` → clones the parent process  
  - `exec()` → replaces process memory with a new program  
- Each process has:
  - **PID** – Process ID  
  - **PPID** – Parent Process ID  

### **Common Process States**
- **Running (R)** → Using CPU  
- **Sleeping (S)** → Waiting for an event or I/O  
- **Zombie (Z)** → Process ended but entry still remains  
- **Stopped (T)** → Paused (e.g., Ctrl+Z)  
- **Uninterruptible Sleep (D)** → Waiting for hardware I/O  

### **Process Management**
- CPU scheduler decides which process runs  
- Memory assigned using virtual memory  
- Signals control processes:
  - `SIGTERM` → ask to stop  
  - `SIGKILL` → force kill  
  - `SIGSTOP` → pause  

---

## 3. What systemd Does & Why It Matters

### **Key Features**
- Manages services through "units"  
- Handles dependencies and parallel startup  
- Central logging using `journalctl`  
- Restarts crashed services automatically  
- Controls resources using cgroups  

### **Why It Matters in DevOps**
- Most modern Linux distros use systemd  
- Helps debug failed services quickly  
- Simplifies log collection  
- Improves reliability during incidents  
- Essential for automation and troubleshooting  

---

## 4. Top 5 Daily Linux Commands

- `ps aux` → View running processes  
- `top` / `htop` → Monitor CPU & memory  
- `systemctl status <service>` → Check service health  
- `journalctl -u <service>` → View service logs  
- `kill -9 <pid>` → Force kill a stuck process  

---
