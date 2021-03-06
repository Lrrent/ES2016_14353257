##ROS安装
-----------
###一.ROS简介
 ROS是开源的，是用于机器人的一种后操作系统，或者说次级操作系统。它提供类似操作系统所提供的功能，包含硬件抽象描述、底层驱动程序管理、共用功能       的执行、程序间的消息传递、程序发行包管理，它也提供一些工具程序和库用于获取、建立、编写和运行多机整合的程序。
###二. 安装过程
2. 添加sources.list
   配置电脑使其能够安装来自 packages.ros.org的软件包。 ROS Jade 仅 支持Trusty (14.04)、Utopic (14.10) 和 Vivid (15.04)。
   本机为14.04版本
   
   ```
   sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'
```
3. 添加keys

    ```
    sudo apt-key adv --keyserver hkp://pool.sks-keyservers.net --recv-key 0xB01FA116
    ```
    
4. 安装

* 首先，确保Debian软件包索引是最新的
  ```
  sudo apt-get update
  ```
  
* 本机使用ubuntu14.04，安装桌面完整版：包含ROS、rqt、rviz、通用机器人函数库、2D/3D仿真器、导航以及2D/3D感知功能。 
   ```
   sudo apt-get install ros-jade-desktop-full
   ```
5. 初始化rosdep
   在开始使用ROS之前还需要初始化rosdep。  rosdep可以方便在需要编译某些源码的时候为其安装一些系统依赖，同时也是某些ROS核心功能组件所必需用到的工具。 
   ```
   sudo rosdep init
   rosdep update
   
   ```
6. 环境配置
   如果每次打开一个新的终端时ROS环境变量都能够自动配置好（即添加到bash会话中），那将会方便很多： 
   ```
   echo "source /opt/ros/jade/setup.bash" >> ~/.bashrc
source ~/.bashrc

   ```
7. 安装rosinstall
    rosinstall 是ROS中一个独立分开的常用命令行工具，它可以方便让你通过一条命令就可以给某个ROS软件包下载很多源码树。 
 要在ubuntu上安装这个工具，运行以下指令
 ```
 sudo apt-get install python-rosinstall
 
 ```
 截至这步,ROS就算安装完了,下面我们来测试一下安装是否成功
###三.安装结果测试
测试教程[点击这里](http://www.th7.cn/system/lin/201504/103167.shtml)

1. 安装完后打开终端,输入以下指令
   ```
   roscore
   ```
2. 再开一个终端,输入下面的命令```rosrun turtlesim turtlesim_node```,打开一个有小乌龟的界面,如下图：
![turtle](https://github.com/Lrrent/ES2016_14353257/blob/master/ROS/test_turtlesim.png)

3. 另外打开一个终端,输入指令```rosrun turtlesim turtle_teleop_key```，这样就可以使用上下左右来控制乌龟走动了,之后会出现类似下面的界面:<br>
![turtle](https://github.com/Lrrent/ES2016_14353257/blob/master/ROS/test_success.png)

4. 然后再打开第四个终端,输入指令```rosrun rqt_graph rqt_graph```,可以看到ROS nodes以及Topic等图形展示
![turtle](https://github.com/Lrrent/ES2016_14353257/blob/master/ROS/turtle_graph.png)

5.  当你的乌龟可以控制跑动时,说明你安装成功了。
