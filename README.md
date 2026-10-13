kubectl apply -f k8s/namespace.yaml

kubectl -n notes create secret generic app-secrets --from-env-file=.env

kubectl apply -R -f .

kubectl get secret app-secrets -n notes -o jsonpath='{.data}'

kubectl rollout restart statefulset postgres -n notes

kubectl delete statefulset postgres -n notes 

kubectl port-forward svc/api 8080:8080 -n notes
