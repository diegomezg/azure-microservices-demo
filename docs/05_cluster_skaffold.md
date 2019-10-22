# Azure Hipster Shop: AKS Microservices Demo

## 5. Set up the kubernetes cluster with Skaffold

```
$ cd ..
$ cd microservices-demo
$ skaffold run --tail

Generating tags...
 - testacr22.azurecr.io/emailservice -> testacr22.azurecr.io/emailservice:v0.1.2-2-g2177813
 - testacr22.azurecr.io/productcatalogservice -> testacr22.azurecr.io/productcatalogservice:v0.1.2-2-g2177813
 - testacr22.azurecr.io/recommendationservice -> testacr22.azurecr.io/recommendationservice:v0.1.2-2-g2177813
 - testacr22.azurecr.io/shippingservice -> testacr22.azurecr.io/shippingservice:v0.1.2-2-g2177813
 - testacr22.azurecr.io/checkoutservice -> testacr22.azurecr.io/checkoutservice:v0.1.2-2-g2177813
 - testacr22.azurecr.io/paymentservice -> testacr22.azurecr.io/paymentservice:v0.1.2-2-g2177813
 - testacr22.azurecr.io/currencyservice -> testacr22.azurecr.io/currencyservice:v0.1.2-2-g2177813
 - testacr22.azurecr.io/cartservice -> testacr22.azurecr.io/cartservice:v0.1.2-2-g2177813
 - testacr22.azurecr.io/frontend -> testacr22.azurecr.io/frontend:v0.1.2-2-g2177813
 - testacr22.azurecr.io/loadgenerator -> testacr22.azurecr.io/loadgenerator:v0.1.2-2-g2177813
 - testacr22.azurecr.io/adservice -> testacr22.azurecr.io/adservice:v0.1.2-2-g2177813
Tags generated in 16.110141ms
Checking cache...
 - testacr22.azurecr.io/emailservice: Found. Pushing
The push refers to repository [testacr22.azurecr.io/emailservice]
```

The Hipster Shop demo uses a Stackdriver log monitor that is specific to Google Cloud, and its driver will try to connect several times and then give up.
See [microservices-demo/docs/development-principles.md](https://github.com/GoogleCloudPlatform/microservices-demo/blob/master/docs/development-principles.md) for more information.

## Check the cluster

```
$ kubectl get nodes
```

Check all pods

```
$ kubectl get pods --all-namespaces
```

```
$ kubectl get service frontend-external

NAME                TYPE           CLUSTER-IP     EXTERNAL-IP   PORT(S)        AGE
frontend-external   LoadBalancer   10.0.177.210   <pending>     80:31482/TCP   12s
```

### Improvements

You could set up a CI/CD pipeline in Azure Devops portal likend to a git repository to automatically deploy the cluster when a commit to __master__ branch is done.

---
[Next step: 6. Create cluster with Skaffold](../docs/06_helm.md)  
[Previous step: 4. Get Kubectl and ACR credentials](../docs/04_get_credentials.md)
