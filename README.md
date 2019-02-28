### Comcast
---
https://github.com/tylertreat/Comcast

```
go get github.com/tylertreat/comcast
comcast --device-eth0 --latency=250 --target-bw=1000 --default-bw=100000 --packet-loss=10%--target-addr=8.8.8.8,10.0.0.0/24 --target-proto=tcp,udp,icmp --target-port=80,22,1000:2000
comcast --device=eht0 --latency=250 --target-bw=1000 --packet-loss=10%
comcast --stop

iptables -A INPUT -m statistic --mode random --probability 0.1 -j DROP
iptables -A OUTPUT -m statistic --mode random --probability 0.1 -j DROP

tc qdisc add dev eth0 root netem delay 50ms 20ms distribution normal
tc qdist change dev eth0 root netem recorder 0.02 duplicate 0.05 corrupt 0.01
tc qdisc del dev eth0 root netem

ipfw add 1 pipe 1 ip from me to any
ipfw add 2 pipe 1 ipfrom any to me
ipfw pipe 1 config delay 500ms bw 1Mbit/s plr 0.1
ipfw delete 1
```

```
```

```
```


