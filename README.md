# DevOps Monitoring Project (Terraform + AWS EKS + Kubernetes + Prometheus + Grafana)

This project sets up a complete **monitoring stack** using **Terraform**, **AWS EKS**, **Kubernetes**, **Prometheus**, **Grafana**, and **Alertmanager**.  
It is designed to demonstrate **real-world DevOps skills**, including infrastructure as code, monitoring, alerting, and Kubernetes deployments.

---

## 🚀 Features
- **Infrastructure as Code**: AWS EKS cluster provisioned using Terraform.
- **Kubernetes Monitoring**: Prometheus for metrics collection, Grafana for visualization.
- **Alerting**: Configured Alertmanager for custom alerts.
- **Dashboards**: Pre-configured Grafana dashboards for Kubernetes, Nodes, and Applications.
- **CI/CD Integration**: GitHub Actions workflow for automated Terraform and Helm deployments.

---

## 🏗️ Architecture
Terraform → AWS EKS Cluster (Kubernetes)
→ Helm (kube-prometheus-stack)
→ Prometheus → Metrics Collection
→ Grafana → Dashboards
→ Alertmanager → Notifications

yaml
Copier
Modifier

---

## ⚙️ Setup Instructions

### 1️⃣ Clone the repository
```bash
git clone https://github.com/your-username/nodejs-eks-terraform-monitoring.git
cd nodejs-eks-terraform-monitoring
2️⃣ Provision Infrastructure (EKS Cluster)
bash
Copier
Modifier
cd terraform
terraform init
terraform apply
3️⃣ Configure kubectl
bash
Copier
Modifier
aws eks update-kubeconfig --region us-east-1 --name devops-monitoring-cluster
4️⃣ Deploy Monitoring Stack
bash
Copier
Modifier
helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
helm repo update
helm upgrade --install monitoring prometheus-community/kube-prometheus-stack -f k8s/monitoring/prometheus-values.yaml
5️⃣ Verify Deployment
bash
Copier
Modifier
kubectl --namespace monitoring get pods
📊 Grafana Access
Username: admin

Password:

bash
Copier
Modifier
kubectl get secret monitoring-grafana -n monitoring -o jsonpath="{.data.admin-password}" | base64 -d
URL:

bash
Copier
Modifier
kubectl get svc monitoring-grafana -n monitoring
Use the LoadBalancer URL to access Grafana in the browser.

![alt text](grafana.png)