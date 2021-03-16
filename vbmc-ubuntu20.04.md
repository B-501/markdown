# VBMC-Ubuntu20.04

## Installation

- install qemu-kvm

    ```
    apt install qemu-kvm libvirt-dev virt-manager
    ```

- install python3

    ```
    apt install python3-pip python3-venv python3-dev pkg-config
    ```

- create a venv

    ```
    python3 -m venv /opt/vbmc
    ```

- activate a venv

    ```
    source /opt/vbmc/bin/activate
    ```

- install pip

    ```
    pip install wheel libvirt-python virtualbmc
    ```

- start vbmcd

    ```
    vbmcd
    ```

- list vbmc domain

    ```
    vbmc list
    ```

## Troubleshooting

- vbmc still running error

    ```
    rm /root/.vbmc/master.pid
    ```