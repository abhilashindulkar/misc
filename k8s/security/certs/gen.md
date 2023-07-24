# Generate Key, Certs.

1. Certificate Authority Key
```
openssl genrsa -out ca.key 2048
```
2. Certificate Signing Request 
```
openssl req -new -key ca.key -subj "/CN=KUBERNETES-CA" -out=ca.csr
```
3. Sign Certificate & generate Publica CA Certificate
```
openssl x509 -req -in ca.csr -signkey ca.key -out ca.crt
```

---

1. Generate API Server Certificate Key
```
openssl genrsa -out apiserver.key 2048
```
2. API Server CSR.
``` 
openssl req -new -key apiserver.key  -subj "/CN=kube-apiserver/O=system:kube-apiserver" -out apiserver.csr -config openssl.cnf
```
3. Sign, generate API Server Certificate with CA Certificate
```
openssl x509 -req -in apiserver.csr -CA ca.crt -CAkey ca.key -out apiserver.crt
```

---

1. Generate Client Certificate Key
```
openssl genrsa -out admin.key 2048
```
2. Client CSR.
``` 
openssl req -new -key admin.key  -subj "/CN=kube-admin/O=system:masters" -out admin.csr
```
3. Sign, generate Client Certificate with CA Certificate
```
openssl x509 -req -in admin.csr -CA ca.crt -CAkey ca.key -out admin.crt
```
---

#### Example to connect to K8s - Rest API Call

```
curl https://kube-apiserver:6443/api/v1/pods --key admin.key --cert admin.crt --cacert ca.crt
```

#### View Certificate details

```
# apiserver kubernetes manifest /etc/kubernetes/manifests/apiserver.yaml
openssl x509 -in /etc/kubernetes/pki/apiserver.crt -text -noout
```
