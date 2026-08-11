# ROS 2 Humble Installation & Setup Guide on WSL2

This repository contains the complete documentation for installing **Ubuntu 22.04 LTS** using **WSL2** on Windows, setting up the **ROS 2 Humble Desktop** environment, as well as verification steps and troubleshooting.

---

## 📋 Environment Details
- **Host OS:** Windows
- **Subsystem:** WSL2 (Windows Subsystem for Linux)
- **Linux Distribution:** Ubuntu 22.04.5 LTS
- **ROS Version:** ROS 2 Humble Hawksbill (Desktop Install)

---

## 🛠️ Installation Steps

### 1. Setting up the Linux Environment (Ubuntu on WSL2)
WSL was enabled and Ubuntu was installed via PowerShell:
```bash
wsl --install -d Ubuntu-22.04
```

### 2. Setting up ROS 2 Repositories and Installing Packages
Inside the Ubuntu terminal, the system was updated and official requirements were installed:
```bash
# Update repositories and add official keys
sudo apt update && sudo apt install curl -y
sudo curl -sSL [https://raw.githubusercontent.com/ros/rosdistro/master/ros.key](https://raw.githubusercontent.com/ros/rosdistro/master/ros.key) -o /usr/share/keyrings/ros-archive-keyring.gpg

# Add ROS 2 repository
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/ros-archive-keyring.gpg] [http://packages.ros.org/ros2/ubuntu](http://packages.ros.org/ros2/ubuntu) $(. /etc/os-release && echo $UBUNTU_CODENAME) main" | sudo tee /etc/apt/sources.list.d/ros2.list > /dev/null

# Install ROS 2 Humble Desktop
sudo apt update
sudo apt install ros-humble-desktop -y
```

### 3. Environment Sourcing
To ensure ROS 2 environment variables are loaded automatically on every new terminal session:
```bash
echo "source /opt/ros/humble/setup.bash" >> ~/.bashrc
source ~/.bashrc
```

---

## ✅ Verification

The environment was successfully verified by executing the following commands inside the Linux environment:

1. Checking the ROS distribution variable:
   ```bash
   echo $ROS_DISTRO
   ```
   **Output:** `humble`

2. Terminal Execution Proof:

![ROS 2 Humble Verification](<img width="1011" height="630" alt="image" src="https://github.com/user-attachments/assets/80b7207e-13fa-4579-ad73-e5f01c63425a" />
)

---

## ⚠️ Troubleshooting

### Issue 1: Running verification commands in PowerShell instead of WSL
- **Cause:** Typing the `echo $ROS_DISTRO` command directly in Windows PowerShell before entering the Linux system, which resulted in no output.
- **Solution:** Switching to the Ubuntu environment first by typing the `wsl` command in PowerShell, or opening a dedicated Ubuntu tab in Windows Terminal.

### Issue 2: `ros2` command not recognized in a new session
- **Cause:** The environment setup file `setup.bash` was not automatically sourced with every new terminal.
- **Solution:** Adding the line `source /opt/ros/humble/setup.bash` to the `~/.bashrc` file so it runs automatically with each new session without needing manual entry.

### Issue 3: Typing Markdown syntax inside the Terminal
- **Cause:** Attempting to write image insertion code `![alt](path)` inside the Bash terminal, causing the error `-bash: ![: event not found`.
- **Solution:** Understanding that Markdown codes are strictly meant to be written inside the `README.md` file and are not executable terminal commands.
