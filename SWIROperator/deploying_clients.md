# Deploying clients 

In this case all SWIR clients need to be deployed into one namespace **library**. Let's create a namespace for our deployment

`kubectl create namespace library`{{execute}}

Our solution consist of three SWIR clients:  
### Books department
`kubectl -n library apply -f clients/books_client.yaml`{{execute}}

### Magazines department
`kubectl -n library apply -f clients/magazines_client.yaml`{{execute}}

### Helpdesk
`kubectl -n library apply -f clients/helpdesk_client.yaml`{{execute}}


The config file is super simple:  
`clients/books_client.yaml`{{open}} and `clients/magazines_client.yaml`{{open}} only tell that the APIs will be exposed on a local interface and port 8090.

`clients/helpdesk_client.yaml`{{open}} only shows that sidecar will be available at port 50051 and that the client wants to invoke APIs on services identifies as books and magazines. The magic of figuring out how to connect to Books and Magazines is left to SWIR Sidecar.

The crucial bit is the labels section which tells the SWIR Operator that this deployment belongs to SWIR Platform and which config file should be applied to this particular deployment.

```
  labels:
    swir: helpdesk
```





