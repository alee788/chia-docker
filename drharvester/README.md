# run from directory with this Dockerfile
```
docker build -t drharvester:latest .
```
-DRSERVER_IP_ADDRESS is your drserver

-FARMER_IP_ADDRESS is your full node

-CA is cert Folder from Full Node

-Mount root PLOT folder to /plots in container
```
sudo docker run --env=DRSERVER_IP_ADDRESS=i.p.add.ress:8080 --env=FARMER_IP_ADDRESS=i.p.add.ress --volume=./ca:/ca --volume=/media/drplotter:/plots --restart=unless-stopped -d drharvester:latest
```
#watchdog - restart on harvester ban -  run in TMUX
```
container_name="unruffled_morse" && while true; do docker exec -it $container_name /bin/bash -c "tail -F ~/.chia/mainnet/log/debug.log | grep -v 'Processing\|process_batch\|_plot_refresh_callback\|Failed\|File\|ValueError\|^$'" | while IFS= read -r line; do echo "$line"; if echo "$line" | grep -q "is still banned, not connecting to it"; then echo "RESTARTING CONTAINER"; docker restart $container_name; break; fi; done; sleep 5; done
```
