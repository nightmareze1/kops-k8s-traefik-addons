# GRAFANA DEPLOY
k create -f grafana-deployment.yml

k create grafana-service.yml

k create ing-grafana.yml

# FOR PERSISTENT DATA OF THE DASHBOARD USE DE VOLUME EBS OR NETWORKFILESYSTEM EFS.

# ADD PROMETHEUS ENDPOINT AND ecs-prometheus AND ADD PERSONAL DASHBOARDS
