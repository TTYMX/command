docker rmi -f $(docker images | grep "none" | awk {'print $3'})
docker rm $(docker ps -f "status=exited" -aq)


docker images
docker ps a
docker run hello-world
docker rm $(docker ps -aq)

sudo docker run -d --name test2 busybox /bin/sh -c "while true; do sleep 3600; done"
docker exec -it test2

telnet 127.0.0.1 80

sudo ip netns ls
sudo ip netns add test1
sudo ip netns add test2

sudo ip link

sudo ip netns exec test1 ip link
sudo ip netns exec test1 ip link set dev lo up

sudo ip link add veth-test1 type veth peer name veth veth-test2

sudo ip link set veth-test1 netns test1
sudo ip link set veth-test2 netns test2

sudo ip netns exec test1 ip addr 192.168.10.1/24 dev veth-test1
sudo ip netns exec test2 ip addr 192.168.10.2/24 dev veth-test2

sudo ip netns exec test1 ip link set veth-test1 up
sduo ip netns exec test2 ip link set veth-test2 up


sudo ip netns exec test1 ping 192.168.10.2


sudo docker network ls
sudo docker network inspect bridge
brctl show
apt-get install brctl-utils





sudo docker rm $(docker ps -f "status=exited" -aq)
sudo docker run -d --name test2 --link test1 busybox /bin/sh -c "while true; do sleep 3600; done"
