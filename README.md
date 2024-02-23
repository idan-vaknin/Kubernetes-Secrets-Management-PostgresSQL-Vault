# Kubernetes-Secrets-Management-PostgresSQL-Vault
 Implementation of PostgreSQL-Vault scheme on Kind Kubernetes.

Command to run the project:

kind create cluster

incase of issues make sure ro run:
jq --version and helm version to verify that jk and helm are installed succesfully

On Path /terasky-demo/demo3/vault-agent-demo:
Run:
./setup.sh

Run:
kubectl get pods -n vault

kubectl get pods -n postgres

# App won't have pods running into the examples are started
kubectl get pods -n app

Move to the following path examples/injector/dynamic-secrets:
cd examples/injector/dynamic-secrets

RUN:
./run.sh

Run Observe no secrets/sidecars on the app pod::
kubectl describe pod <name of pod> -n app

kubectl exec -ti <name of app pod> -n app -c app -- ls /vault/secrets

Patch the app:as
./patch.sh

Observe the secrets at:
kubectl describe pod <name of pod> -n app

kubectl exec -ti <name of app pod> -n app -c app -- ls /vault/secrets

Port forward and open the webpage:

kubectl port-forward <name of app pod> -n app 8080:8080

open http://127.0.0.1:8080
