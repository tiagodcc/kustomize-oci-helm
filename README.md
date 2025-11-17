# 37638

Reproduction for [Renovate Discussion #37638](https://github.com/renovatebot/renovate/discussions/37638)

## Current behavior

Renovate does not create a PR to update the helm chart version from the original OCI registry when a registry alias is used. It fails to modify the kustomization.yaml file with the following logs:

```
 INFO: Cannot find replaceString in current file content. Was it already updated? (repository=tiagodcc/kustomize-oci-helm, packageFile=kustomization.yaml, branch=renovate/redis-23.x)
       "depName": "redis",
       "existingContent": "helmCharts:\n  - name: redis\n    version: 23.0.10\n    repo: oci://docker.registry.example.com/bitnamicharts\n",
       "replaceString": "docker.registry.example.com/bitnamicharts/redis:23.0.10"
DEBUG: No content changed (repository=tiagodcc/kustomize-oci-helm, packageFile=kustomization.yaml, branch=renovate/redis-23.x)
       "depName": "redis"
```

## Expected behavior

Renovate creates a PR to update the helm chart version from the original OCI registry.

```
helmCharts:
  - name: redis
    version: 23.2.12
    repo: oci://docker.registry.example.com/bitnamicharts
```

## Link to the Renovate issue or Discussion

https://github.com/renovatebot/renovate/pull/39346

https://github.com/renovatebot/renovate/discussions/37638
