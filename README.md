# ReloaderOnOCP_IndividualNamespace
This uses [Reloader](https://github.com/stakater/Reloader) on Openshift to deploy to a specific Namespace. By default, Reloader installs a "clusterRole", this process uses "Role".

Also includes examples
```
.
├── LICENSE
├── README.md
├── ReloaderOCPManifests
│   ├── deployment.yaml
│   ├── roleBinding.yaml
│   ├── role.yml
│   └── serviceaccount.yaml
├── ReloaderUsageExampleUsingAuto
│   ├── deployment.yaml
│   └── secret.yaml
└── ReloaderUsageExampleUsingSecret
    ├── deployment.yaml
    └── secret.yaml
```


## Deployment process
`oc apply --namespace YourNamespace -f openshiftManifests/` - This will create the Service Account, Deployment, Role, RoleBinding AND other things not listed here that the pod will request (such as a Secret creation).

## Example using Reloader in a Deployment
1. `oc apply --namespace YourNamespace -f ReloaderUsageExampleUsingAuto/` - This will rollout for any secret/configMap used in deployment

2. `oc apply --namespace YourNamespace -f ReloaderUsageExampleUsingSecret/` - This will rollout for a specific secret name

## Deletion process
`oc delete --namespace YourNamespace -f openshiftManifests/`