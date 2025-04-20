FROM python:3.9-bullseye

# Install Java(PySpark requirements) and related packages
RUN apt-get update && \
    apt-get install -y --no-install-recommends \
    openjdk-11-jdk \
    sudo \
    && rm -rf /var/lib/apt/lists/*

# Setting environment variables
ENV JAVA_HOME=/usr/lib/jvm/java-11-openjdk-amd64
ENV PATH=$PATH:$JAVA_HOME/bin

# Install PySpark and related packages
RUN pip install --no-cache-dir pyspark pandas numpy matplotlib findspark

# Add user
ARG USERNAME=vscode
ARG USER_UID=1000
ARG USER_GID=1000
RUN groupadd --gid $USER_GID $USERNAME \
    && useradd -s /bin/bash --uid $USER_UID --gid $USER_GID -m $USERNAME