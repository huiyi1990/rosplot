rosplot
=======

Python tool for plotting arbitrary fields of ROS messages in real time

Usage:

    rostopic echo [topic] | rosplot [x fields] [y fields] [options]"

    options:
            
    [number]    -i --update_interval : milliseconds between plot updates
    [number]    -c --point_count : max points to plot in sliding window
    [number]    --size : the size of the points
    [0-255]     -a : alpha, the transparency of the points

    hint: pass multiple y fields separated by commas to plot multiple fields
                
Examples:

    --- gps positions ---
    rostopic echo /android/fix | ./rosplot latitude longitude

    --- simple time series ---
    rostopic echo /android/barometric_pressure | ./rosplot time fluid_pressure

    --- fast update, rolling window ---
    rostopic echo /android/illuminance | ./rosplot time illuminance -i 50 -c 200

    --- multiple y fields plotted against one x field ---
    rostopic echo /android/imu | ./rosplot time linear_acceleration.x,linear_acceleration.y,linear_acceleration.z

    --- three pairs of fields ---
    rostopic echo /android/imu | ./rosplot linear_acceleration.x,linear_acceleration.z,linear_acceleration.y linear_acceleration.z,linear_acceleration.y,linear_acceleration.x
