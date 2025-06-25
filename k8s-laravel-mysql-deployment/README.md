# Kubernetes Laravel and MySQL Deployment

This project contains Kubernetes manifests for deploying a Laravel application with a MySQL database. It includes a deployment for a web server running NGINX with PHP 8.2+ and a MySQL database.

## Project Structure

```
k8s-laravel-mysql-deployment
├── manifests
│   ├── deployment.yaml
│   ├── service.yaml
│   └── configmap.yaml
└── README.md
```

## Prerequisites

- Kubernetes cluster (Minikube, GKE, EKS, etc.)
- kubectl command-line tool installed
- Helm (optional, if using Helm charts)

## Deployment Instructions

1. **Clone the repository**:
   ```bash
   git clone <repository-url>
   cd k8s-laravel-mysql-deployment
   ```

2. **Apply the ConfigMap** (if needed):
   ```bash
   kubectl apply -f manifests/configmap.yaml
   ```

3. **Deploy the application**:
   ```bash
   kubectl apply -f manifests/deployment.yaml
   ```

4. **Expose the web server**:
   ```bash
   kubectl apply -f manifests/service.yaml
   ```

5. **Check the status of the pods**:
   ```bash
   kubectl get pods
   ```

6. **Access the application**:
   - If using a LoadBalancer service, get the external IP:
     ```bash
     kubectl get services
     ```
   - If using a ClusterIP service, you may need to port-forward:
     ```bash
     kubectl port-forward service/<service-name> 8080:8080
     ```

## Database Configuration

The MySQL database is configured with the following credentials:
- Database Name: `<vandy>-db`
- User: `root`
- Password: `Hello@123`

Make sure to update your Laravel `.env` file with these credentials to connect to the database.

## Notes

- Ensure that your Kubernetes cluster has sufficient resources to run the application.
- Modify the deployment and service manifests as needed to fit your specific requirements.