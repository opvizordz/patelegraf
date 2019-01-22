FROM s390x/alpine:3.8
LABEL "com.example.vendor"="Opvizor, Inc."
LABEL version="1.9.2"
LABEL description="Telegraf Docker image for Performance Analyzer Linux monitoring for s390x architecture"

# Work path
WORKDIR /runtime

# Download Telegraf
ADD https://dl.influxdata.com/telegraf/releases/telegraf-1.9.2_linux_s390x.tar.gz ./

# Copy entrypoint script
COPY ./runtime/start.sh start.sh

# Installing packages & clean up
RUN tar xzf telegraf-1.9.2_linux_s390x.tar.gz -C . && \
        chmod +x telegraf//usr/bin/telegraf && \
        cp telegraf/usr/bin/telegraf /usr/bin/ && \
        rm -rf *.tar.gz* telegraf/

ENTRYPOINT [ "./start.sh" ]
