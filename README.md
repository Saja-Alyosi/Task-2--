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

🔹 Environment Setup
bash
# Auto-source ROS on terminal start
echo 'source /opt/ros/jazzy/setup.bash' >> ~/.bashrc
source ~/.bashrc

🐧 Linux Basics for Beginners
Command	Description
ls	List directory contents
cd	Change directory
pwd	Print working directory
mkdir	Create a new directory
touch	Create a new file
rm	Remove a file
rm -rf	Remove a directory recursively
cp	Copy files
mv	Move or rename files
nano	Terminal text editor
sudo	Execute with superuser privileges
📁 Ubuntu File System Structure
Path	Description
/bin, /sbin	System executables
/etc	Configuration files
/home/user	User's personal directory
/opt	ROS installation location
/usr	User programs (similar to Program Files)
/var/log	System logs
/boot	Boot files
🧩 ROS 2 Core Concepts
🔹 Nodes
The fundamental executable unit in ROS 2

Run with ros2 run

Communicate via Topics, Services, and Actions

bash
# Run a turtlesim node
ros2 run turtlesim turtlesim_node
🔹 Topics
Pub/Sub (Publish/Subscribe) communication pattern

Continuous data streams

Identified by name and data type

bash
# Publish to a topic
ros2 topic pub /cmd_vel geometry_msgs/msg/Twist "{linear: {x: 2.0}}"

# Subscribe to a topic
ros2 topic echo /turtle1/pose
🔹 Services
Client/Server communication

Request/Response pattern

Used for quick, synchronous tasks

bash
# Call a service
ros2 service call /spawn turtlesim/srv/Spawn "{x: 2, y: 3, theta: 0.2}"
🔹 Actions
Similar to services, but for long-running tasks

Contains Goal + Result + Feedback

Can be cancelled

bash
# Send an action goal
ros2 action send_goal /turtle1/rotate_absolute turtlesim/action/RotateAbsolute "{theta: 1.5}" --feedback
🛠️ Creating Your First Node
🔹 Setting Up a Workspace
bash
mkdir -p ~/ros2_ws/src
cd ~/ros2_ws
colcon build
source install/setup.bash
🔹 Creating a Python Package
bash
cd ~/ros2_ws/src
ros2 pkg create my_py_pkg --build-type ament_python --dependencies rclpy
🔹 Writing a Minimal Node
python
#!/usr/bin/env python3
import rclpy
from rclpy.node import Node

class MyNode(Node):
    def __init__(self):
        super().__init__("my_node")
        self.get_logger().info("Hello ROS 2!")

def main(args=None):
    rclpy.init(args=args)
    node = MyNode()
    rclpy.spin(node)
    rclpy.shutdown()

if __name__ == "__main__":
    main()
🔹 Building & Running
bash
# Update setup.py with entry point
# Then build and run
colcon build --packages-select my_py_pkg
source install/setup.bash
ros2 run my_py_pkg my_node
🔄 Node Communication
🔹 Publisher & Subscriber
python
# Publisher
self.publisher = self.create_publisher(Int64, "number", 10)
self.timer = self.create_timer(1.0, self.publish_number)

# Subscriber
self.subscriber = self.create_subscription(Int64, "number", self.callback, 10)
🔹 Service
python
# Server
self.service = self.create_service(ResetCounter, "reset_counter", self.callback)

# Client
self.client = self.create_client(ResetCounter, "reset_counter")
request = ResetCounter.Request()
request.reset_value = 10
future = self.client.call_async(request)
🔹 Action
python
# Server
self.action_server = ActionServer(self, CountUntil, "count_until", self.goal_callback, self.execute_callback)

# Client
self.action_client = ActionClient(self, CountUntil, "count_until")
future = self.action_client.send_goal_async(goal)
⚙️ Parameters
python
# Declare parameters
self.declare_parameter("number", 2)
self.declare_parameter("publish_period", 1.0)

