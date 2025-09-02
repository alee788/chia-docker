# chia-docker

 #drplotter
```
container_name="unruffled_morse" && while true; do docker exec -it $container_name /bin/bash -c "tail -F ~/.chia/mainnet/log/debug.log | grep -v 'Processing\|process_batch\|_plot_refresh_callback\|Failed\|File\|ValueError\|^$'" | while IFS= read -r line; do echo "$line"; if echo "$line" | grep -q "is still banned, not connecting to it"; then echo "RESTARTING CONTAINER"; docker restart $container_name; break; fi; done; sleep 5; done
```

#gigahorse
```
./chia-gigahorse-farmer/chia.bin start farmer
```
```
watch -n 300 "./chia-gigahorse-farmer/chia.bin show -s && ./chia-gigahorse-farmer/chia.bin farm summary"
```
