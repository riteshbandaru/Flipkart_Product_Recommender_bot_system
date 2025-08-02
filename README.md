# Flipkart Product Recommender Bot System

A machine learning-powered product recommendation system for Flipkart with web interface and comprehensive monitoring capabilities.

## 🚀 Features

- **Intelligent Product Recommendations**: Advanced ML algorithms for personalized product suggestions
- **Web Interface**: User-friendly Flask web application
- **Real-time Monitoring**: Integrated Prometheus metrics and Grafana dashboards
- **Containerized Deployment**: Docker support for easy deployment
- **Kubernetes Ready**: Production-ready deployment configuration for Kubernetes clusters
- **CI/CD Pipeline**: Automated deployment with monitoring setup

## 🛠️ Tech Stack

- **Backend**: Python, Flask
- **Machine Learning**: Scikit-learn, Pandas, NumPy
- **Frontend**: HTML, CSS, JavaScript
- **Monitoring**: Prometheus, Grafana
- **Containerization**: Docker
- **Orchestration**: Kubernetes, Minikube
- **Cloud Platform**: Google Cloud Platform (GCP)

## 📁 Project Structure

```
Flipkart_Product_Recommender_bot_system/
├── data/                    # Dataset and data processing files
├── flipkart/               # Core recommendation engine
├── grafana/                # Grafana configuration and dashboards
├── prometheus/             # Prometheus monitoring setup
├── static/                 # CSS, JavaScript, and image files
├── templates/              # HTML templates for Flask app
├── utils/                  # Utility functions and helpers
├── app.py                  # Main Flask application
├── Dockerfile              # Docker container configuration
├── flask-deployment.yaml   # Kubernetes deployment configuration
├── requirements.txt        # Python dependencies
├── setup.py               # Package setup configuration
└── test.py                # Test cases
```

## 🚀 Quick Start

### Prerequisites

- Python 3.7+
- Docker
- Kubernetes cluster (Minikube for local development)
- Google Cloud Platform account (for production deployment)

### Local Development

1. **Clone the repository**
   ```bash
   git clone https://github.com/riteshbandaru/Flipkart_Product_Recommender_bot_system.git
   cd Flipkart_Product_Recommender_bot_system
   ```

2. **Create virtual environment**
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```

3. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```

4. **Run the application**
   ```bash
   python app.py
   ```

5. **Access the application**
   Open your browser and navigate to `http://localhost:5000`

## 🐳 Docker Deployment

1. **Build the Docker image**
   ```bash
   docker build -t flipkart-recommender .
   ```

2. **Run the container**
   ```bash
   docker run -p 5000:5000 flipkart-recommender
   ```

## ☸️ Kubernetes Deployment

### Local Deployment with Minikube

1. **Start Minikube cluster**
   ```bash
   minikube start
   ```

2. **Point Docker to Minikube**
   ```bash
   eval $(minikube docker-env)
   ```

3. **Build Docker image**
   ```bash
   docker build -t flask-app:latest .
   ```

4. **Create Kubernetes secrets**
   ```bash
   kubectl create secret generic llmops-secrets \
     --from-literal=GROQ_API_KEY="" \
     --from-literal=ASTRA_DB_APPLICATION_TOKEN="" \
     --from-literal=ASTRA_DB_KEYSPACE="default_keyspace" \
     --from-literal=ASTRA_DB_API_ENDPOINT="" \
     --from-literal=HF_TOKEN="" \
     --from-literal=HUGGINGFACEHUB_API_TOKEN=""
   ```

5. **Deploy the application**
   ```bash
   kubectl apply -f flask-deployment.yaml
   ```

6. **Check deployment status**
   ```bash
   kubectl get pods
   ```

7. **Expose the service**
   ```bash
   kubectl port-forward svc/flask-service 5000:80 --address 0.0.0.0
   ```

## 🌐 Google Cloud Platform Deployment

### 1. Initial Setup

1. **Create VM Instance on Google Cloud**
   - Go to VM Instances and click "Create Instance"
   - **Name**: `flipkart-recommender-vm`
   - **Machine Type**: E2-Standard (16 GB RAM)
   - **Boot Disk**: Ubuntu 24.04 LTS (256 GB)
   - **Networking**: Enable HTTP and HTTPS traffic

2. **Connect to VM via SSH**

### 2. Configure VM Instance

1. **Clone repository**
   ```bash
   git clone https://github.com/riteshbandaru/Flipkart_Product_Recommender_bot_system.git
   cd Flipkart_Product_Recommender_bot_system
   ```

2. **Install Docker**
   ```bash
   # Add Docker's official GPG key
   sudo apt-get update
   sudo apt-get install ca-certificates curl
   sudo install -m 0755 -d /etc/apt/keyrings
   sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
   sudo chmod a+r /etc/apt/keyrings/docker.asc

   # Add the repository to Apt sources
   echo \
     "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \
     $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
     sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
   sudo apt-get update

   # Install Docker packages
   sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin

   # Test Docker installation
   docker run hello-world
   ```

3. **Configure Docker (run without sudo)**
   ```bash
   sudo groupadd docker
   sudo usermod -aG docker $USER
   newgrp docker
   docker run hello-world
   ```

4. **Enable Docker to start on boot**
   ```bash
   sudo systemctl enable docker.service
   sudo systemctl enable containerd.service
   ```

### 3. Install and Configure Minikube

1. **Install Minikube**
   ```bash
   curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
   sudo install minikube-linux-amd64 /usr/local/bin/minikube
   ```

2. **Start Minikube**
   ```bash
   minikube start
   ```

3. **Install kubectl**
   ```bash
   sudo snap install kubectl --classic
   kubectl version --client
   ```