# Get values
number = self.get_parameter("number").value
period = self.get_parameter("publish_period").value
bash
# Pass parameters at runtime
ros2 run my_py_pkg number_publisher --ros-args -p number:=5 -p publish_period:=0.5

# Load from YAML file
ros2 run my_py_pkg number_publisher --ros-args --params-file ~/params.yaml
🚀 Launch Files
🔹 XML Example
xml
<launch>
    <node pkg="my_py_pkg" exec="number_publisher" name="pub1">
        <param name="number" value="3" />
        <remap from="/number" to="/my_number" />
    </node>
    <node pkg="my_cpp_pkg" exec="number_counter" />
</launch>
🔹 Python Example
python
from launch import LaunchDescription
from launch_ros.actions import Node

def generate_launch_description():
    return LaunchDescription([
        Node(package="my_py_pkg", executable="number_publisher"),
        Node(package="my_cpp_pkg", executable="number_counter")
    ])
🔹 Running
bash
ros2 launch my_robot_bringup my_robot.launch.xml
🤖 Building a Custom Robot (URDF + TF)
🔹 URDF Structure
xml
<robot name="my_robot">
    <link name="base_link">
        <visual>
            <geometry>
                <box size="0.6 0.4 0.2" />
            </geometry>
            <material name="green">
                <color rgba="0 0.6 0 1" />
            </material>
        </visual>
    </link>
    <joint name="base_to_wheel" type="continuous">
        <parent link="base_link" />
        <child link="wheel_link" />
        <origin xyz="0.2 0.3 0.1" />
        <axis xyz="0 1 0" />
    </joint>
</robot>
🔹 Visualize in RViz
bash
ros2 launch urdf_tutorial display.launch.py model:=/path/to/my_robot.urdf.xacro
🔹 View TF Tree
bash
ros2 run tf2_tools view_frames
🎮 Simulating in Gazebo
🔹 Install Gazebo
bash
sudo apt install ros-jazzy-ros-gz
🔹 Launch Simulation
bash
# Start Gazebo with empty world
ros2 launch ros_gz_sim gz_sim.launch.py gz_args:="empty.sdf -r"

# Spawn robot
ros2 run ros_gz_sim create -topic robot_description
🔹 Add Control Systems
xml
<gazebo>
    <plugin filename="gz-sim-diff-drive-system" name="gz::sim::systems::DiffDrive">
        <left_joint>left_wheel_joint</left_joint>
        <right_joint>right_wheel_joint</right_joint>
        <wheel_separation>0.45</wheel_separation>
        <wheel_radius>0.1</wheel_radius>
    </plugin>
</gazebo>
🔹 Control the Robot
bash
ros2 topic pub /cmd_vel geometry_msgs/msg/Twist "{linear: {x: 0.5}}"
📋 Command Cheat Sheet
Category	Command
Nodes	ros2 node list, ros2 run <pkg> <exec>
Topics	ros2 topic list, ros2 topic echo, ros2 topic pub
Services	ros2 service list, ros2 service call
Actions	ros2 action list, ros2 action send_goal
Parameters	ros2 param list, ros2 param get, ros2 param set
Launch	ros2 launch <pkg> <file>
TF	ros2 run tf2_tools view_frames
Gazebo	gz sim, ros2 launch ros_gz_sim gz_sim.launch.py
Build	colcon build --packages-select <pkg>
Bags	ros2 bag record, ros2 bag play
🧭 What's Next?
Area	Tools & Libraries
Navigation	Navigation 2 (Nav2)
Robotic Arms	MoveIt 2
Hardware Control	ros2_control
Computer Vision	OpenCV, PCL
Simulation	Gazebo, Ignition
Machine Learning	TensorFlow, PyTorch
📚 Additional Resources
Official ROS 2 Documentation

Robotics Backend YouTube Channel

Book GitHub Repository

ROS Discourse Forum

Robotics Stack Exchange
