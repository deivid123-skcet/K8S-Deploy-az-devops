# K8S-Deploy-az-devops

O BackEnd serve somente para fazer um teste de conexão com o banco de dados e o frontend para enviar os dados para o backend, sendo necessario colocar a url do backend quando for gerado dentro do arquivo js.js na pasta front-end.

Essa pipeline foi criada no AzureDevops, sendo assim sendo necessario a criação do Service connection do Kubernetes antes da criação.

Link da documentação de com instruções de como criar uma pipeline de CI/CD com o Azure devops e GKE: https://cloud.google.com/architecture/creating-cicd-pipeline-vsts-kubernetes-engine#.net-corelinux_3

Tambem necessario criar o service connection do repositorio do docker, no meu caso foi do Docker hub.

A parte de secrets foi usado do proprio Azure Devops.


Abaixo segue o que cada step da pipeline faz.

Task 1: Efetua o Replace da senha do banco de dados no arquivo Dockerfile que está gravado na biblioteca de variaveis do azure devops.

Task 2: Efetua o Replace da senha do banco de dados no arquivo conexão.php que está gravado na biblioteca de variaveis do azure devops.

Task 3: Efetua o build da imagem do backend e o push para o repositorio do dockerhub.

Task 4: Efetua o build da imagem do banco de dados e o push para o repositorio do dockerhub.

Task 5: Cria os Serviços do K8s que está no GCP sendo eles o LoadBalancer e a connection do banco para que possa se comunicar com o backend.

Task 6: Cria os Deployments do K8s sendo eles o PVC para o banco de dados, o deployment do banco de dados e o deployment do backend com 6 replicas.


