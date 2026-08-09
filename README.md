# 🤖 Comprehensive ROS Guide

---

## 📑 Table of Contents

1. [Introduction to ROS](#introduction-to-ros)
2. [Basic Linux Commands](#basic-linux-commands)
3. [Installing ROS 2 - Humble](#installing-ros-2---humble)
4. [ROS 2 Commands](#ros-2-commands)

## Introduction to ROS

### What is ROS?

**ROS** (Robot Operating System) is an open-source framework designed specifically for robotics applications. It provides comprehensive tools and software packages that simplify the development and operation of complex robotic systems.

### ✨ Key Features:

* ✓ Efficient and reliable communication between robot components
* ✓ Comprehensive libraries for control and sensing
* ✓ 3D simulation using Gazebo
* ✓ Data visualization tools using RViz
* ✓ Supported by a large global community
* ✓ Free and highly customizable

## Basic Linux Commands

These commands are essential before getting started with ROS:

| Command           | Description                                     | Example                             |
| ----------------- | ----------------------------------------------- | ----------------------------------- |
| `ls`              | List the contents of the current directory      | `$ ls -la`                          |
| `cd [path]`       | Navigate to a specific directory                | `$ cd Desktop`                      |
| `pwd`             | Display the current directory path              | `$ pwd`                             |
| `mkdir [name]`    | Create a new directory                          | `$ mkdir robot`                     |
| `sudo`            | Execute a command with administrator privileges | `$ sudo apt-get update`             |
| `apt-get update`  | Update the package list                         | `$ sudo apt-get update`             |
| `apt-get install` | Install a package                               | `$ sudo apt-get install ros-humble` |
| `nano [file]`     | Open a text editor                              | `$ nano setup.bash`                 |
| `source [file]`   | Load environment variables                      | `$ source ~/.bashrc`                |
| `echo`            | Print text or a variable                        | `$ echo $ROS_DISTRO`                |

## Installing ROS 2 - Humble

### ⚠️ Requirements:

* **Operating System:** Ubuntu 22.04 LTS or later
* **Memory:** At least 4 GB
* **Storage:** At least 2–3 GB

### 🔧 Installation Steps:

#### Step 1️⃣: Update the System

```bash
sudo apt update && sudo apt upgrade -y
```

#### Step 2️⃣: Install Required Utilities

```bash
sudo apt install software-properties-common curl -y
```

#### Step 3️⃣: Add the Key

```bash
sudo curl -sSL https://raw.githubusercontent.com/ros/rosdistro/master/ros.key -o /usr/share/keyrings/ros-archive-keyring.gpg
```

#### Step 4️⃣: Add the Repository

```bash
echo "deb [arch=amd64 signed-by=/usr/share/keyrings/ros-archive-keyring.gpg] http://packages.ros.org/ros2/ubuntu jammy main" | sudo tee /etc/apt/sources.list.d/ros2.list > /dev/null
```

#### Step 5️⃣: Update the Packages

```bash
sudo apt update
```

#### Step 6️⃣: Install ROS 2 Humble

```bash
sudo apt install ros-humble-desktop -y
```

#### Step 7️⃣: Set Up the Environment

```bash
echo 'source /opt/ros/humble/setup.bash' >> ~/.bashrc
```

#### Step 8️⃣: Load the Configuration

```bash
source ~/.bashrc
```

#### Step 9️⃣: Verify the Installation

```bash
ros2 --version
```

## ROS 2 Commands

### Basic Commands:

| Command                                 | Description                                 |
| --------------------------------------- | ------------------------------------------- |
| `ros2 node list`                        | Display a list of active nodes              |
| `ros2 topic list`                       | Display a list of available topics          |
| `ros2 service list`                     | Display a list of available services        |
| `ros2 topic echo [topic_name]`          | Display the data being published on a topic |
| `ros2 interface show [msg_type]`        | Display the structure of a message          |
| `ros2 launch [package] [launch_file]`   | Run a launch file                           |
| `ros2 run [package] [executable]`       | Run a node or executable                    |
| `ros2 param list`                       | Display a list of parameters                |
| `ros2 param set [node] [param] [value]` | Set a parameter value                       |
| `ros2 param get [node] [param]`         | Get a parameter value                       |
| `ros2 node info [node_name]`            | Get information about a node                |
| `ros2 topic info [topic_name]`          | Get information about a topic               |
