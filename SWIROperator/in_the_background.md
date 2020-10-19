

While you are reading this, Kubernetes will notify the sidecar about all resources that the SWIR Operator is ineterested in. If you remember from the second step SWIR Operator wants to know about all deployements with **swir** label.
SWIR Operator will check the namespace and the name of the deployment and will try to find the appropriate config file. On success, SWIR Operator will update the deployment specs and add another and configure a container for SWIR Sidecar.

Hopefully by now the operator is ready... let check it again 

### Wait for the operator
You might want to execute the command below until Pods are **Running** and in **READY** state
`kubectl -n swirop get po`{{execute}}

### You can check the logs 
`kubectl -n swirop logs swir-operator`{{copy}}<kbd>Tab</kbd>

You need to paste this line into the terminal and press <kbd>Tab</kbd> for the autocomplete to populate the full name of the pod.


