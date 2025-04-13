FROM python:3.9-bullseye

# Javaのインストール（PySparkの要件）
RUN apt-get update && \
    apt-get install -y --no-install-recommends \
    openjdk-11-jdk \
    && rm -rf /var/lib/apt/lists/*

# 環境変数の設定
ENV JAVA_HOME=/usr/lib/jvm/java-11-openjdk-amd64
ENV PATH=$PATH:$JAVA_HOME/bin

# PySparkとその依存関係のインストール
RUN pip install --no-cache-dir pyspark pandas numpy matplotlib

# findsparkのインストール
RUN pip install --no-cache-dir findspark

# ユーザ追加
RUN mkdir -p /home/pyspark
RUN chmod 777 -R /home/pyspark
RUN groupadd pyspark
RUN useradd -s /bin/bash pyspark -g pyspark
