The following PEM configuration is available for testing on the OpenStack platform:
- PEM Server v8
- EPAS 13 client running PEM client and registered with the server


Here are the steps to access the console and the client database:
1.	Log on  to the EDB network (VPN)
2.	Log on to the PEM server console:
https://172.16.208.125:8443/pem

using the following credentials:
```
username = enterprisedb
password = postgres
```


3. The registered EPAS 13 server has same credentials and default specs, i.e.:
```
database = edb
port = 5444
```

![](https://github.com/EnterpriseDB/tech-partner-program/blob/main/Lab%20Environment/images/PEM.png)
