# learning-devsecops

```bash
root@ubuntu:~$docker network create --driver=bridge gateway
root@ubuntu:~$docker network inspect gateway
root@ubuntu:~$docker network inspect gateway
[
    {
        "Name": "gateway",
        "Id": "9c5e72964d510547680fa2de3ee18a15c6cf0143cbea08227bd48f2dd9270dcc",
        "Created": "2020-01-21T14:01:43.708044252+07:00",
        "Scope": "local",
        "Driver": "bridge",
        "EnableIPv6": false,
        "IPAM": {
            "Driver": "default",
            "Options": {},
            "Config": [
                {
                    "Subnet": "172.19.0.0/16",
                    "Gateway": "172.19.0.1"
                }
            ]
        },
....
```

Custom vm.max_map_count for issue elastic-search-max-virtual-memory
```bash
    root@ubuntu:~$sysctl -w vm.max_map_count=262144
```