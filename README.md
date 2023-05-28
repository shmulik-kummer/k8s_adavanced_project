# k8s_adavanced_project
CI Pipeline
1. build producer image using the Dockerfile in the producer folder
2. Build consumer imahe using the Dockerfile in the consumer folder
3. Push producer image to Dockerhub
4. Push consumer image to Dockerhub
5. Create Helm chart for deploying consumer and producer application
6. Push the helm chart to Git repo

CD Pipeline

7. checkout helm chart from git
8. Define connectivity to our application’s kubernetes API server.
9. Run ‘helm upgrade’ to deploy the latest image of applications to the cluster.

RabbitMQ
10. Deploy RabbiMQ to the cluster using the stable helm chart at:
https://bitnami.com/stack/rabbitmq/helm
11. Deploy RabbitMQ exporter in order to expose metrics regarding the status of our
RabbitMQ server.
** Create a values.yaml file for configuring deployment of RabbitMQ exporter helm chart deployment.
