# OpenVPN-docker-UPatras

OpenVPN client connected to UPatras VPN.

### Instructions

* Download ```UPatras.ovpn``` from [Mussa](https://mussa.upnet.gr/user/index.php?action=downloadVPN) to the ```vpn``` folder.

* Edit line ```auth-user-pass``` in ```UPatras.ovpn``` to ```auth-user-pass /vpn/creds.txt```

* Set your UPatras username and password in ```creds.txt``` as in the example file.

* Run ```docker-compose up -d```

To verify your container is connected to the internet, open a new terminal on the host machine and get your container's public IP:

```
docker exec -it upatras_vpn_container curl ifconfig.me && echo

```