# RAW Image Mount

## Configuration

- if a qcow2 format image, convert to a raw format image

    ```bash
    qemu-img convert -f qcow2 focal-server-cloudimg-amd64.img focal-server-cloudimg-amd64.raw
    ```

- check partitions in the image

    ```bash
    kpartx -v focal-server-cloudimg-amd64.raw
    ```

- attach the image to a loop device using kpartx

    ```bash
    kpartx -v focal-server-cloudimg-amd64.raw -a
    ```

- create a mount point

    ```bash
    mkdir /mnt/loop-dev
    ```

- show a list of the loop device partitions

    ```bash
    losetup -a
    ```

- mount / partiton of the raw image

    ```bash
    mount /dev/mapper/loop0p1 /mnt/loop-dev
    ```
