1. **Part 1 – Linux & Git (20 Q/A)**
2. **Part 2 – CI/CD & Jenkins (20 Q/A)**
3. **Part 3 – Docker & Kubernetes (20 Q/A)**
4. **Part 4 – Terraform & AWS Core Services (20 Q/A)**
5. **Part 5 – AWS Advanced, Monitoring, Security & Scenario-based (20 Q/A)**

Phir main saare combine karke ek **final PDF** bana dunga jo tu interview me revise kar sake.

---

## **Part 1 – Linux & Git (20 Questions & Answers)**

**Q1. What is Linux, and why is it popular in DevOps?**
**A:** Linux is an open-source operating system known for stability, security, and flexibility. It's popular in DevOps because most cloud servers run Linux, it's lightweight, and supports automation tools.
**Example:** AWS EC2 default AMI is Amazon Linux.

---

**Q2. Command to check current working directory?**

```
pwd
```

---

**Q3. How to list files including hidden ones?**

```
ls -a
```

---

**Q4. Command to check disk usage in human-readable format?**

```
df -h
```

---

**Q5. Difference between `scp` and `rsync`?**
**A:**

* `scp`: Securely copies files between systems but re-copies every time.
* `rsync`: Syncs files efficiently by copying only changed parts.

---

**Q6. How to check which process is using a specific port?**

```
sudo lsof -i :8080
```

---

**Q7. How to search for a specific word in a file?**

```
grep "keyword" filename
```

---

**Q8. How to find top 10 memory-consuming processes?**

```
ps aux --sort=-%mem | head -n 10
```

---

**Q9. Command to compress and extract files?**

```
tar -czvf archive.tar.gz folder/   # Compress
tar -xzvf archive.tar.gz           # Extract
```

---

**Q10. How to check running services in Linux?**

```
systemctl list-units --type=service
```

---

**Q11. What is Git?**
**A:** Git is a distributed version control system used to track changes in source code and collaborate with multiple developers.

---

**Q12. Difference between Git and GitHub?**
**A:**

* Git: Version control tool.
* GitHub: Cloud-based hosting for Git repositories.

---

**Q13. How to clone a Git repository?**

```
git clone <repo_url>
```

---

**Q14. How to check Git commit history?**

```
git log --oneline
```

---

**Q15. How to create a new branch and switch to it?**

```
git branch feature-branch
git checkout feature-branch
```

---

**Q16. How to merge branches in Git?**

```
git checkout main
git merge feature-branch
```

---

**Q17. How to resolve Git merge conflicts?**
**A:**

1. Open conflicting file(s).
2. Edit manually to keep required changes.
3. Stage changes with `git add`.
4. Commit with `git commit`.

---

**Q18. Difference between `git pull` and `git fetch`?**
**A:**

* `git pull`: Fetch + Merge.
* `git fetch`: Only downloads changes but does not merge.

---

**Q19. How to undo the last commit but keep changes?**

```
git reset --soft HEAD~1
```

---

**Q20. How to set a remote origin in Git?**

```
git remote add origin <repo_url>
```

---

Bhai, agar tu bole to main **Part 2 – CI/CD & Jenkins (next 20 Q/A)** abhi bana ke de deta hoon, aur aise karke hum 100 complete karenge, fir final PDF bana ke de dunga.

Kya main ab **Part 2** shuru kar du?

Bhai chalo **Part 2 – CI/CD & Jenkins (20 Q/A)** banate hain 🚀
Ye section Jenkins, GitHub Actions, CI/CD basics, aur real-world examples cover karega.

---

## **Part 2 – CI/CD & Jenkins (20 Questions & Answers)**

**Q21. What is CI/CD?**
**A:**

* **CI (Continuous Integration):** Automatically build & test code whenever changes are pushed.
* **CD (Continuous Delivery/Deployment):** Automatically deliver or deploy changes to production.
  **Example:** Jenkins pipeline that builds a Node.js app after every commit.

---

**Q22. Benefits of CI/CD in DevOps?**
**A:**

* Faster delivery
* Reduced manual errors
* Early bug detection
* Automated deployments

