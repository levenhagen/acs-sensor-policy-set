# ACS Cloud Service agent(Sensor) - ACM PolicySet

With this policySet, you'll be able to apply policies to your ACM managed clusters, in order to enroll them in ACS Cloud Service as well.

Read the short tutorial:

1 - If you don't have one, create your ACSCS instance at console.redhat.com/beta.

2 - Also, in case you haven't yet, download the cloud init bundle (Kubernetes Secrets).

3 - Apply the init bundle to the ACM Hub cluster: kubectl create -f <init_bundle_secrets>.yaml -n rhacs-operator (If the namespace doesn't exist, create it with ```oc create namespace rhacs-operator```)

4 - Create one more secret containing ACSCS URLs in the Hub Cluster: ```kubectl create secret generic acs-credential-endpoint --from-literal=UI=<YOUR ACSCS UI URL> --from-literal=endpoint=<YOUR ACSCS DATA ENDPOINT> -n rhacs-operator``` (You can get these info in your instance dashboard in https://console.redhat.com/beta/application-services/acs/instances)

5 - Now in RHACM, create this policySet with PolicyGenerator in the Applications menu.

PS: This policySet will target every managed cluster in RHACM. If you don't want a given cluster to be tracked/enrolled in ACSCS, apply the following label to the given cluster(s) before creating and applying this policySet: "acscs=Skip"
