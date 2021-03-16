# MAAS

## Installation

- switch a user to root user

    ```bash
    sudo su -
    ```

- stop a swap function

    ```bash
    swapoff -a
    ```

- change a hostname

    ```bash
    vi /etc/hostname
    ```

    ```bash
    maas
    ```

- generate a ssh key

    ```bash
    ssh-keygen
    ```

- copy a public key for login to the deployed server

    ```bash
    cat ~/.ssh/id_rsa.pub
    ```

- add a repository

    ```bash
    apt-add-repository -yu ppa:maas/2.9
    ```

- install maas

    ```bash
    apt install maas
    ```

- initialize maas

    ```bash
    maas init region+rack --database-uri maas-test-db:///
    ```

- create an admin user

    ```bash
    maas createadmin --username=admin --email=admin@admin.com
    ```



## Troubleshooting

### restarting loop maas-rackd service by IPv6

- look up IPs that have mngtmpaddr, noprefixroute tag

  ```bash
  5: vlan19@enp1s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default qlen 1000
      link/ether 52:54:00:19:0a:b7 brd ff:ff:ff:ff:ff:ff
      inet 192.168.111.7/16 brd 192.168.255.255 scope global vlan19
         valid_lft forever preferred_lft forever
      inet6 fda3:d48c:33c5::712/128 scope global dadfailed tentative noprefixroute
         valid_lft forever preferred_lft forever
      inet6 fd0c:b572:ca6c:0:5054:ff:fe19:ab7/64 scope global mngtmpaddr noprefixroute
         valid_lft forever preferred_lft forever
      inet6 fda3:d48c:33c5:0:5054:ff:fe19:ab7/64 scope global mngtmpaddr noprefixroute
         valid_lft forever preferred_lft forever
      inet6 fe80::5054:ff:fe19:ab7/64 scope link
         valid_lft forever preferred_lft forever
  ```

- remove IPs that have mngtmpaddr, noprefixroute tag

  ```bash
  ip address del fda3:d48c:33c5::712/128 dev vlan19
  ip address del fd0c:b572:ca6c:0:5054:ff:fe19:ab7/64 dev vlan19
  ip address del fda3:d48c:33c5:0:5054:ff:fe19:ab7/64 dev vlan19
  ```



## Etc.

#### cloud-init disable

- disable cloud-init after deploy

  ```bash
  touch /etc/cloud/cloud-init.disabled
  ```