---

**Q23. What is Jenkins?**
**A:** Jenkins is an open-source automation server used to build, test, and deploy applications through pipelines.

---

**Q24. Difference between Freestyle project and Pipeline in Jenkins?**
**A:**

* **Freestyle:** GUI-based job configuration, less flexible.
* **Pipeline:** Code-based (`Jenkinsfile`), reusable, version-controlled.

---

**Q25. How to install Jenkins on Ubuntu?**

```
sudo apt update
sudo apt install fontconfig openjdk-17-jre
wget -q -O - https://pkg.jenkins.io/debian/jenkins.io.key | sudo tee /usr/share/keyrings/jenkins-keyring.asc > /dev/null
echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] https://pkg.jenkins.io/debian binary/ | sudo tee /etc/apt/sources.list.d/jenkins.list > /dev/null
sudo apt update
sudo apt install jenkins
```

---

**Q26. Default port of Jenkins?**
**A:** `8080`

---

**Q27. Where is Jenkins home directory in Linux?**
**A:** `/var/lib/jenkins`

---

**Q28. What is a Jenkins Pipeline?**
**A:** A pipeline is a set of steps written in Groovy syntax that automates build, test, and deploy stages. Stored in a `Jenkinsfile`.

---

**Q29. Jenkins Declarative Pipeline Example**

```groovy
pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh 'npm install'
            }
        }
        stage('Test') {
            steps {
                sh 'npm test'
            }
        }
        stage('Deploy') {
            steps {
                sh 'echo Deploying Application...'
            }
        }
    }
}
```

---

**Q30. Difference between Declarative and Scripted Pipelines?**
**A:**

* **Declarative:** Simpler, structured syntax (`pipeline { }`).
* **Scripted:** More flexible, written in Groovy script.

---

**Q31. How to integrate GitHub with Jenkins?**
**A:**

1. Install "Git" plugin in Jenkins.
2. Add GitHub repo URL in job configuration.
3. Use Webhook in GitHub to trigger builds automatically.

---

**Q32. What is a Jenkins Agent/Node?**
**A:**
A machine connected to Jenkins that executes jobs. Master coordinates; agents run builds.

---

**Q33. How to secure Jenkins?**
**A:**

* Enable authentication & authorization.
* Use HTTPS.
* Limit plugin usage.
* Keep Jenkins updated.

---

**Q34. How to store sensitive credentials in Jenkins?**
**A:**
Use **Jenkins Credentials Plugin** and access them via `credentialsId` in pipelines.

---

**Q35. How to trigger Jenkins build automatically on Git push?**
**A:**

* Configure GitHub Webhook: `http://<jenkins-server>/github-webhook/`
* Enable "GitHub hook trigger for GITScm polling".

---

**Q36. What is Blue Ocean in Jenkins?**
**A:**
A modern UI for Jenkins pipelines with visual stages & real-time logs.

---

**Q37. How to run a specific stage only in Jenkins?**
**A:**
Use `when` condition in pipeline:

```groovy
when { branch 'main' }
```

---

**Q38. How to retry a failed Jenkins step?**

```groovy
retry(3) {
    sh 'npm install'
}
```

---

**Q39. Difference between Jenkins and GitHub Actions?**
**A:**

* **Jenkins:** Self-hosted, highly customizable.
* **GitHub Actions:** Integrated with GitHub, cloud-based, easier setup.

---

**Q40. Common Jenkins interview question scenario**
**Q:** You have a Node.js project that must run `npm install`, `npm test`, and deploy to AWS EC2. How will you design a Jenkins pipeline?
**A:**

* Create `Jenkinsfile` with Build, Test, Deploy stages.
* Use SSH to deploy to EC2.
* Configure credentials in Jenkins for AWS access.

---

Bhai, agar tu bole to main ab **Part 3 – Docker & Kubernetes (20 Q/A)** likh deta hoon, phir hum 60 pe pahunch jayenge.

Kya main **Part 3** shuru karu?
Bhai chalo **Part 3 – Docker & Kubernetes (20 Q/A)** likh dete hain 🚀
Ye section containerization, orchestration, aur real-world DevOps use cases cover karega.

