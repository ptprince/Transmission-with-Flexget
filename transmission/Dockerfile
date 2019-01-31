FROM linuxserver/transmission

ADD https://raw.githubusercontent.com/ronggang/transmission-web-control/master/release/install-tr-control.sh /tmp

RUN echo 1 | sh /tmp/install-tr-control.sh && \
    rm /tmp/install-tr-control.sh 

CMD ["/init"]