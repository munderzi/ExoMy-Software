# Base image
FROM ros:noetic

ENV TZ=Europe/Zurich
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone

# Basic tools
RUN apt-get update && \
    apt-get install apt-utils nano git wget curl python3-pip net-tools iputils-ping python-is-python3 -y

# Install additional ros packages
RUN apt-get update && apt-get install ros-noetic-joy -y
RUN pip install adafruit-circuitpython-pca9685

# Install packages for camera use
RUN apt-get update && \
    apt-get install ros-noetic-usb-cam -y

# Add ros sourcing to bashrc
RUN echo ". /opt/ros/noetic/setup.bash" >> ~/.bashrc

# Create Ros workspace
ENV EXOMY_WS=/root/exomy_ws
RUN mkdir -p $EXOMY_WS/src

WORKDIR /root

COPY ./entrypoint.sh /
ENTRYPOINT ["/entrypoint.sh"]
