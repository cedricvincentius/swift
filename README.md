apiVersion: cert-manager.io/v1
kind: ClusterIssuer
metadata:
  name: letsencrypt-cloudflare
spec:
  acme:
    email: your@email.com
    server: https://acme-v02.api.letsencrypt.org/directory
    privateKeySecretRef:
      name: letsencrypt-cloudflare-key
    solvers:
    - dns01:
        cloudflare:
          email: your@email.com
          apiTokenSecretRef:
            name: cloudflare-api-token
            key: api-token

microk8s kubectl create ingress my-ingress \
    --annotation cert-manager.io/issuer=letsencrypt \
    --rule 'my-service.example.com/*=my-service:80,tls=my-service-tls'

    Y2ZxVRMSsdOU6EI7X2UP8zIn1Xaaqc1MC-p4blVi

    kubectl create secret generic cloudflare-api-token \
  --from-literal=api-token='Y2ZxVRMSsdOU6EI7X2UP8zIn1Xaaqc1MC-p4blVi' \
  --namespace=default
  

docker run cloudflare/cloudflared:latest tunnel --no-autoupdate run --token eyJhIjoiY2MyYWRlZDExNTc2MGE4OTYyMzI4MmQ2ZGExNWQ3MGEiLCJ0IjoiNDIxNWFjZjYtZDE3MC00MjIzLWIyN2YtYTdhNmNjMzViOGNjIiwicyI6IlpqQmtZMkZtTlRjdE9EazBaaTAwWWpVMExXSTBZbVF0WkRoaU9ERmtZVFV3TnpGaSJ9