4. **Verify installation**
   ```bash
   minikube status
   kubectl get nodes
   kubectl cluster-info
   ```

### 4. Configure Git

```bash
git config --global user.email "your-email@example.com"
git config --global user.name "your-username"
```

### 5. Deploy Application

1. **Point Docker to Minikube**
   ```bash
   eval $(minikube docker-env)
   ```

2. **Build Docker image**
   ```bash
   docker build -t flask-app:latest .
   ```

3. **Create secrets**
   ```bash
   kubectl create secret generic llmops-secrets \
     --from-literal=GROQ_API_KEY="" \
     --from-literal=ASTRA_DB_APPLICATION_TOKEN="" \
     --from-literal=ASTRA_DB_KEYSPACE="default_keyspace" \
     --from-literal=ASTRA_DB_API_ENDPOINT="" \
     --from-literal=HF_TOKEN="" \
     --from-literal=HUGGINGFACEHUB_API_TOKEN=""
   ```

4. **Deploy application**
   ```bash
   kubectl apply -f flask-deployment.yaml
   kubectl get pods
   ```

5. **Expose service**
   ```bash
   kubectl port-forward svc/flask-service 5000:80 --address 0.0.0.0
   ```

## 📊 Monitoring Setup

### Prometheus and Grafana Deployment

1. **Create monitoring namespace**
   ```bash
   kubectl create namespace monitoring
   kubectl get ns
   ```

2. **Deploy Prometheus**
   ```bash
   kubectl apply -f prometheus/prometheus-configmap.yaml
   kubectl apply -f prometheus/prometheus-deployment.yaml
   ```

3. **Deploy Grafana**
   ```bash
   kubectl apply -f grafana/grafana-deployment.yaml
   ```

4. **Expose Prometheus (Port 9090)**
   ```bash
   kubectl port-forward --address 0.0.0.0 svc/prometheus-service -n monitoring 9090:9090
   ```

5. **Expose Grafana (Port 3000)**
   ```bash
   kubectl port-forward --address 0.0.0.0 svc/grafana-service -n monitoring 3000:3000
   ```

### Grafana Configuration

1. **Access Grafana**
   - URL: `http://YOUR_VM_EXTERNAL_IP:3000`
   - Username: `admin`
   - Password: `admin`

2. **Configure Data Source**
   - Go to Settings > Data Sources > Add Data Source
   - Choose Prometheus
   - URL: `http://prometheus-service.monitoring.svc.cluster.local:9090`
   - Click Save & Test

3. **Create Dashboards**
   - Import pre-configured dashboards from `grafana/` directory
   - Monitor application metrics, system performance, and recommendation accuracy

## 🧪 Testing

Run the test suite:
```bash
python test.py
```

## 📈 How It Works

1. **Data Processing**: The system processes Flipkart product data from the `data/` directory
2. **Recommendation Engine**: Core ML algorithms in the `flipkart/` module generate personalized recommendations
3. **Web Interface**: Flask application serves recommendations through a user-friendly interface
4. **Monitoring**: Prometheus collects metrics while Grafana provides visualization dashboards
5. **Containerization**: Docker ensures consistent deployment across environments
6. **Orchestration**: Kubernetes manages scaling, load balancing, and service discovery

## 🔧 Configuration

- **Application Settings**: Modify `app.py` for Flask configuration
- **ML Parameters**: Update model parameters in the `flipkart/` module
- **Monitoring**: Configure thresholds in `prometheus/` and `grafana/` directories
- **Deployment**: Adjust resource limits in `flask-deployment.yaml`

## 📝 Environment Variables

Create a `.env` file or configure the following secrets:

```bash
GROQ_API_KEY=your_groq_api_key
ASTRA_DB_APPLICATION_TOKEN=your_astra_token
ASTRA_DB_KEYSPACE=default_keyspace
ASTRA_DB_API_ENDPOINT=your_astra_endpoint
HF_TOKEN=your_huggingface_token
HUGGINGFACEHUB_API_TOKEN=your_huggingface_hub_token
```

## 🚀 Accessing the Application

After successful deployment:

- **Main Application**: `http://YOUR_VM_EXTERNAL_IP:5000`
- **Prometheus Metrics**: `http://YOUR_VM_EXTERNAL_IP:9090`
- **Grafana Dashboards**: `http://YOUR_VM_EXTERNAL_IP:3000`

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## 📝 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 👨‍💻 Author

**Ritesh Bandaru**
- GitHub: [@riteshbandaru](https://github.com/riteshbandaru)

## 🙏 Acknowledgments

- Flipkart for providing the dataset
- Open source community for the amazing tools and libraries
- Google Cloud Platform for hosting infrastructure
- Kubernetes and Docker communities for containerization support

## 📞 Support

If you have any questions or need help:

- Open an issue in this repository
- Check the troubleshooting section in the documentation
- Contact the maintainer through GitHub

## 🔍 Troubleshooting

### Common Issues

1. **Docker build fails**: Ensure all dependencies are listed in `requirements.txt`
2. **Minikube won't start**: Check if virtualization is enabled in BIOS
3. **Pods in CrashLoopBackOff**: Check logs with `kubectl logs <pod-name>`
4. **Port forwarding issues**: Ensure firewall rules allow the specified ports
5. **Grafana connection issues**: Verify Prometheus service URL and networking

### Useful Commands

```bash
# Check cluster status
kubectl cluster-info
kubectl get nodes
kubectl get pods --all-namespaces

# View logs
kubectl logs <pod-name>
kubectl describe pod <pod-name>

# Check services
kubectl get svc
kubectl describe svc <service-name>

# Monitor resources
kubectl top nodes
kubectl top pods
```

---

⭐ **Star this repository if you found it helpful!**

---

