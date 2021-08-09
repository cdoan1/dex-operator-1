# dex-operator

This is a operator-sdk based operator to deploy and manage Dex.

# Usage

## Using the bundle

You'll need operator-sdk 1.9.0+.

```bash
git clone https://github.com/identitatem/dex-operator.git
cd dex-operator
oc new-project dex-operator

# To use prebuilt image. Otherwise, you can reset these variables and build your own.
export IMAGE_TAG_BASE=quay.io/cdoan/dex-operator
export VERSION=0.0.2

# this will deploy the operator bundle as a catalog source and deploy the operator from there.
make sdk-run

# test the DexClient CR
oc apply -f config/samples/auth_v1alpha1_dexclient.yaml

# test the DexServer CR
oc apply -f config/samples/auth_v1alpha1_dexserver.yaml
```

## Using a deployment manifest

```bash
oc new-project dex-operator
oc apply -f bundle/manifests/auth.identitatem.io_dexclients.yaml
oc apply -f bundle/manifests/auth.identitatem.io_dexservers.yaml
oc apply -f hack/deployment.yaml
```

# References

See Reference: https://hackmd.io/@0HKGaOf5Rg-SU-pJybkgKw/B1GhGowAO
