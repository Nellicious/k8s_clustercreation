Generating private key for John (john.key)
```
$ openssl genrsa -out john.key 2048
```

Generating certificate signing request (john.csr)
```
$ openssl req -new -key john.key -out john.csr -subj "/CN=john/O=finance"
```

Copy kubernetes ca certificate and key from the master node kmaster
>If you used my vagrant provisioning scripts, the root password for all the nodes is "kubeadmin"
```
$ scp root@kmaster:/etc/kubernetes/pki/ca.{crt,key} .
```

Sign the certificate using certificate authority

$ openssl x509 -req -in john.csr -CA /etc/kubernetes/pki/ca.crt -CAkey /etc/kubernetes/pki/ca.key -CAcreateserial -out john.crt -days 365
```

```
openssl x509 -req -in john.csr -CA ca.crt -CAkey ca.key -CAcreateserial -out john.crt -days 365

```
