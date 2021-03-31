# IP Nonlocal Bind

## Configuration

- add a line to sysctl.conf

    ```bash
    vi /etc/sysctl.conf
    ```

    ```bash
    # ...
    
    net.ipv4.ip_nonlocal_bind = 1
    ```

- apply a configuration

  ```bash
  sysctl -p
  ```

- check the ip_nonlocal_bind value, the value is 1

  ```bash
  cat /proc/sys/net/ipv4/ip_nonlocal_bind
  ```

## Tip

- if you use HAproxy and keepavlied, you can run HAproxy service with an ip unallocated to a node