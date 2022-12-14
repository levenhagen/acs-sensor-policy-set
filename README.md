# acs-sensor-policy-set

This is a attempt to have a policy to 

1 - If you don't have one, create your ACSCS instance at console.redhat.com/beta.

2 - Also in case you haven't yet, download the cloud init bundle (Kubernetes Secrets).

3 - Apply the init bundle on the cluster to be secured by ACSCS: kubectl create -f <init_bundle>.yaml -n stackrox

4 - Create one more secret containing ACSCS URLs: ```kubectl create secret generic acs-credential-endpoint --from-literal=UI=<YOUR ACSCS UI URL> --from-literal=endpoint=< YOUR ACSCS DATA ENDPOINT>``` (You can get these info in your instance dashboard in https://console.redhat.com/beta/application-services/acs/instances)

5 - in RHACM, create this policySet with PolicyGenerator in the applications view.

PS: This policySet will target every cluster in RHACM. If you don't want a given cluster to be tracked, apply the following label to it: "acscs=Skip"

Future improvements: automate the process of creating the secrets to every managed cluster in RHACM.
