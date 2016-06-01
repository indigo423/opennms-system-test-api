FROM stests/base
MAINTAINER jesse@opennms.org

ADD /rpms/*.rpm /
# Does minion really need postgresql-server?
RUN yum install -y /*.rpm && \
	rm -rf /*.rpm && \
	yum -y clean all

COPY etc     /opt/minion/etc
COPY scripts /opt/minion/bin

# Ports
# 162   - SNMP traps
# 1299  - RMI Registry
# 1514  - Syslog
# 8201  - Karaf SSH
# 45444 - RMI Server
EXPOSE 162/udp 1299 1514/udp 5150 8201 45444

WORKDIR /opt/minion
ENV JAVA_HOME /usr/lib/jvm/java-1.8.0-openjdk
CMD ["/opt/minion/bin/bootstrap.sh"]