# moveit_benchmark_tutorial
This tutorial follows the [moveit benchmark tutorial](http://docs.ros.org/indigo/api/moveit_tutorials/html/doc/benchmarking_tutorial.html)  
However, there are some problems using the moveit tutorial in my project.

My system setup:  
-OS: Ubuntu 14.04  
-ROS: Indigo  
-Robot: fetch  

Package Required:  
-[Moveit!](https://github.com/ros-planning/moveit)  
-[fetch_ros](https://github.com/fetchrobotics/fetch_ros)  
-[warehouse_ros](https://github.com/ros-planning/warehouse_ros)  

### Three steps to carry out the benchmark:  

#### cfg and launch file
one demo cfg and launch files are attached here.  

#### run the benchmark
```
roslaunch moveit_ros_benchmarks fetch_benchmark.launch
```  
This step will generate a log file in the output path set in the cfg file.  

#### generate a PDF of the plot  
cd to the folder containing moveit_benchmark_statistics.py  
```
python moveit_benchmark_statistics.py /home/shengjian/benchmark.log.1.log -p benchmark.pdf
```
This step will generate a PDF of the benchmark result in the working dir.  
  
### Using constraing  
I follow the advise [here](https://groups.google.com/forum/#!topic/moveit-users/G-YTRJmHcXc)  
The constraints have to be set programmatically into the database.  
Here is a way to set the default constraint, for fetch, it is wirst_rolling_link upright.  
```
roslaunch fetch_moveit_config default_warehouse_db.launch reset:=true
```
Then we can benchmark the planner with constraint
