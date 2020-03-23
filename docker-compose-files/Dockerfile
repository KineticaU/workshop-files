#FROM debian:10-slim
#FROM ubuntu:18.04
#FROM debian:9-slim
#FROM debian:8-slim
FROM ubuntu:18.04

RUN rm -rf /var/lib/apt/lists/* \
    && apt-get update --fix-missing -o Acquire::CompressionTypes::Order::=gz \
    && apt upgrade -y \
    && apt autoremove -y  \
    && apt autoclean -y \
    && apt-get install --no-install-recommends -y supervisor openssh-server tzdata nano wget gnupg \
    && apt-get autoclean && apt-get autoremove \
    && ln -sf /usr/share/zoneinfo/Europe/London /etc/localtime \
    && echo "Europe/London" > /etc/timezone

RUN mkdir -p /root/.ssh && \
    chmod 0700 /root/.ssh

COPY supervisord.conf /etc/supervisor/conf.d/supervisord.conf

RUN mkdir /var/run/sshd
RUN echo 'root:root' |chpasswd
RUN sed -ri 's/^#?PermitRootLogin\s+.*/PermitRootLogin yes/' /etc/ssh/sshd_config
RUN sed -ri 's/UsePAM yes/#UsePAM yes/g' /etc/ssh/sshd_config

CMD ["/usr/bin/supervisord","-n", "-c", "/etc/supervisor/conf.d/supervisord.conf"]