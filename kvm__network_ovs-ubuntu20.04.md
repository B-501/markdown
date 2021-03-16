# KVM_Network_Openvswitch-Ubuntu20.04

## Installation

- install kvm

    ```bash
    apt install qemu-kvm libvirt-dev virt-manager
    ```

- install openvswitch

    ```bash
    apt install openvswitch-switch
    ```

- create a ovs-bridge

    ```bash
    ovs-vsctl add-br ovsbr0
    ovs-vsctl add-port ovsbr0 em1
    ovs-vsctl set Interface ovsbr0 mtu_request=9000
    ```

- create a net-define.xml file

    ```bash
    vi ~/ovsbr0.xml
    ```
    
    ```xml
    <network>
        <name>ovsbr0</name>
        <forward mode='bridge'/>
        <bridge name='ovsbr0'/>
        <virtualport type='openvswitch'/>
        <portgroup name='vlan_untagged' default='yes'>
        </portgroup>
        <portgroup name='vlan_10-ipmi'>
            <vlan>
                <tag id='10'/>
            </vlan>
        </portgroup>
        <portgroup name='vlan_11-api'>
            <vlan>
                <tag id='11'/>
            </vlan>
        </portgroup> 
        <portgroup name='vlan_12-overlay'>
            <vlan>
                <tag id='12'/>
            </vlan>
        </portgroup> 
        <portgroup name='vlan_13-octavia'>
            <vlan>
                <tag id='13'/>
            </vlan>
        </portgroup>
        <portgroup name='vlan_14-ceph_public'>
            <vlan>
                <tag id='14'/>
            </vlan>
        </portgroup>
        <portgroup name='vlan_15-ceph_cluster'>
            <vlan>
                <tag id='15'/>
            </vlan>
        </portgroup>
        <portgroup name='vlan_18-kubernetes'>
            <vlan>
                <tag id='18'/>
            </vlan>
        </portgroup>
        <portgroup name='vlan_19-external'>
            <vlan>
                <tag id='19'/>
            </vlan>
        </portgroup>
        <portgroup name='vlan_trunk'>
            <vlan trunk='yes'>
                <tag id='10'/>
                <tag id='11'/>
                <tag id='12'/>
                <tag id='13'/>
                <tag id='14'/>
                <tag id='15'/>
                <tag id='16'/>
                <tag id='17'/>
                <tag id='18'/>
                <tag id='19'/>
            </vlan>
        </portgroup>
    </network>
    ```

- apply net.xml

    ```bash
    virsh net-define ~/ovsbr0.xml
    virsh net-start ovsbr0
    virsh net-autostart ovsbr0
    ```