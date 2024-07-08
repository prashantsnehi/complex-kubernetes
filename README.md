# complex-kubernetes

command to create secret
psnehi@Prashants-Air complex_kubernetes % kubectl create secret generic pgpassword --from-literal PGPASSWORD=postgrespassword
secret/pgpassword created
psnehi@Prashants-Air complex_kubernetes % kubectl get secrets
