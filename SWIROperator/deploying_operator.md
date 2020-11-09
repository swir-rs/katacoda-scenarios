


### Create a namespace 
We will create a separate namespace **swirop** to isolate the operator from our library solution
`kubectl create namespace swirop`{{execute}}  

### Create necessary config maps
We will use these config maps to configure SWIR sidecar

`kubectl -n swirop create configmap swir-operator-config-library --from-file=./operator/books.yaml --from-file=./operator/helpdesk.yaml --from-file=./operator/magazines.yaml`{{execute}}

`kubectl -n swirop create configmap swir-operator-certs-library --from-file=./certs/ca-chain.cert.pem --from-file=./certs/client.internal_grpc.swir.rs.cert.pem --from-file=./certs/client.internal_grpc.swir.rs.key.pem --from-file=./certs/server.internal_grpc.swir.rs.cert.pem --from-file=./certs/server.internal_grpc.swir.rs.key.pem`{{execute}}

### Add roles and permissions 
Roles and permissions are required so SWIR operator can receive notifications about deployed resources

`kubectl -n swirop apply -f operator/service_account.yaml`{{execute}}

`kubectl -n swirop apply -f operator/role.yaml`{{execute}}

`kubectl -n swirop apply -f operator/role_binding.yaml`{{execute}}

### Deploy the operator
`kubectl -n swirop apply -f operator/operator.yaml`{{execute}}

### Wait for the operator
You might want to execute the command below until Pods are **Running** and in **READY** state
`kubectl -n swirop get po`{{execute}}



