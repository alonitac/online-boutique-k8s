# Kubernetes

## The Online Boutique

<p align="center">
<img src="img/onlineboutique.png" />
</p>

Online Boutique is a cloud-first microservices demo application. Online Boutique consists of an 11-tier microservices application. The application is a web-based e-commerce app where users can browse items, add them to the cart, and purchase them.

Google uses this application to demonstrate use of technologies like Kubernetes, Istio, etc... you can watch the original GitHub repo [here](https://github.com/GoogleCloudPlatform/microservices-demo).

In this exercise we will deploy the Online Boutique stack, and perform some changes to the service. You can work on any k8s cluster that suits you - minikube, k3s, k0s etc...

## Deploy the Online Boutique service

Deploy `release/kubernetes-manifests.yaml` in k8s cluster.

1. Fork the exercise repo, then clone your forked repo locally: https://github.com/alonitac/online-boutique-k8s.git
2. Under `release/` directory you can find the manifests for every service, deploy all manifests in your k8s cluster, you can do it by `kubectl apply -k release/`
3. visit the app


## Tasks

### Change Cart service port

The port of `cartservice` Service is `7070`, change it to `7078`.

### Autoscale the Product catalog


The `productcatalogservice` Deployment is running as a single instance deployment. Configure an HorizontalPodAutoscaler to autoscale the deployment's pods. Set the min replicas as `1`, max as `4`. Set the target CPU utilization to `60%`.

In order to test the autoscaler in action, run the load test.

### Load Generator service - ConfigMap code migration

Review the Load Generator [manifest YAML](release/load-generator.yaml). This Deployment consists of `initContainer` which is responsible to ping the frontend service, and the regular container which performs the load test itself.

Migrate the executed commands of the init container (`spec.spec.initContainers[0].command`) into a `ConfigMap`.

### Redis HELM migration

Instead of using the `redis-cart` Deployment, deploy this service as a Helm chart using [Bitnami's chart](https://github.com/bitnami/charts/tree/main/bitnami/redis/#installing-the-chart)

###


# Good Luck

Don't hesitate to ask any questions
