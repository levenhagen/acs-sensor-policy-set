# acs-sensor-policy-set

This is a attempt to have a policy to 

1 - If you don't have one, create your ACSCS instance at console.redhat.com/beta.

2 - Also in case you haven't yet, download the cloud init bundle (Kubernetes Secrets).

3 - Apply the init bundle on the hub cluster: kubectl create -f <init_bundle_secrets>.yaml -n rhacs-operator (If the namespace doesn't exists, create it with ```oc create namespace rhacs-operator```)

4 - Create one more secret containing ACSCS URLs in the Hub Cluster: ```kubectl create secret generic acs-credential-endpoint --from-literal=UI=<YOUR ACSCS UI URL> --from-literal=endpoint=< YOUR ACSCS DATA ENDPOINT> -n rhacs-operator``` (You can get these info in your instance dashboard in https://console.redhat.com/beta/application-services/acs/instances)

5 - in RHACM, create this policySet with PolicyGenerator in the applications view.

PS: This policySet will target every cluster in RHACM. If you don't want a given cluster to be tracked, apply the following label to it: "acscs=Skip"
