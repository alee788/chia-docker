FROM ubuntu:latest

RUN apt-get update && apt-get install -y wget && \
    rm -rf /var/lib/apt/lists/*

RUN wget https://github.com/Chia-Network/drplotter/releases/download/1.0.3/drplotter_1.0.3_amd64.deb

RUN apt-get update && \
    #apt-get install -y vim && \
    apt-get install -y ./drplotter_1.0.3_amd64.deb && \
    rm drplotter_1.0.3_amd64.deb && \
    rm -rf /var/lib/apt/lists/*

#ENV DRSERVER_IP_ADDRESS="192.168.254.45:8080"
#ENV FARMER_IP_ADDRESS="192.168.254.44"
# mount your ssl cert directory to /ca
# mount your root plot folder to /plots

CMD ["/bin/bash", "-c", "\
    drchia init -c /ca && \
    drchia plots add -d /plots && \
    sed -i '/farmer_peers:/!b;n;s/  - host: .*/  - host: '$FARMER_IP_ADDRESS'/' ~/.chia/mainnet/config/config.yaml && \
    sed -i 's/recursive_plot_scan:.*$/recursive_plot_scan: true/' ~/.chia/mainnet/config/config.yaml && \
    drchia start harvester -r && \
    tail -f /dev/null"]