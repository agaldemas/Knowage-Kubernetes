# Knowage-Kubernetes

## Requirements

You must provide two secrets for Knowage, one for the DB and one for Knowage itself. You could use either a YAML descriptor like:

```yaml
apiVersion: v1
kind: Secret
metadata:
  name: knowage-db-secret
  namespace: knowage
type: Opaque
data:
  db-user: a25vd2FnZQ==
  db-pass: a25vd2FnZQ==
  db-root-pass: eW91J3JlIGEgbGVnZW5kYXJ5IGhhY2tlcg==
  db-db: a25vd2FnZQ==
---
apiVersion: v1
kind: Secret
metadata:
  name: knowage-secret
  namespace: knowage
type: Opaque
data:
  hmac: Nk1kYzRmMjhpV1lQWDd6OWp5NVpyVFFvcTNidU52
  password-encryption-secret: eEI2a00yRG9VSlBWd05kYkt1NzM5NFRBR2FYODVMSA==
```

Or you could use `kubectl`:

```
kubectl create secret generic knowage-db-secret --namespace knowage \
	--from-literal="db-user=knowage" \
	--from-literal="db-pass=knowage" \
	--from-literal="db-root-pass=Uber-S3cur3-r00+-pASsw0rD" \
	--from-literal="db-db=knowage"

kubectl create secret generic knowage-secret --namespace knowage \
	--from-literal="hmac=bH2a7BWp4NvFx5cJSKqm8RE6nge9YZ3A" \
	--from-literal="password-encryption-secret=t683459SdLsf2m7bgBjQervAGX"
```

## Installation

You should have to apply all the descriptors in this project using:

```
kubectl apply -f .
```
