FROM ubuntu:latest

RUN apt-get update && apt-get install -y wget && \
    rm -rf /var/lib/apt/lists/*

RUN wget https://github.com/Chia-Network/drplotter/releases/download/1.0.3/drplotter_1.0.3_amd64.deb

RUN apt-get update && \
    #apt-get install -y vim && \
    apt-get install -y ./drplotter_1.0.3_amd64.deb && \
    rm drplotter_1.0.3_amd64.deb && \
    rm -rf /var/lib/apt/lists/*

CMD ["/bin/bash", "-c", "\
    drserver && \
    tail -f /dev/null"]