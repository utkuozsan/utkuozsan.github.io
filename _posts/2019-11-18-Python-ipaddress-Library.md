
# 1. Address


```python
import ipaddress

```


```python
ADDRESSES =  ['192.168.1.1', '8.8.8.8', '145.6.7.178', 'fdfd:87b5:b475:5e3e:b1bc:e121:a8eb:14aa']
```


```python
for ip in ADDRESSES:
    addr = ipaddress.ip_address(ip)
    print('{!r}'.format(addr))
    print(addr)
    print(f'IP Verison: {addr.version}')
    print(f'is private: {addr.is_private}')
    print(f'Integer: {int(addr)}')
    print()
```

    IPv4Address('192.168.1.1')
    192.168.1.1
    IP Verison: 4
    is private: True
    Integer: 3232235777
    
    IPv4Address('8.8.8.8')
    8.8.8.8
    IP Verison: 4
    is private: False
    Integer: 134744072
    
    IPv4Address('145.6.7.178')
    145.6.7.178
    IP Verison: 4
    is private: False
    Integer: 2433091506
    
    IPv6Address('fdfd:87b5:b475:5e3e:b1bc:e121:a8eb:14aa')
    fdfd:87b5:b475:5e3e:b1bc:e121:a8eb:14aa
    IP Verison: 6
    is private: True
    Integer: 337611086560236126439725644408160982186
    
    

#  2. Networks

It should be only network address with a subnetmask or prefix-length.



```python
NETWORKS = ['10.67.100.0/255.255.255.0', '8.8.8.0/24', 'fdfd:87b5:b475:5e3e::/64']
```


```python
for n in NETWORKS:
    net = ipaddress.ip_network(n)
    print('{!r}'.format(net))
    print(net)
    print(f'is private: {net.is_private}')
    print(f'broadcast: {net.broadcast_address}')
    print(f'compressed: {net.compressed}')
    print(f'with netmask: {net.with_netmask}')
    print(f'with hostmask: {net.with_hostmask}')
    print(f'number of addreses: {net.num_addresses}')
    print()
```

    10.67.100.0/24
    is private: True
    broadcast: 10.67.100.255
    compressed: 10.67.100.0/24
    with netmask: 10.67.100.0/255.255.255.0
    with hostmask: 10.67.100.0/0.0.0.255
    number of addreses: 256
    
    8.8.8.0/24
    is private: False
    broadcast: 8.8.8.255
    compressed: 8.8.8.0/24
    with netmask: 8.8.8.0/255.255.255.0
    with hostmask: 8.8.8.0/0.0.0.255
    number of addreses: 256
    
    fdfd:87b5:b475:5e3e::/64
    is private: True
    broadcast: fdfd:87b5:b475:5e3e:ffff:ffff:ffff:ffff
    compressed: fdfd:87b5:b475:5e3e::/64
    with netmask: fdfd:87b5:b475:5e3e::/ffff:ffff:ffff:ffff::
    with hostmask: fdfd:87b5:b475:5e3e::/::ffff:ffff:ffff:ffff
    number of addreses: 18446744073709551616
    
    

A network instance is iterable, and yields the addresses on the network.


```python
NETWORKS = ['10.0.0.0/30', '192.168.100.0/29']
```


```python
for n in NETWORKS:
    net = ipaddress.ip_network(n)
    print('{!r}'.format(net))
    for host in net:
        print(host)
    print()
```

    IPv4Network('10.0.0.0/30')
    10.0.0.0
    10.0.0.1
    10.0.0.2
    10.0.0.3
    
    IPv4Network('192.168.100.0/29')
    192.168.100.0
    192.168.100.1
    192.168.100.2
    192.168.100.3
    192.168.100.4
    192.168.100.5
    192.168.100.6
    192.168.100.7
    
    

 The base address of the network and the broadcast address are both included. To find the addresses that can be used by regular hosts on the network, use the hosts() method, which produces a generator.


```python
NETWORKS = ['10.0.0.0/30', '192.168.100.0/29']

for n in NETWORKS:
    net = ipaddress.ip_network(n)
    print('{!r}'.format(net))
    for host in net.hosts():
        print(host)
    print()
```

    IPv4Network('10.0.0.0/30')
    10.0.0.1
    10.0.0.2
    
    IPv4Network('192.168.100.0/29')
    192.168.100.1
    192.168.100.2
    192.168.100.3
    192.168.100.4
    192.168.100.5
    192.168.100.6
    
    


