
### argocd application

```yaml
apiVersion: argoproj.io/v1alpha1
kind: Application
metadata:
  name: springboot-template
spec:
  destination:
    name: ''
    namespace: uat
    server: 'https://kubernetes.default.svc'
  source:
    repoURL: 'https://github.com/zawthanoo/argocd-apps.git'
    path: springboot-template/overlays/uat
    targetRevision: HEAD
  sources: []
  project: default
  syncPolicy:
    automated: 
       prune: true
```


## ingress for all argocd applicaiton
```yaml
apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  name: uat-ingress
  namespace: uat
  annotations:
    nginx.ingress.kubernetes.io/backend-protocol: HTTP
spec:
  ingressClassName: nginx
  rules:
  - http:
      paths:
      - path: /spring-hello
        pathType: Prefix
        backend:
          service:
            name: uat-spring-rest-helloworld
            port:
              number: 8282
      - path: /argocd-mfe-shell
        pathType: Prefix
        backend:
          service:
            name: uat-angular-mfe-shell
            port:
              number: 8282              
```