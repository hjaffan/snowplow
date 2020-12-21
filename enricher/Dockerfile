FROM amd64/ubuntu:latest
# Install Java 8
RUN apt-get update -y
RUN apt-get install wget unzip openjdk-8-jre -y
RUN update-alternatives --config java
# Download Kinesis Enricher Jar
RUN wget -O snowplow_stream_enrich_kinesis_0.21.0.zip 'https://bintray.com/snowplow/snowplow-generic/download_file?file_path=snowplow_stream_enrich_kinesis_0.21.0.zip'
# Unzip the Jar
RUN unzip snowplow_stream_enrich_kinesis_0.21.0.zip
# Execute Scala Steam Collector Jar as a process
COPY ./enricher.config.hocon .
COPY ./resolver.json .
COPY ./enrichments enrichments/
ENTRYPOINT java -Dorg.slf4j.simpleLogger.defaultLogLevel=info -jar snowplow-stream-enrich-kinesis-0.21.0.jar --config enricher.config.hocon --resolver file:resolver.json --enrichments file:enrichments
