# OpenShift Compliance Operator

## Usage

This is to deploy the [Compliance Operator](https://docs.openshift.com/container-platform/4.6/security/compliance_operator/compliance-operator-understanding.html) into an OpenShift 4.6 or later cluster. This operator
provides compliance scanning based on selectable set of rules.

Some useful commands for checking the scan


`oc get profiles.compliance -n  openshift-operators`

Profiles will be references/managed via the defined `ScanSetting` and `ScanSettingBinding` objects

`oc get compliancesuite -n  openshift-operators`

`oc get ProfileBundle -n openshift-operators`

`oc get compliancescan -n  openshift-operators`

`oc get ComplianceCheckResult -n  openshift-operators`

`oc patch ComplianceRemediation -n  openshift-operators --patch '{"spec":{"apply":true}}' --type=merge`

Example Applying Patch Manually

```
➜  cluster-config git:(main) ✗ oc get complianceremediations | grep rhcos4-moderate-worker-no-empty-passwords 
rhcos4-moderate-worker-no-empty-passwords                                    NotApplied
➜  cluster-config git:(main) ✗ oc patch complianceremediations rhcos4-moderate-worker-no-empty-passwords --patch '{"spec":{"apply":true}}' --type=merge  
complianceremediation.compliance.openshift.io/rhcos4-moderate-worker-no-empty-passwords patched
➜  cluster-config git:(main) ✗ oc get complianceremediations | grep rhcos4-moderate-worker-no-empty-passwords                                          
rhcos4-moderate-worker-no-empty-passwords                                    Applied
```



