# fio Disk Benchmark

## Options

- --direct: no ram cache
- --rw: read/write type
- --bs: block size, file size
- --size: total file size per 1 job(thread)
- --numjobs: simultaneous read/write files
- --iodepth: queue depth



## Commands

- Bandwidth test, Sequence read/write test

    ```bash
    fio --directory=/tmp --name fio_test_file --direct=1 --rw=write --bs=16M --size=1G --numjobs=1 --time_based --runtime=60 --group_reporting --norandommap --iodepth 1

    fio --directory=/tmp --name fio_test_file --direct=1 --rw=write --bs=16M --size=1G --numjobs=1 --time_based --runtime=60 --group_reporting --norandommap --iodepth 1
    ```


- 4k random read/write test

    ```bash
    fio --directory=/tmp --name fio_test_file --direct=1 --rw=randwrite --bs=4K --size=1G --numjobs=16 --time_based --runtime=60 --group_reporting --norandommap --iodepth 32

    fio --directory=/tmp --name fio_test_file --direct=1 --rw=randread --bs=4K --size=1G --numjobs=16 --time_based --runtime=60 --group_reporting --norandommap --iodepth 32
    ```

- 64k random read/write test

    ```bash
    fio --directory=/tmp --name fio_test_file --direct=1 --group_reporting --norandommap --rw=randwrite --bs=64K --size=1G --numjobs=1 --iodepth 32

    fio --directory=/tmp --name fio_test_file --direct=1 --group_reporting --norandommap --rw=randread --bs=64K --size=1G --numjobs=1 --iodepth 32
    ```

- 128k rand read/write test

    ```bash
    fio --directory=/tmp --name fio_test_file --direct=1 --group_reporting --norandommap --rw=randwrite --bs=128K --size=1G --numjobs=1 --iodepth 32

    fio --directory=/tmp --name fio_test_file --direct=1 --group_reporting --norandommap --rw=randread --bs=128K --size=1G --numjobs=1 --iodepth 32
    ```
