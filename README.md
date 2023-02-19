# **Setup Ubuntu AWS**
Setup + add swap and instal Docker &amp; docker-compose

## _01 - Add Swap:_

- check if your instance already has a swap file or partition:

``` bash
sudo swapon --show
```

- Create 1GB swap file called `/swapfile`. You can adjust the size of the file by changing the number after `-l`.
``` bash
sudo fallocate -l 1G /swapfile
```
``` bash
sudo chmod 600 /swapfile
```
``` bash
sudo mkswap /swapfile
```

- Enable the swap file
``` bash
sudo swapon /swapfile
```

-  Add an entry to the `/etc/fstab` file to ensure that the swap file is automatically enabled after every reboot
``` Bash
/swapfile swap swap defaults 0 0
```
- Verify the swap file
```bash
sudo swapon --show
free -h
```


