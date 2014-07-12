rosplot
=======

Python tool for plotting arbitrary fields of ROS messages fast and in real time

Usage:

rostopic echo {topic} | rosplot {x field} {y field}

Examples:

rostopic echo /android/barometric_pressure | ./rosplot time fluid_pressure

rostopic echo /android/fix | ./rosplot latitude longitude

rostopic echo /android/imu | ./rosplot time linear_acceleration.z
