FROM ubuntu:22.04@sha256:b6b83d3c331794420340093eb706a6f152d9c1fa51b262d9bf34594887c2c7ac

RUN apt-get update && apt-get install -y socat tzdata 
# RUN apt-get install -y openssh-server sudo

RUN ln -sf /usr/share/zoneinfo/Asia/Seoul /etc/localtime
RUN dpkg-reconfigure tzdata

RUN adduser pwn

WORKDIR /home/pwn

COPY ./flag ./flag
COPY ./deploy/prob ./prob

RUN chmod 644 ./flag 
RUN chmod 755 ./prob

USER pwn

EXPOSE 8080
# EXPOSE 22
CMD socat TCP-LISTEN:8080,reuseaddr,fork EXEC:./prob,stderr
