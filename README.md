# manifests

This is, ideally, a gitops manifest repo for [gitops-actions-application](https://github.com/cringdahl/gitops-actions-application). PRs in that repo will trigger image builds, which in turn will trigger PRs to this repo's `kustomize\overlay\dev` directory. This manifest PR will contain the in-progress image tag created in the application PR's Action.

Once the application repo's PR is closed (with or without merge), the manifest PR will also close. On an app PR merge, the manifest PR will also merge. If the app PR is not merged, the manifest PR will also not merge.

The idea here is that the app repo triggers all action on this repository. No manual Actions runs should be necessary in a working environment.

Currently, the only work being done is in the Github Actions and container creation space. No guarantees made that the actual manifest will actually work.

# notes
Currently, applicationset.yaml is being `kubectl apply`d manually.

`ingress\spec\rules\host` should be adjusted based on the IP of the cluster it lands in.

may need to rework how image tags get updated

repos are generic secrets with special labels! this needs to be automated when we get to handling secret data