---

## **Part 3 – Docker & Kubernetes (20 Questions & Answers)**

**Q41. What is Docker?**
**A:**
Docker is a containerization platform that packages applications and their dependencies into containers, making them portable and consistent across environments.

---

**Q42. Difference between VM and Docker Container?**
**A:**

| Feature     | VM              | Docker Container      |
| ----------- | --------------- | --------------------- |
| OS Overhead | Full OS per VM  | Shares Host OS Kernel |
| Boot Time   | Minutes         | Seconds               |
| Size        | GBs             | MBs                   |
| Performance | Slightly slower | Near-native           |

---

**Q43. Common Docker commands?**

```
docker --version
docker pull <image>
docker build -t myapp .
docker run -d -p 8080:80 myapp
docker ps
docker stop <container_id>
docker rm <container_id>
```

---

**Q44. What is Dockerfile?**
**A:**
A text file containing instructions to build a Docker image.
Example:

```dockerfile
FROM node:16
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
CMD ["npm", "start"]
```

---

**Q45. What is Docker Compose?**
**A:**
A tool for defining and running multi-container applications using a `docker-compose.yml` file.

---

**Q46. Example `docker-compose.yml`**

```yaml
version: '3'
services:
  web:
    build: .
    ports:
      - "5000:5000"
  redis:
    image: redis
```

---

**Q47. How to persist data in Docker?**
**A:**
Use **volumes**:

```
docker run -v myvolume:/data myapp
```

---

**Q48. What is Kubernetes?**
**A:**
Kubernetes (K8s) is an open-source container orchestration platform to automate deployment, scaling, and management of containerized applications.

---

**Q49. Main Kubernetes components?**
**A:**

* **Master Node:** API Server, Controller Manager, Scheduler, etcd
* **Worker Node:** Kubelet, Kube-proxy, Container Runtime

---

**Q50. What is a Pod in Kubernetes?**
**A:**
Smallest deployable unit in K8s, which can contain one or more containers.

---

**Q51. YAML example of a Pod**

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: mypod
spec:
  containers:
    - name: nginx
      image: nginx
      ports:
        - containerPort: 80
```

---

**Q52. What is a Deployment in Kubernetes?**
**A:**
A higher-level object to manage pods with rolling updates and rollback features.

---

**Q53. Example Deployment YAML**

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: nginx-deployment
spec:
  replicas: 3
  selector:
    matchLabels:
      app: nginx
  template:
    metadata:
      labels:
        app: nginx
    spec:
      containers:
        - name: nginx
          image: nginx:latest
          ports:
            - containerPort: 80
```

---

**Q54. What is a Service in Kubernetes?**
**A:**
An abstraction to expose applications running in Pods to other services or the outside world. Types: ClusterIP, NodePort, LoadBalancer.

---

**Q55. What is Ingress in Kubernetes?**
**A:**
An API object to manage external access to services, usually HTTP.

---

**Q56. How to scale Pods in Kubernetes?**
**A:**

```
kubectl scale deployment nginx-deployment --replicas=5
```

---

**Q57. What is the difference between ConfigMap and Secret in Kubernetes?**
**A:**

* **ConfigMap:** Stores non-sensitive configuration data.
* **Secret:** Stores sensitive data (base64 encoded).

---

**Q58. How to check logs of a Pod?**

```
kubectl logs <pod_name>
```

---

**Q59. What is a StatefulSet in Kubernetes?**
**A:**
A controller for managing stateful applications that require persistent identity and storage.

---

**Q60. How to update a container image in Kubernetes?**

```
kubectl set image deployment/nginx-deployment nginx=nginx:latest
```

---

Bhai ab agar bole to main **Part 4 – AWS Cloud (20 Q/A)** likh deta hoon jisme S3, EC2, IAM, RDS, networking sab cover karenge.
Kya main **AWS wala part 4** start karu?
Bhai chalo **Part 4 – AWS Cloud (20 Q/A)** likh dete hain ☁️
Ye section AWS ke core services, networking, aur DevOps me unka use cover karega.

