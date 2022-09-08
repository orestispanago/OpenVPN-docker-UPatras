# OpenVPN-docker-UPatras

OpenVPN client connected to UPatras VPN.

### Instructions

* Download ```UPatras.ovpn``` from [Mussa](https://mussa.upnet.gr/user/index.php?action=downloadVPN)

* Edit line ```auth-user-pass``` in ```UPatras.ovpn``` to ```auth-user-pass /etc/openvpn/creds.txt```

* Set your UPatras username and password in ```creds.txt``` as in the example file.

* Build the docker image:

```
docker build . -t vpn_image
```

* Run the container:

```
docker run -it --cap-add=NET_ADMIN --device /dev/net/tun --dns 150.140.129.30 --name openvpn_container vpn_image openvpn /etc/openvpn/UPatras.ovpn
```

If everything works as expected you should see ```Initialization Sequence Completed``` in your terminal.

To verify your container is connected to the internet, open a new terminal on the host machine and get your container's public IP:

```
docker exec -it openvpn_container curl ipinfo.io/ip && echo
```

Stop and remove one-liner may come in handy:

```
docker stop openvpn_container && docker rm openvpn_container
```