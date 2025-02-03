# Basic OPA - Yamls

#### This repository contains the basic steps for deploying OPA Within a GKE cluster. Follow the below steps to enforce a security policy denying all pod deployments across your cluster.
*After forking the attached YAML Files*

---
##### Step 1. 
Install The OPA operator into your Kubernetes cluster 
`Kubectl create -f https://raw.githubusercontent.com/killer-sh/cks-course-environment/master/course-content/opa/gatekeeper.yaml` 

##### Step 2. 
View the new namespace containing your operator
`Kubectl get ns`
*&*
`Kubectl -n gatekeeper-system get pod,svc`

##### Step 3. 
Now as an example we'll deploy the deny all template then the constraint

*You need a template first then the policy to follow your template. You an then see active polices by referencing your template name.*
`kubectl create -f deny-all-template.yaml`
&
`kubectl create -f always-deny-constraint.yaml`

---
Now you'll see across your Kubernetes cluster, No pods will be able to be deployed as Defined in the Rego supporting our OPA policy. 

For more information on how the Rego enforces policy on our cluster, refer to the following notes from a colleague:
https://docs.google.com/document/d/1Zigpzg-LYqRuTmEwJVLsa2Ik1up0HwPjppKIktz0Pds/edit?tab=t.0