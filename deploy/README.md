## Basic installation

To run a basic installation with `kubectl`, run the following:

```bash
kubectl apply -f basic/rbac.yaml
kubectl apply -f basic/crd.yaml
kubectl apply -f basic/operator.yaml
kubectl apply -f basic/redis-enterprise-cluster.yaml
```

or just run
```bash
kubectl apply -f basic -R
```

### PSP
If you are running pod security policy (PSP), you will need to apply the `psp.yaml` file
BEFORE applying the basic yaml folder. To apply the psp.yaml file run
```bash
kubectl apply -f advanced/psp.yaml
```
 
 
 ### OpenShift
 To run OpenShift you will need to run a bit more stuff.
 ```bash
oc apply -f openshift/scc.yaml
oc apply -f scc.yamloc adm policy add-scc-to-group redis-enterprise-scc system:serviceaccounts:\<my-project\>
oc apply -f openshift/sb_rbac.yaml
oc adm policy add-cluster-role-to-user redis-enterprise-operator-sb --serviceaccount redis-enterprise-operator --rolebinding-name=redis-enterprise-operator-sb
```

From here you can continue almost like in basic;
```bash
kubectl apply -f openshift/crd.yaml
kubectl apply -f openshift/operator_rhel.yaml
kubectl apply -f openshift/redis-enterprise-cluster_rhel.yaml
```