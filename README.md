<p align="center">  
   <img src = "source/ub.png" width = 500>
</p >

# <p align="center">Robotics Project</p >

<p align="center">Professor: Ralph SEULIN</p >  
<p align="center">Students: ZHU Chen,GU Heng</p >  

## Contents
1. [Introduction](#introduction)
2. [Move Robot](#Move-Robot)
3. [Mapping and Localization](#Mapping-and-Localization)
4. [Navigation](#Navigation)
5. [Follow waypoints](#Follow-waypoints)
6. [Conclusion](#Conclusion)

## Introduction
## Move robot
## Mapping and Localization
## Navigation
In order to achieve autonomous navigation of the robot, we need to use a navigation stack. The navigation stack is a set of ROS nodes and algorithms that are used to automatically move the robot from one point to another, thereby avoiding all obstacles that the robot may encounter.  

<p align="center">  
   <img src = "source/navigation package.png" width = 800>
</p >  

In order to realize the path planning of the robot, we need to use the 2D Nav target tool of the mobile robot, costmap, and calculate the trajectory. In order to achieve these goals, we need to use the move_base package. The move_base package contains the move_base node.  The move_base node is one of the major elements in the ROS Navigation Stack, since it links all of the elements that take place in the Navigation process. As shown below:  

<p align="center">  
   <img src = "source/move_base.png" width = 400>
</p >  

The move_base node implements SimpleActionServer and receives target information with geometry_msgs/PoseStamped messages. The following table describes the description of some topics subscribed and published by the move_base node.  

<p align="center">  
   <img src = "source/movebase topic.png" width = 900>
</p >   

If we need the robot to avoid obstacles to reach the designated place, we also need to use the following parameters:  
**The Global Planner:** When the move_base node receives a new target, the target will be sent to the global planner immediately. Then, the global planner is responsible for calculating the safe path to reach the target posture. The path is calculated before the robot starts to move, so readings made by the robot's sensors during the movement are not considered. Every time the global planner plans a new path, the path is published to the /plan topic.  

**The Local Planner:** Local planners can instantly recalculate the robot's path to prevent the robot from hitting the object, but still allow it to reach its destination. When the local plan is generated, it will be published to the topic named /local_plan.  

**Global Costmap:** The global cost map is created based on the static map generated by the user. In this case, the initialization cost map provides width, height, and obstacle information.  

**Local Costmap:** The local planner uses the local cost map to calculate the local plan, which is created directly based on the robot's sensor readings.
dwa_local_planner: The DWA local planner provides an implementation of the Dynamic Window Approach algorithm.  













## Follow waypoints
