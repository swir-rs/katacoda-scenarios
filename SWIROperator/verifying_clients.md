
To verify that the clients are running run

`kubectl -n library get po`{{execute}}

You might need to repeat this command until all pods are in **Ready** state


As you see there is only one container in each pod. You can inspect the logs by running

`kubectl -n library logs helpdesk-`{{copy}}<kbd>Tab</kbd>

	You need to paste this line into the terminal and press <kbd>Tab</kbd> for the autocomplete to populate the full name of the pod.
	
Closer inspection will show that there are plenty of warning messages in the log indicating that **Helpdesk** is not able to connect to its sidecar...

...which is correct since we have not deployed the SWIR Operator yet... and this what we are going to do in the next step.
