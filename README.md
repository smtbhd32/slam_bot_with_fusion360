# SLAM Bot With Fusion360

This project demonstrates the development of a SLAM (Simultaneous Localization and Mapping) bot using ROS and Gazebo. The process involves creating a robot model in Fusion 360, exporting it to URDF, adding functionality with Gazebo plugins, and implementing SLAM for robot localization and map creation. The entire project is based on the [SLAM Robot Simulation playlist](https://www.youtube.com/watch?v=cQh0gNfb6ro&list=PLXM8kq-f3YucvPdqchLU22WfUfjKCIqlO&ab_channel=JerinPeter) by Jerin Peter.

## Watch Demo

You can watch the demonstration on YouTube by clicking the video below:

<p align="center">
  <a href="https://youtu.be/1A1sOTqlxNs" target="_blank">
    <img src="https://github.com/smtbhd32/slam_bot_with_fusion360/raw/main/video%20thumbnail.png" alt="Watch the video" width="80%" height="auto" />
  </a>
</p>


## Features
- **3D Design**: The robot model was created using Fusion 360 and exported to URDF.
- **Gazebo Integration**: The robot is simulated in Gazebo with LIDAR and differential drive functionality.
- **Custom Environment**: A custom Gazebo world was created to test the robot.
- **SLAM Implementation**: Used the [slam_gmapping](https://github.com/ros-perception/slam_gmapping) package for robot localization and map creation.
- **Teleoperation**: The robot can be manually controlled using the `teleop_twist_keyboard` package during simulation.
- **Visualization**: The robot and SLAM process can be visualized using RQT and RViz.

## Project Steps
1. **Create the Robot Model**: Design the robot in Fusion 360, including adding joints, and export it to URDF using the `fusion2urdf` tool.
   
   ![Screenshot 2024-12-09 001758](https://github.com/user-attachments/assets/d631e91e-2da0-4205-8904-06279217ca4a)

3. **Test the Robot in Gazebo**: Import the URDF model into Gazebo and add LIDAR and differential drive functionality through plugins.
   
   ![Screenshot 2024-12-08 222045](https://github.com/user-attachments/assets/22e8e54c-ecf8-4762-a287-adf614353673)

5. **Create a Gazebo World**: Build a custom Gazebo world for the robot and modify the launch file to load it.
   
   ![Screenshot 2024-12-08 233748](https://github.com/user-attachments/assets/db809819-5b22-4005-af2f-2a2a1c512cd4)

7. **Implement SLAM**: Use the `slam_gmapping` package for robot localization and map creation.
   
   ![Screenshot 2024-12-09 063508](https://github.com/user-attachments/assets/ccf7a287-50c0-468b-bb4b-47f9092ec526)

9. **Save the Map**: Save the generated map after running the SLAM process.
    
   ![Screenshot 2024-12-09 002645](https://github.com/user-attachments/assets/06b777b1-6304-459e-9275-830089f47fc5)

11. **Control the Robot**: Use the `teleop_twist_keyboard` package to manually control the robot during the simulation.

## Commands
1. **Gazebo Launch (Simulate the Robot)**:
   ```bash
   roslaunch myrobot_description gazebo.launch
   ```

2. **RViz Launch (Visualize the Robot)**:
   ```bash
   roslaunch myrobot_description display.launch
   ```

3. **GMAPPING Launch (Start SLAM for Localization and Map Creation)**:
   ```bash
   roslaunch myrobot_description mapping.launch
   ```

4. **Teleoperation (Control the Robot Using the Keyboard)**:
   ```bash
   rosrun teleop_twist_keyboard teleop_twist_keyboard.py
   ```
5. **Saving the map**:
   ```bash
   rosrun map_server map_saver -f myworld_map
   ```

## Issues Faced
- **Python Compatibility**: The script for exporting Fusion 360 models to URDF used `distutils.dir_util`, which is deprecated in Python 3.10 and above. This caused issues since Fusion 360 uses Python 3.12. I resolved this by replacing `distutils` with `shutil` for directory operations, ensuring compatibility with Python 3.12.
- **Gazebo Plugin Configuration**: I encountered difficulties when setting up the Gazebo plugins for LIDAR and differential drive functionality, requiring multiple adjustments to the configuration files.
- **Updated Fusion2URDF Plugin**: I forked and updated the [Fusion2URDF plugin](https://github.com/smtbhd32/fusion2urdf) to ensure compatibility with newer Python versions.

## Acknowledgments
A huge thank you to **Jerin Peter** for his insightful and detailed tutorials. His work served as the foundation for this project and provided the necessary knowledge to successfully develop and simulate the SLAM bot.
