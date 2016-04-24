FROM alpine

ENV CONSUL_TEMPLATE_VERSION=0.14.0

# Update wget to get support for SSL
RUN apk --update add haproxy wget

# Download consul-template
RUN ( wget --no-check-certificate https://releases.hashicorp.com/consul-template/${CONSUL_TEMPLATE_VERSION}/consul-template_${CONSUL_TEMPLATE_VERSION}_linux_amd64.zip -O /tmp/consul_template.zip && unzip /tmp/consul_template.zip && mv consul-template /usr/bin && rm -rf /tmp/* )

ADD files/start.sh /bin/start.sh
COPY files/haproxy.json /tmp/haproxy.json
COPY files/haproxy.ctmpl /tmp/haproxy.ctmpl

ENTRYPOINT ["/bin/start.sh"]
