# Test Multicast with Iperf
## ASM
On receiver:
```
iperf -s -u -B 239.12.34.10%eth1 -i 1
```

On sender:
```
iperf -c 239.12.34.10 -u --ttl 64 -t 60
```

## ASM with Bidir
On receiver:
```
iperf -s -u -B 238.0.0.123%eth1 -i 1
```

On sender:
```
iperf -c 238.0.0.123 -u --ttl 64 -t 60
```

## SSM
On receiver:
```
iperf -s -u -B 232.12.34.30%eth1 -H 10.12.10.40 -i 1
```

On sender:
```
iperf -c 232.12.34.30 -u --ttl 64 -t 60
```