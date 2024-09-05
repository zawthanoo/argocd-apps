
### Ingress Setup

Install ingress-nginx (https://kubernetes.github.io/ingress-nginx/deploy/)
```
kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/controller-v1.11.2/deploy/static/provider/cloud/deploy.yaml
```

Example Ingress 
```
apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  name: uat-ingress
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
              number: 8080
```


