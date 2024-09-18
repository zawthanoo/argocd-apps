
### argocd application

```yaml
apiVersion: argoproj.io/v1alpha1
kind: Application
metadata:
  name: spring-rest-helloworld
spec:
  destination:
    name: ''
    namespace: uat
    server: 'https://kubernetes.default.svc'
  source:
    repoURL: 'https://github.com/zawthanoo/argocd-apps.git'
    path: spring-rest-helloworld/overlays/uat
    targetRevision: HEAD
  sources: []
  project: default
  syncPolicy:
    syncOptions:
    - PruneLast=true
```
