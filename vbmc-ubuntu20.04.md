# VBMC-Ubuntu20.04

## Installation

- install qemu-kvm

    ```bash
    apt install qemu-kvm libvirt-dev virt-manager
    ```

- install python3

    ```bash
    apt install python3-pip python3-venv python3-dev pkg-config
    ```

- create a venv

    ```bash
    python3 -m venv /opt/vbmc
    ```

- activate a venv

    ```bash
    source /opt/vbmc/bin/activate
    ```

- install pip

    ```bash
    pip install wheel libvirt-python virtualbmc
    ```

- start vbmcd

    ```bash
    vbmcd
    ```

- list vbmc domain

    ```bash
    vbmc list
    ```

## Troubleshooting

- vbmc still running error

    ```bash
    rm /root/.vbmc/master.pid
    ```