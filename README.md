# Comman to execute the prometheus in localserver

helm install --values prometheus.yaml  prometheus prometheus-community/prometheus --set alertmanager.enabled=true,kube-state-metrics.enabled=true,prometheus-node-exporter.enabled=true,prometheus-pushgateway.enabled=true  --set server.persistentVolume.enabled=true --set server.persistentVolume.storageClass=local-storage --set server.persistentVolume.existingClaim=prometheus-pvc -n monitoring

#---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

helm upgrade --values grafana-values.yaml grafana grafana/grafana --set persistence.enabled=true,persistence.storageClassName="local-storage",persistence.existingClaim="grafana-pvc" -n monitoring
