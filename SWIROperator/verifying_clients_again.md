

Since we deployed SWIR Operator in the previous step it would be good to verify that it works as expected.

Since we have injected SWIR Operator, we should be seeing two containers per pod. It will take some time to transition to a steady state so for a while you might see pods with one and two containers in different states before older versions of pods are eventually terminated and garbage collected by the system.

`kubectl -n library get po`{{execute}}

You might need to repeat this command until all pods have two containers and are in **Ready** state.

Finally, we should be able to inspect the logs of **Helpdesk** client

`kubectl -n library logs helpdesk-`{{copy}}<kbd>Tab</kbd>
You need to paste this line into the terminal and press <kbd>Tab</kbd> for the autocomplete to populate the full name of the pod. 

All errors should be gone since now the SWIR sidecar instance has been created, the client can connect to its sidecar and avai of its functionality to connect to other microservices in **Library** solution.
