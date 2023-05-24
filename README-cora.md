# Use Accelerator to create project
#   - Update namespaces to wfd-apps (can use wfd-services, but really don't need this namespace at all)
#   - Choose to dynamically provision each service
#   - Change instance name to wfd-msgbroker, wfd-db, and wfd-cache
#   - Update cluster instance class to rabbitmq-unmanaged, mysql-unmanaged, and redis-unmanaged
#   - Create git repo and check in code
#   - Update URLs in config/develoepr/workloads.yaml
#   - Update $text field in catalog config for search and availability

# For TAP 1.5.0, apply RBAC workaround to iterate and run clusters:
kubectl create clusterrolebinding admin-me --clusterrole=cluster-admin --user=ciberkleid@vmware.com

# If using dynamic provisioning with rabbitmq-unmanaged, mysql-unmanaged, and redis-unmanaged class instance names, then:
#   1. Don't need the service-instance namespace
#   2. can skip apply of config/service-operator/

kubectl apply -f config/app-operator/

kubectl apply -f config/developer/