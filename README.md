# complex-kubernetes

command to create secret
psnehi@Prashants-Air complex_kubernetes % kubectl create secret generic pgpassword --from-literal PGPASSWORD=postgrespassword
secret/pgpassword created
psnehi@Prashants-Air complex_kubernetes % kubectl get secrets


To create and start dashboard
=> kubectl apply -f https://raw.githubusercontent.com/kubernetes/dashboard/v2.5.0/aio/deploy/recommended.yaml
=> kubectl proxy

Url: http://localhost:8001/api/v1/namespaces/kubernetes-dashboard/services/https:kubernetes-dashboard:/proxy/

To generate token for dashboard
=> kubectl version
=> kubectl -n kubernetes-dashboard create token admin-user

If your Kubernetes server version is v1.24 or higher you must run the following command:
kubectl -n kubernetes-dashboard create token admin-user

If your Kubernetes server version is older than v1.24 you must run the following command:
kubectl -n kubernetes-dashboard get secret $(kubectl -n kubernetes-dashboard get sa/admin-user -o jsonpath="{.secrets[0].name}") -o go-template="{{.data.token | base64decode}}"

