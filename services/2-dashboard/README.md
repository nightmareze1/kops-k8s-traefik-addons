# METRICS
k create -f metrics.yml

# ADMIN
k create -f dashboard-admin.yml

# DASHBOARD dashboard.yml==v1.8.1 or v1.8.3.yaml last version
k create -f v1.8.3.yaml

# CREATE USER WITH SIMPLE AUTH
htpasswd -c ./auth zz1
cat auth
kubectl create secret generic mysecret --from-file auth --namespace=kube-system


# CONFIGURE INGRESS WITH AUTH AND SECRET

vi ing-dashboard.yml

apiVersion: extensions/v1beta1
kind: Ingress
metadata:
  annotations:
    kubernetes.io/ingress.class: traefik
    traefik.frontend.rule.type: PathPrefix
    ingress.kubernetes.io/auth-type: "basic"
    ingress.kubernetes.io/auth-secret: "mysecret"
  generation: 1
  name: kubernetes-dashboard
  namespace: kube-system
spec:
  rules:
  - host: app5.itshellweb.org
    http:
      paths:
      - backend:
          serviceName: kubernetes-dashboard
          servicePort: 443
        path: /

k create -f ing-dashboard.yml
