# Router on Linux

## Router Configuration

- configure ip_forward value to 1

    ```bash
    sysctl -w net.ipv4.ip_forward=1
    ```

- check the ip_forward value, the value is 1

    ```bash
    cat /proc/sys/net/ipv4/ip_forward
    ```

- allocate an ip to interfaces

    ```bash
    ip addr add 172.16.10.254/24 dev ens3
    ip addr add 172.16.11.254/24 dev ens4
    ```

- check a routing table

    ```bash
    ip route
    ```

## Node1 Configuration

- allocate an ip to an interface

    ```bash
    ip addr add 172.16.10.11/24 dev ens3
    ```
    
- add a route

    ```bash
    ip route add 0.0.0.0/0 via 172.16.10.254
    ```

## Node2 Configuration

- allocate an ip to an interface

    ```bash
    ip addr add 172.16.11.11/24 dev ens3
    ```
    
- add a route

    ```bash
    ip route add 0.0.0.0/0 via 172.16.11.254
    ```

## Test

- run ping on node1(172.16.10.11)

    ```bash
    ping 172.16.11.11
    ```

## Tip

- if you use this configuration and a bridge(openvswitch etc.) supperted trunk mode, you can use it like a L3 switch supported SVI