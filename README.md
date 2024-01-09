# argocd-ocp
1. Install argocd operator (tested on OCP 4.10.36)
2. Crear Argocd instance and add this to allow sso using ocp:

```yaml
spec:
  sso:
    provider: dex
    dex:
      openShiftOAuth: true
```
3. Add rbacs [1]
```sh
oc adm groups new cluster-admins
oc adm groups add-users cluster-admins USER
oc adm policy add-cluster-role-to-group cluster-admin cluster-admins
```yaml

[1] https://docs.openshift.com/gitops/1.11/accesscontrol_usermanagement/configuring-sso-on-argo-cd-using-dex.html
