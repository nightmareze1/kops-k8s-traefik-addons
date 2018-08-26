# LAUNCHING PROMETHEUS: CONFIG MAP, I NEED CONFIGURE MY TRAEFIK ENDPOINT
k create -f config-map.yaml

k create -f clusterRole.yaml

# DEPLOY PROMETHEUS
k create -f prometheus-deployment.yaml

k create -f prometheus-service.yaml

# CONFIGURE INGRESS

k craete -f ing-prometheus.yml

