# ArgoCD

### Create argocd

```bash
kubectl apply -f app-off-app.yaml
```

### Create Creds

```bash
ssh-keygn -t ed25519 -C "argocd-bot"
```

- open file .pub and copy to ssh in github
- create file argocd-repo-creds.yaml this example

```bash
## file argocd-repo-creds.yaml
apiVersion: v1
kind: Secret
metadata:
  name: argoproj-ssh-creds
  namespace: argocd
  labels:
    argocd.argoproj.io/secret-type: repo-creds
stringData:
  url: git@github.com:argoproj-labs
  type: helm
  sshPrivateKey: |
    -----BEGIN OPENSSH PRIVATE KEY-----
    ...
    -----END OPENSSH PRIVATE KEY-----
```

- copy private key to this

```bash
kubectl apply -f argocd-repo-creds.yaml
```