---

## **Part 4 – AWS Cloud (20 Questions & Answers)**

**Q61. What is AWS?**
**A:**
AWS (Amazon Web Services) is a cloud computing platform offering over 200 services like compute, storage, networking, databases, AI, etc., on a pay-as-you-go model.

---

**Q62. What are AWS global infrastructure components?**
**A:**

* **Regions** – Geographical areas (e.g., us-east-1)
* **Availability Zones (AZs)** – Multiple data centers within a region
* **Edge Locations** – Used for caching in CloudFront

---

**Q63. What is EC2 in AWS?**
**A:**
Elastic Compute Cloud – Virtual servers in the cloud.
Example to launch:

```
aws ec2 run-instances --image-id ami-12345 --instance-type t2.micro
```

---

**Q64. EC2 Instance types?**
**A:**

* **General Purpose:** t2, t3
* **Compute Optimized:** c5, c6g
* **Memory Optimized:** r5, x1
* **Storage Optimized:** i3, d2
* **Accelerated Computing:** p3, g4

---

**Q65. What is S3?**
**A:**
Simple Storage Service – Object storage with 99.999999999% durability.
Use cases: backups, static website hosting, media storage.

---

**Q66. S3 storage classes?**
**A:**

* Standard
* Standard-IA (Infrequent Access)
* One Zone-IA
* Glacier / Glacier Deep Archive

---

**Q67. What is IAM?**
**A:**
Identity and Access Management – Controls who can access AWS resources.

---

**Q68. IAM Best Practices?**

* Use least privilege
* Enable MFA
* Use IAM roles instead of access keys
* Rotate credentials regularly

---

**Q69. What is VPC?**
**A:**
Virtual Private Cloud – A logically isolated network in AWS. You can define subnets, route tables, internet gateways, etc.

---

**Q70. VPC components?**
**A:**

* Subnets (Public/Private)
* Route Tables
* Internet Gateway
* NAT Gateway
* Security Groups
* NACLs

---

**Q71. What is RDS?**
**A:**
Relational Database Service – Managed database service supporting MySQL, PostgreSQL, MariaDB, Oracle, and SQL Server.

---

**Q72. Difference between RDS and Aurora?**
**A:**
Aurora is a MySQL/PostgreSQL-compatible database built for the cloud with better performance and auto-scaling storage.

---

**Q73. What is CloudFormation?**
**A:**
Infrastructure as Code (IaC) service to define AWS resources in YAML/JSON templates.

---

**Q74. What is Auto Scaling?**
**A:**
Automatically adjusts the number of EC2 instances based on demand.

---

**Q75. Difference between Security Groups and NACLs?**
**A:**

| Security Groups  | NACLs            |
| ---------------- | ---------------- |
| Stateful         | Stateless        |
| Instance level   | Subnet level     |
| Allow rules only | Allow/Deny rules |

---

**Q76. What is CloudWatch?**
**A:**
Monitoring and observability service for AWS resources and applications.

---

**Q77. What is Route 53?**
**A:**
AWS's scalable DNS service. Supports domain registration, DNS routing, and health checks.

---

**Q78. What is AWS Lambda?**
**A:**
A serverless compute service to run code without managing servers. Triggered by events (S3, API Gateway, CloudWatch).

---

**Q79. How to host a static website on S3?**
**A:**

* Create an S3 bucket
* Enable static website hosting
* Upload files
* Set bucket policy for public read access

---

**Q80. Difference between ELB types?**
**A:**

* **Application Load Balancer (ALB):** Layer 7, HTTP/HTTPS
* **Network Load Balancer (NLB):** Layer 4, TCP/UDP
* **Gateway Load Balancer (GLB):** For security appliances

---

Bhai ab agar bole to main **Part 5 – DevOps Tools & CI/CD (20 Q/A)** bana deta hoon jisme Jenkins, Terraform, Ansible, Git, monitoring sab cover karenge.
Kya main **Part 5** likhu?
Bhai chalo **Part 5 – DevOps Tools & CI/CD (20 Q/A)** banate hain jisme Jenkins, Terraform, Ansible, Git, Docker, Kubernetes, Monitoring sab ka detail Q\&A hoga.

