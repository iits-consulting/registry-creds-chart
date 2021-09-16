## Usage

```shell
    helm repo add registry-creds-chart https://iits-consulting.github.io/registry-creds-chart/
    helm search repo registry-creds
    helm install registry-creds registry-creds-chart/registry-creds --set dockerConfigJsonBase64Encoded="eyJhdXRo...REPLACE_ME"
```