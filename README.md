# Testkube GKE GitHub Action

GitHub action to run Testkube commands on a GKE cluster equipped with Testkube

## Inputs

| Name | Type | Description | Default Value |
| ---- | ---- | ----------- | ------------- |
| gke-sa-key | Required | GKE Service Account Key | "" |
| gke-project-id | Required | GKE project ID | "" |
| gke-cluster-name | Required | GKE cluster name | "" |
| gke-zone | Required | GKE cluster zone | "" |
| command | Required | Testkube Command | "get" |
| resource | Optional | Testkube Resource | "tests" |
| namespace | Optional | Testkube Namespace | "testkube" |
| api-key | Optional | API key | "" |
| api-uri | Optional | API URI | "" |
| parameters | Optional | Parameters | "" |
| stdin | Optional | Standard input | "" |

## Underlying actions

This GitHub action is a composite action. To see details on the different used actions, check their docs:

* [google-github-actions/setup-gcloud](https://github.com/google-github-actions/setup-gcloud)
* [google-github-actions/get-gke-credentials](https://github.com/google-github-actions/get-gke-credentials)
* [kubeshop/testkube-docker-action](https://github.com/kubeshop/testkube-docker-action)

## Example usage

```sh
      - name: Run Testkube test
        uses: kubeshop/testkube-gke-action@v1
        with:
          gke-sa-key: ${{ secrets.GKE_SA_KEY }}
          gke-project-id: ${{ secrets.GKE_PROJECT }}
          gke-cluster-name: ${{ secrets.GKE_CLUSTER_NAME_DEV }}
          gke-zone: ${{ secrets.GKE_ZONE_DEV }}
          command: 'run'
          resource: 'test'
          namespace: 'testkube'
          parameters: 'successful-soapui-test'
```
