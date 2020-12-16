FROM amd64/ubuntu:latest
# Install Java 8
RUN apt-get update -y
RUN apt-get install wget unzip openjdk-8-jre -y
RUN update-alternatives --config java
# Download Scala Stream Collector Jar
RUN wget https://bintray.com/snowplow/snowplow-generic/download_file?file_path=snowplow_scala_stream_collector_kinesis_0.16.0.zip
# Unzip the Jar
RUN unzip snowplow_scala_stream_collector_kinesis_0.16.0.zip
# Execute Scala Steam Collector Jar as a process
COPY ./collector.config.hocon .
ENTRYPOINT java -jar snowplow-stream-collector-kinesis-0.16.0.jar --config collector.config.hocon & disown
