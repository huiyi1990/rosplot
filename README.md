rosplot
=======

Python tool for plotting arbitrary fields of ROS messages in real time

Usage:

    rostopic echo [topic] | rosplot [x fields] [y fields] [options]

    options:
            
    [number]    -i --update_interval : milliseconds between plot updates
    [number]    -c --point_count : max points to plot in sliding window
    [number]    --size : the size of the points
    [0-255]     -a : alpha, the transparency of the points

    hint: pass multiple y fields separated by commas to plot multiple fields
                
Examples:

    --- gps positions ---
    rostopic echo /android/fix | ./rosplot latitude longitude

![gps screenshot](screenshots/example1-gps.png?raw=true "GPS: Latitude vs Longitude")

    --- simple time series ---
    rostopic echo /android/barometric_pressure | ./rosplot time fluid_pressure

![pressure screenshot](screenshots/example2-pressure.png?raw=true "Barometric Pressure vs Time")

    --- fast update, rolling window ---
    rostopic echo /android/illuminance | ./rosplot time illuminance -i 50 -c 200

![illuminance screenshot](screenshots/example3-illuminance.png?raw=true "Illuminance vs Time")

    --- multiple y fields plotted against one x field ---
    rostopic echo /android/imu | ./rosplot time linear_acceleration.x,linear_acceleration.y,linear_acceleration.z

![3v1 imu screenshot](screenshots/example4-imu.png?raw=true "IMU x,y,z vs Time")

    --- three pairs of fields ---
    rostopic echo /android/imu | ./rosplot linear_acceleration.x,linear_acceleration.z,linear_acceleration.y linear_acceleration.z,linear_acceleration.y,linear_acceleration.x

![paired imu screenshot](screenshots/example5-imu.png?raw=true "IMU x,z,y vs IMU z,y,x")
