FROM osrf/ros:jazzy-desktop-full

# Update and upgrade packages
RUN apt-get update && apt-get upgrade -y

# Install python3-pip
RUN apt-get install -y python3-pip

# Installations for workspace manipulation
RUN apt-get install python3-vcstool python3-colcon-common-extensions git wget -y

# SSH client allows git management from inside container
RUN apt-get install openssh-client -y

# Ease of use utilities
RUN apt-get install -y nano bash-completion

# Gazebo Installation
RUN apt-get install -y \
    gazebo11 \
    ros-jazzy-gazebo-ros-pkgs \
    ros-jazzy-gazebo-ros-control \
    ros-jazzy-gazebo-msgs \
    ros-jazzy-tf2-geometry-msgs

# Setup ROS 2 environment
RUN echo 'source /opt/ros/jazzy/setup.bash' >> /root/.bashrc
RUN echo 'alias s="source install/local_setup.bash"' >> /root/.bashrc
RUN echo 'alias c="colcon build --symlink-install --cmake-args=-DCMAKE_BUILD_TYPE=Release"' >> /root/.bashrc
RUN echo 'PYTHONWARNINGS="ignore:easy_install command is deprecated,ignore:setup.py install is deprecated"; export PYTHONWARNINGS' >> /root/.bashrc

# Select which Turtlebot to spawn
ENV TURTLEBOT3_MODEL 'burger'

# Force color prompt for sudo user
RUN sed -i -e 's/#force_color_prompt=yes/force_color_prompt=yes/g' /root/.bashrc

# Set default shell
ENV SHELL /bin/bash

# Default command
CMD ["/bin/bash"]
