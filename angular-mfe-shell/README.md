
### argocd application

```yaml
apiVersion: argoproj.io/v1alpha1
kind: Application
metadata:
  name: angular-mfe-shell
spec:
  destination:
    name: ''
    namespace: uat
    server: 'https://kubernetes.default.svc'
  source:
    repoURL: 'https://github.com/zawthanoo/argocd-apps.git'
    path: angular-mfe-shell/overlays/uat
    targetRevision: HEAD
  sources: []
  project: default
  syncPolicy:
    automated: 
       prune: true
```