# MS-AUTH-K8S

Este repositório contém os manifestos Kubernetes para o microsserviço **hackaton-ms-auth**, responsável pela autenticação e autorização da aplicação.

## 📂 Estrutura do Projeto

```
ms-auth-k8s/
│-- kubernetes/
│   ├── Auth/
│   │   ├── auth-configmap.yaml
│   │   ├── auth-deployment.yaml
│   │   ├── auth-hpa.yaml
│   │   ├── auth-service.yaml
```

- **`auth-configmap.yaml`**: Define as variáveis de ambiente e configurações necessárias para o serviço de autenticação.

- **`auth-deployment.yaml`**: Define o deployment do microsserviço, incluindo réplicas e especificações do container.

- **`auth-hpa.yaml`**: Configuração do Horizontal Pod Autoscaler (HPA) para escalar automaticamente os pods com base na carga de CPU.

- **`auth-service.yaml`**: Define o service para expor o microsserviço dentro do cluster Kubernetes.

## 🚀 Implantação no Kubernetes

### 1️⃣ Habilitar Kubernetes no Docker Desktop
Caso ainda não tenha habilitado o suporte ao Kubernetes no Docker Desktop, faça isso nas configurações do Docker.

### 2️⃣ Aplicar os manifestos
Execute os seguintes comandos para criar os recursos no cluster:

```sh
kubectl apply -f kubernetes/Auth/auth-configmap.yaml
kubectl apply -f kubernetes/Auth/auth-deployment.yaml
kubectl apply -f kubernetes/Auth/auth-hpa.yaml
kubectl apply -f kubernetes/Auth/auth-service.yaml
```

### 3️⃣ Acessar o serviço
Após a implantação, o serviço estará disponível dentro do cluster. Para expor localmente, utilize um port-forward:

```sh
kubectl port-forward svc/auth-service 8080:80
```
Agora, a API de autenticação estará acessível em `http://localhost:8080`.
