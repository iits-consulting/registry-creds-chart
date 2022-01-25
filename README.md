This project is based on https://github.com/alexellis/registry-creds

## Usage

Create dockerconfigjson

```shell
kubectl create secret docker-registry regcred --docker-server=https://index.docker.io/v1/ --docker-username=victor.getz@iits-consulting.de --docker-password=my-password --docker-email=victor.getz@iits-consulting.de --dry-run=client -o yaml
```

Output looks like this then

```yaml
apiVersion: v1
data:
  .dockerconfigjson: eyJhdXRocyI6eyJodHRwczovL2luZGV4LmRvY2tlci5pby92MS8iOnsidXNlcm5hbWUiOiJ2aWN0b3IuZ2V0ekBpaXRzLWNvbnN1bHRpbmcuZGUiLCJwYXNzd29yZCI6Im15LXBhc3N3b3JkIiwiZW1haWwiOiJ2aWN0b3IuZ2V0ekBpaXRzLWNvbnN1bHRpbmcuZGUiLCJhdXRoIjoiZG1samRHOXlMbWRsZEhwQWFXbDBjeTFqYjI1emRXeDBhVzVuTG1SbE9tMTVMWEJoYzNOM2IzSmsifX19
kind: Secret
metadata:
  creationTimestamp: null
  name: regcred
type: kubernetes.io/dockerconfigjson
```
Copy dockerconfigjson and perform this commands

```shell
helm repo add registry-creds-chart https://iits-consulting.github.io/registry-creds-chart/
helm search repo registry-creds
helm install registry-creds registry-creds-chart/registry-creds --set defaultClusterPullSecret.dockerConfigJsonBase64Encoded="eyJhdXRocyI6eyJodHRwczovL2luZGV4LmRvY2tlci5pby92MS8iOnsidXNlcm5hbWUiOiJ2aWN0b3IuZ2V0ekBpaXRzLWNvbnN1bHRpbmcuZGUiLCJwYXNzd29yZCI6Im15LXBhc3N3b3JkIiwiZW1haWwiOiJ2aWN0b3IuZ2V0ekBpaXRzLWNvbnN1bHRpbmcuZGUiLCJhdXRoIjoiZG1samRHOXlMbWRsZEhwQWFXbDBjeTFqYjI1emRXeDBhVzVuTG1SbE9tMTVMWEJoYzNOM2IzSmsifX19"
```
