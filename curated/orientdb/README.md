# Infinity OrientDB helm chart

Orient DB helm chart

## Installation:

`helm install . --name <RELEASE-NAME> --namespace <NAMESPACE> --set rootpassword=<PASSWORD>`

If rootPassword is not set, a random one will be used.
`helm install . --name <RELEASE-NAME> --namespace <NAMESPACE> --set rootpassword=<PASSWORD>`

## Scaling:

Get the name of your statefulset:

`kubectl get statefulsets -n <NAMESPACE>`

Then scale it:

`kubectl scale <STATEFULSET-NAME> --replicas=<DESIRED-SIZE>`

This scaling is possible due to the hazelcast plugin used for node discovery. For more information check the config file under config/hazelcast.xml and at http://docs.hazelcast.org/docs/3.0/manual/html/ch12s02.html

## Testing:

`helm test <RELEASE-NAME> --cleanup --timeout 1000`

## Accessing the UI

`kubectl port-forward <POD-NAME> 2480:2480 -n <NAMESPACE>`

Note: POD-NAME is any pod from the statefulset.

## Editing the hazelcast configuration

The hazelcast configuration can be edited at runtime by editing the config.yaml file in the templates of the orient. As of right now only the hazelcast file can be edited dynamically

## Maintainers

Product Engineering Team (AKA The Sommeliers) @ [B-yond](https://www.b-yond.com)
E: <sommeliers@b-yond.com>