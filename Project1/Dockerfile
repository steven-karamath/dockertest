FROM ubuntu

#set timezone
ENV TZ=America/Toronto
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone

#install required packages
RUN apt-get update && \
apt-get install -yq  net-tools \
			stress \
			iperf \
			snmpd \
			tzdata

#all the scripts and files required for stress tests
COPY stress.sh /opt/stress.sh
COPY cpustress.sh /opt/cpustress.sh
COPY diskusage.sh /opt/diskusage.sh
COPY networkstress.sh /opt/networkstress.sh

#snmp config
COPY snmpd.conf /etc/snmp/snmpd.conf

#expose port 161 for cacti to read
EXPOSE 161

ENTRYPOINT "/opt/stress.sh"
