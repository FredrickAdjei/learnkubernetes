REPLICASETS
This is where labeling our pods
during creation comes in handy.
We could now provide these labels
as a filter for Replica Set.
Under the selector section, we use the match labels filter
and provide the same label that we used
while creating the pods.
This way, the Replica Set knows which pods to monitor.

update replicaset by changing the yaml file and using command

kubectl replace -f <file.yaml>.  or

kubectl scale replicaset --replicas=6 <replicasetname> if u use the yamlfile it wont update