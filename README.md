Test change 

## Info

Simple sample Konflux Components for testing.

The `main` branch contains Application named `main-app` and Component named `main-component`.

The `monorepo` branch contains another Application named `monorepo` and two Components (`component1` and `component2`) each in own directory.

The `component1-nudging` and `component2-nudged` branches contain Components to test nudging.

## Deployment

```
export NAMESPACE=test
kubectl create namespace $NAMESPACE
kubectl apply -k ./deploy --namespace=$NAMESPACE
```
Alternatively, deploy only one app:
```
kubectl apply -k ./deploy/main-app --namespace=$NAMESPACE
```
or
```
kubectl apply -k ./deploy/monorepo-app --namespace=$NAMESPACE
```
or
```
kubectl apply -k ./deploy/nudge-app --namespace=$NAMESPACE
```
Note, in order for nudging to work, image reference must match.
Which means that it's expected to deploy nudge components into `test` namespace and configured quay org must match.

or
```
kubectl apply -k ./deploy/multi-platform-app --namespace=$NAMESPACE
```

## Descrease resources requirements

To descrease resource requirements of build task and disable checks,
add the following resources override into your pipeline run:
```
spec:
  taskRunSpecs:
  - pipelineTaskName: build-container
    computeResources:
      requests:
        cpu: 250m
        memory: 256Mi
      limits:
        memory: 2Gi
  params:
  - name: skip-checks
    value: 'true'
```
[{"depName": "quay.io/konflux-ci/tekton-catalog/task-apply-tags quay.io/konflux-ci/tekton-catalog/task-apply-tags quay.io/konflux-ci/tekton-catalog/task-build-image-index quay.io/konflux-ci/tekton-catalog/task-build-image-index quay.io/konflux-ci/tekton-catalog/task-buildah-oci-ta quay.io/konflux-ci/tekton-catalog/task-buildah-oci-ta quay.io/konflux-ci/tekton-catalog/task-clair-scan quay.io/konflux-ci/tekton-catalog/task-clair-scan quay.io/konflux-ci/tekton-catalog/task-clamav-scan quay.io/konflux-ci/tekton-catalog/task-clamav-scan quay.io/konflux-ci/tekton-catalog/task-coverity-availability-check quay.io/konflux-ci/tekton-catalog/task-coverity-availability-check quay.io/konflux-ci/tekton-catalog/task-deprecated-image-check quay.io/konflux-ci/tekton-catalog/task-deprecated-image-check quay.io/konflux-ci/tekton-catalog/task-ecosystem-cert-preflight-checks quay.io/konflux-ci/tekton-catalog/task-ecosystem-cert-preflight-checks quay.io/konflux-ci/tekton-catalog/task-git-clone-oci-ta quay.io/konflux-ci/tekton-catalog/task-git-clone-oci-ta quay.io/konflux-ci/tekton-catalog/task-init quay.io/konflux-ci/tekton-catalog/task-init quay.io/konflux-ci/tekton-catalog/task-prefetch-dependencies-oci-ta quay.io/konflux-ci/tekton-catalog/task-prefetch-dependencies-oci-ta quay.io/konflux-ci/tekton-catalog/task-push-dockerfile-oci-ta quay.io/konflux-ci/tekton-catalog/task-push-dockerfile-oci-ta quay.io/konflux-ci/tekton-catalog/task-rpms-signature-scan quay.io/konflux-ci/tekton-catalog/task-rpms-signature-scan quay.io/konflux-ci/tekton-catalog/task-sast-coverity-check-oci-ta quay.io/konflux-ci/tekton-catalog/task-sast-coverity-check-oci-ta quay.io/konflux-ci/tekton-catalog/task-sast-shell-check-oci-ta quay.io/konflux-ci/tekton-catalog/task-sast-shell-check-oci-ta quay.io/konflux-ci/tekton-catalog/task-sast-snyk-check-oci-ta quay.io/konflux-ci/tekton-catalog/task-sast-snyk-check-oci-ta quay.io/konflux-ci/tekton-catalog/task-sast-unicode-check-oci-ta quay.io/konflux-ci/tekton-catalog/task-sast-unicode-check-oci-ta quay.io/konflux-ci/tekton-catalog/task-show-sbom quay.io/konflux-ci/tekton-catalog/task-show-sbom quay.io/konflux-ci/tekton-catalog/task-source-build-oci-ta quay.io/konflux-ci/tekton-catalog/task-source-build-oci-ta", "currentValue": "0.1", "currentDigest": "sha256:4973fa42a8f06238613447fbdb3d0c55eb2d718fd16f2f2591a577c29c1edb17", "newValue": "0.2", "newDigest": "sha256:517a51e260c0b59654a9d7b842e1ab07d76bce15ca7ce9c8fd2489a19be6463d", "packageFile": ".tekton/main-component-push.yaml", "parentDir": ".tekton", "depTypes": ["tekton-bundle"]}]