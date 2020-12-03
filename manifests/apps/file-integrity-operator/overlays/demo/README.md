# OpenShift File Integrity Operator

## Usage

This is to deploy the [File Integrity Operator](https://access.redhat.com/documentation/en-us/openshift_container_platform/4.6/html/security_and_compliance/file-integrity-operator) into an OpenShift 4.6 or later cluster. This operator
provides file integrity scanning based on AIDE (Advanced Intrusion Detection Environment).

Some useful commands for checking the configuration & results:


`oc get fileintegrity -n openshift-operators`

`oc get fileintegrity -n openshift-operators worker-fileintegrity -o jsonpath="{ .status.phase }"`

`oc get fileintegritynodestatuses -n openshift-operators`

`oc get fileintegritynodestatuses.fileintegrity.openshift.io -n openshift-operators -ojsonpath='{.items[*].results}' | jq`

# Get ConfigMap from above output and view full report here
`oc describe cm aide-ds-worker-fileintegrity-ip-10-0-130-192.ec2.internal-failed`