---

## **Part 5 – DevOps Tools & CI/CD (20 Questions & Answers)**

**Q81. What is DevOps?**
**A:**
DevOps is a set of practices combining software development (Dev) and IT operations (Ops) to shorten the development lifecycle while delivering high-quality software through automation, collaboration, and continuous delivery.

---

**Q82. Difference between Continuous Integration, Continuous Delivery, and Continuous Deployment?**
**A:**

* **CI:** Frequent merging of code into a shared repository, followed by automated build & test.
* **CD (Delivery):** Code is always ready for deployment after CI tests pass (manual approval needed).
* **CD (Deployment):** Fully automated release to production without manual approval.

---

**Q83. What is Jenkins?**
**A:**
Jenkins is an open-source CI/CD automation server that supports building, testing, and deploying code using pipelines.

---

**Q84. Types of Jenkins Pipelines?**
**A:**

* Declarative Pipeline (structured syntax)
* Scripted Pipeline (flexible Groovy script)

---

**Q85. What is a Jenkinsfile?**
**A:**
A text file containing the pipeline script that defines stages for build, test, and deployment.

Example:

```groovy
pipeline {
  agent any
  stages {
    stage('Build') { steps { sh 'npm install' } }
    stage('Test') { steps { sh 'npm test' } }
  }
}
```

---

**Q86. What is Terraform?**
**A:**
Terraform is an Infrastructure as Code (IaC) tool to provision cloud resources using declarative configuration files.

---

**Q87. Terraform lifecycle commands?**

* `terraform init` → Initialize
* `terraform plan` → Preview changes
* `terraform apply` → Create/modify resources
* `terraform destroy` → Delete resources

---

**Q88. What is Ansible?**
**A:**
Ansible is a configuration management & orchestration tool that uses YAML playbooks to automate server configuration and application deployment.

---

**Q89. Difference between Ansible, Puppet, and Chef?**
**A:**

* **Ansible:** Agentless, YAML-based, easy to learn
* **Puppet:** Agent-based, declarative
* **Chef:** Agent-based, Ruby DSL

---

**Q90. What is Git?**
**A:**
Git is a distributed version control system for tracking code changes.

---

**Q91. Common Git commands?**

* `git clone <url>`
* `git status`
* `git add .`
* `git commit -m "message"`
* `git push origin main`
* `git pull`

---

**Q92. What is Docker?**
**A:**
Docker is a containerization platform that packages applications and dependencies into containers for portability and consistency.

---

**Q93. Difference between VM and Docker container?**
**A:**

| VM                 | Docker            |
| ------------------ | ----------------- |
| Runs on hypervisor | Runs on OS kernel |
| Heavyweight        | Lightweight       |
| Boots in minutes   | Boots in seconds  |

---

**Q94. What is Kubernetes?**
**A:**
Kubernetes (K8s) is an open-source container orchestration platform to manage containerized applications at scale.

---

**Q95. Key Kubernetes components?**

* **Pod** – Smallest deployable unit
* **Node** – Worker machine
* **Deployment** – Manages replica sets
* **Service** – Exposes application
* **Ingress** – HTTP/HTTPS routing

---

**Q96. What is Helm in Kubernetes?**
**A:**
Helm is a package manager for Kubernetes that deploys applications using charts (predefined templates).

---

**Q97. What is Prometheus?**
**A:**
Prometheus is an open-source monitoring system for collecting and querying metrics.

---

**Q98. What is Grafana?**
**A:**
Grafana is an open-source visualization tool that integrates with Prometheus, ElasticSearch, etc., to create dashboards.

---

**Q99. How to integrate Jenkins with Docker?**
**A:**

* Install Docker on Jenkins server
* Add Jenkins user to Docker group
* Use Docker plugin or CLI in pipeline to build & push images

---

**Q100. What are the benefits of DevOps?**
**A:**

* Faster delivery of software
* Improved collaboration between teams
* Reduced downtime with automated deployment & rollback
* Scalability and better resource utilization

---


make pdf of this dada 





