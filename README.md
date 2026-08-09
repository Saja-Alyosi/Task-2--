# 🤖 ROS 2 from Scratch – The Ultimate Guide

> 🚀 A complete, professional summary of ROS 2 fundamentals, installation, and building your first simulated robot.

---

## 📌 Table of Contents

- [What is ROS 2?](#-what-is-ros-2)
- [Installing Ubuntu & ROS 2](#-installing-ubuntu--ros-2)
- [Linux Basics for Beginners](#-linux-basics-for-beginners)
- [ROS 2 Core Concepts](#-ros-2-core-concepts)
- [Creating Your First Node](#-creating-your-first-node)
- [Node Communication (Topics, Services, Actions)](#-node-communication-topics-services-actions)
- [Parameters](#-parameters)
- [Launch Files](#-launch-files)
- [Building a Custom Robot (URDF + TF)](#-building-a-custom-robot-urdf--tf)
- [Simulating in Gazebo](#-simulating-in-gazebo)
- [Command Cheat Sheet](#-command-cheat-sheet)
- [What's Next?](#-whats-next)
- [Additional Resources](#-additional-resources)

---

## 🧠 What is ROS 2?

![ROS Logo](https://upload.wikimedia.org/wikipedia/commons/thumb/b/bb/Ros_logo.svg/1200px-Ros_logo.svg.png)

**ROS 2** (Robot Operating System 2) is an open-source framework for developing robotics applications. It consists of:

| Component | Description |
|-----------|-------------|
| 🧩 **Framework** | A unified software structure for developing Nodes |
| 🛠️ **Tools** | Essential utilities like RViz, Gazebo, and rqt_graph |
| 🔌 **Plugins** | Pre-built packages like Navigation 2 and MoveIt 2 |
| 🌍 **Community** | A vast, active community of developers and researchers |

### ✅ Key Features:
- Supports **Python** & **C++**
- Runs on **Ubuntu**, **Windows**, and **macOS**
- Free and open-source
- Suitable for complex robots and industrial projects

---

## 💻 Installing Ubuntu & ROS 2

### 🔹 System Requirements
- **OS:** Ubuntu 24.04 (Noble Numbat)
- **ROS 2 Distribution:** Jazzy Jalisco (LTS until 2029)

### 🔹 Installation Steps

```bash
# 1. Update system packages
sudo apt update && sudo apt upgrade -y

# 2. Install required tools
sudo apt install software-properties-common curl -y

# 3. Add ROS GPG key
sudo curl -sSL https://raw.githubusercontent.com/ros/rosdistro/master/ros.key -o /usr/share/keyrings/ros-archive-keyring.gpg

# 4. Add ROS repository
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/ros-archive-keyring.gpg] http://packages.ros.org/ros2/ubuntu $(. /etc/os-release && echo $UBUNTU_CODENAME) main" | sudo tee /etc/apt/sources.list.d/ros2.list > /dev/null

# 5. Install ROS 2
sudo apt update
sudo apt install ros-jazzy-desktop -y

# 6. Install development tools
sudo apt install ros-dev-tools -y
