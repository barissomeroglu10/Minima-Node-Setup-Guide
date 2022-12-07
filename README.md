# Minima-Node-Setup-Guide
You will learn setup a Minima Node

+ MINIMUM SYSTEM REQUIREMENTS

CPU: 1 CPU

RAM: 1 GB

SSD: -

++ Create minima user

sudo adduser minima

+++ Authorizing the User

sudo usermod -aG sudo minima

++++ Switch to Minima user

su - minima

+++++ Docker installation

sudo curl -fsSL https://get.docker.com/ -o get-docker.sh
sudo chmod +x ./get-docker.sh && ./get-docker.sh
sudo usermod -aG docker $USER
exit
su - minima

++++++ Node Initialization

docker run -d -e minima_mdspassword=123 -e minima_server=true -v ~/minimadocker9001:/home/minima/data -p 9001-9004:9001-9004 --restart unless-stopped --name minima9001 minimaglobal/minima:latest

+++++++ We are starting a Docker server

sudo systemctl enable docker.service
sudo systemctl enable containerd.service

++++++++ Auto Update command

docker run -d --restart unless-stopped --name watchtower -e WATCHTOWER_CLEANUP=true -e WATCHTOWER_TIMEOUT=60s -v /var/run/docker.sock:/var/run/docker.sock containrrr/watchtower

+++++++++ Entry to the Minima terminal

docker exec -it minima9001 minima

++++++++++ Account Linking

incentivecash uid:XXXX-XXXX
