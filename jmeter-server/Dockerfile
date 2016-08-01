# Use Ubuntu
FROM ubuntu
MAINTAINER TestAutomationGuru

# Install wger & JRE
RUN apt-get clean && \
	apt-get update && \
	apt-get -qy install \
				wget \
				default-jre-headless \
				telnet \
				iputils-ping

# Install jmeter
RUN   mkdir /jmeter \
      && cd /jmeter/ \
      && wget https://archive.apache.org/dist/jmeter/binaries/apache-jmeter-2.13.tgz \
      && tar -xzf apache-jmeter-2.13.tgz \
      && rm apache-jmeter-2.13.tgz

# Set Jmeter Home
ENV JMETER_HOME /jmeter/apache-jmeter-2.13/

# Add Jmeter to the Path
ENV PATH $JMETER_HOME/bin:$PATH

# Ports to be exposed from the container for JMeter Slaves/Server
EXPOSE 1099 50000

# Application to run on starting the container
ENTRYPOINT $JMETER_HOME/bin/jmeter-server \
                        -Dserver.rmi.localport=50000 \
                        -Dserver_port=1099