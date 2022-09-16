# Base image
FROM ros:melodic 

ENV TZ=Europe/Zurich
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone

# Basic tools
RUN apt-get update && \
    apt-get install nano git tmux wget curl python-pip net-tools iputils-ping -y

# Install additional ros packages
RUN apt-get update && apt-get install ros-melodic-joy -y
RUN pip install adafruit-pca9685

# Install packages for camera use
RUN apt-get update && \
    apt-get install ros-melodic-usb-cam -y

# Add ros sourcing to bashrc
RUN echo ". /opt/ros/melodic/setup.bash" >> ~/.bashrc

# Create Ros workspace
ENV EXOMY_WS=/root/exomy_ws
RUN mkdir -p $EXOMY_WS/src

WORKDIR /root

COPY ./entrypoint.sh /
ENTRYPOINT ["/entrypoint.sh"]
