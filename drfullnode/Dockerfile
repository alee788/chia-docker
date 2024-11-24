FROM ubuntu:latest

RUN apt-get update && apt-get install -y unminimize && \
    rm -rf /var/lib/apt/lists/*

CMD ["/bin/bash", "-c", "\
    tail -f /dev/null"]