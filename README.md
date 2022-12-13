# acs-sensor-policy-set

1 - Create your ACSCS instance at console.redhat.com/beta

2 - Download the cloud init bundle (Kubernetes Secrets)

3 - Either apply them manually (oc apply -f init-bundle.yaml) or place in the input-sensor/acs-secrets.yml file(the policy will apply all secrets contained in that file).

4 - Get the UI and Endpoint URLs of your instance and place it in the input-sensor/acs-secrets.yml, base64 encoded.

5 - Create this policySet with PolicyGenerator in RHACM.

PS: This policySet will be target to every managed cluster in RHACM. If you want a managed cluster to be out of this placement, apply the following label to the cluster: "acscs=Skip"