```python
NETWORKS = [ipaddress.ip_network(net) for net in ['10.0.0.0/30', '192.168.100.0/29']]

ADDRESSES = [ipaddress.ip_address(addr) for addr in ['10.0.0.2', '10.0.0.5', '192.168.100.5', '192.168.100.10']]

for ip in ADDRESSES:
    for net in NETWORKS:
        if ip in net:
            print(f'{ip} is in subnet {net}')
        else:
            print(f'{ip} is not in subnet {net}')
```

    10.0.0.2 is in subnet 10.0.0.0/30
    10.0.0.2 is not in subnet 192.168.100.0/29
    10.0.0.5 is not in subnet 10.0.0.0/30
    10.0.0.5 is not in subnet 192.168.100.0/29
    192.168.100.5 is not in subnet 10.0.0.0/30
    192.168.100.5 is in subnet 192.168.100.0/29
    192.168.100.10 is not in subnet 10.0.0.0/30
    192.168.100.10 is not in subnet 192.168.100.0/29
    

# 3. Interface

A network interface represents a specific address on a network and can be represented by a host address and a network prefix or netmask.


```python
ADDRESSES =  ['192.168.1.1/27', '8.8.8.8/32', '145.6.7.178/29', 'fdfd:87b5:b475:5e3e:b1bc:e121:a8eb:14aa/64']

for ip in ADDRESSES:
    iface = ipaddress.ip_interface(ip)
    print('{!r}'.format(iface))
    print(f'network:\n {iface.network}')
    print(f'ip:\n {iface.ip}')
    print(f'IP with prefixlen:\n {iface.with_prefixlen}')
    print(f'netmask:\n {iface.with_netmask}')
    print(f'hostmask:\n {iface.with_hostmask}')
    print()
```

    IPv4Interface('192.168.1.1/27')
    network:
     192.168.1.0/27
    ip:
     192.168.1.1
    IP with prefixlen:
     192.168.1.1/27
    netmask:
     192.168.1.1/255.255.255.224
    hostmask:
     192.168.1.1/0.0.0.31
    
    IPv4Interface('8.8.8.8/32')
    network:
     8.8.8.8/32
    ip:
     8.8.8.8
    IP with prefixlen:
     8.8.8.8/32
    netmask:
     8.8.8.8/255.255.255.255
    hostmask:
     8.8.8.8/0.0.0.0
    
    IPv4Interface('145.6.7.178/29')
    network:
     145.6.7.176/29
    ip:
     145.6.7.178
    IP with prefixlen:
     145.6.7.178/29
    netmask:
     145.6.7.178/255.255.255.248
    hostmask:
     145.6.7.178/0.0.0.7
    
    IPv6Interface('fdfd:87b5:b475:5e3e:b1bc:e121:a8eb:14aa/64')
    network:
     fdfd:87b5:b475:5e3e::/64
    ip:
     fdfd:87b5:b475:5e3e:b1bc:e121:a8eb:14aa
    IP with prefixlen:
     fdfd:87b5:b475:5e3e:b1bc:e121:a8eb:14aa/64
    netmask:
     fdfd:87b5:b475:5e3e:b1bc:e121:a8eb:14aa/ffff:ffff:ffff:ffff::
    hostmask:
     fdfd:87b5:b475:5e3e:b1bc:e121:a8eb:14aa/::ffff:ffff:ffff:ffff
    
    

# 4. Extra Notes 


```python
attack_ip_addresses = ['85.4.5.6', '172.32.4.90', '100.1.1.1', '8.1.1.2', '20.5.1.2', '30.30.5.5', '192.168.0.1', '10.1.1.1']
new = [x for x in attack_ip_addresses if ipaddress.ip_address(x).is_global and ipaddress.ip_address(x).version == 4]

print (new)
```

    ['85.4.5.6', '172.32.4.90', '100.1.1.1', '8.1.1.2', '20.5.1.2', '30.30.5.5']
    


```python
ip = ipaddress.ip_address('fe80::3')
```


```python
print(ip.version)
print(ip.is_private)
print(ip.is_link_local)
```

    6
    True
    True
    


```python
subnet_of_IP = list(ipaddress.ip_network('192.0.2.0/28').subnets(new_prefix=30))
print(subnet_of_IP)
print(subnet_of_IP[0].compressed)
print(type(subnet_of_IP[0].compressed))
```

    [IPv4Network('192.0.2.0/30'), IPv4Network('192.0.2.4/30'), IPv4Network('192.0.2.8/30'), IPv4Network('192.0.2.12/30')]
    192.0.2.0/30
    <class 'str'>
    


```python
for host in subnet_of_IP[0]:
    print(host)
```

    192.0.2.0
    192.0.2.1
    192.0.2.2
    192.0.2.3
    


```python
subnet_of_IP[0]
```




    IPv4Network('192.0.2.0/30')
# Reference
https://pymotw.com/3/ipaddress/
https://dbader.org/blog/python-ipaddress-module


