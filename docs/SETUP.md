My hardware:

```
1. A spare laptop that is plugged in 24/7.
2. An ethernet cable connecting my laptop to my router. (recommended over using Wi-Fi)
3. A personal computer to manage the Nextcloud dashboard.
4. 1TB HDD.
```

Operating system, files, and software:

```
1. Ubuntu server (with encryption enabled)
2. Docker
3. Nextcloud
4. Systemd
5. Vlock (optional)
```

QoL configurations:

Since I am using a laptop, I disabled lid-switch actions using ```sudo nano /etc/systemd/logind.conf``` and setting ```HandleLidSwitch=ignore``` before uncommenting it. Afterwards I used ```sudo systemctl mask sleep.target suspend.target hibernate.target hybrid-sleep.target``` to prevent Ubuntu from entering power-saving modes completely, and restarted the power service by using ```sudo systemctl restart systemd-logind```

Mounting the drive:

I first ran ```sudo mkdir -p /mnt/cloud-storage```, identified my HDD by using ```lsblk``` and mounted it using ```sudo mount /dev/yourstoragedrive /mnt/cloud-storage```. I also configured ```/etc/fstab``` to mount my drive automatically upon boot.

Docker:

I installed docker using ```sudo apt update && sudo apt install -y docker.io docker-compose-v2``` and created a directory to work within ```mkdir -p ~/homelab/nextcloud```, afterwards I configured ```docker-compose.yml``` and launched it using ```docker compose up -d```. You can find the configuration I used under the docker directory in this repository.

Physical security:

First, I disabled ctrl+alt+delete interrupts using ```sudo systemctl mask ctrl-alt-del.target``` and ```sudo systemctl daemon-reload``` afterwards. And I also installed vlock to lock my terminal screen using ```sudo apt install -y vlock```.

PC syncing:

After confirming that the service works by visiting the Nextcloud dashboard, I installed the Nextcloud Desktop Client on my personal computer so I could sync it with my server and automatically save my files in my cloud. The desktop client application is very intuitive with its UI so I will not  be going over it.

Nextcloud Dashboard:

I did minimal configurations to the dashboard, it has a very intuitive set up making it very easy to understand even if it's your first time seeing it.
