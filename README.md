# VProfile Project - Local Stack Setup

## 📌 Project Overview

The **VProfile Project** is a local multi-tier web application stack setup designed for DevOps practice and experimentation. This project forms a baseline for future DevOps automation, containerization, orchestration, and CI/CD pipelines.

## 🎯 Objectives

- Set up a web application stack locally using virtual machines.
- Understand the structure and interdependencies of a multi-service architecture.
- Gain hands-on experience with automation tools like **Vagrant** and **VirtualBox**.
- Prepare a repeatable and automated infrastructure setup for R&D and learning.

## 🚀 Why This Project?

1. **Baseline for Future Projects**:  
   The setup lays the groundwork for containerization (Docker), orchestration (Kubernetes), CI/CD pipelines (Jenkins, GitHub Actions), and infrastructure automation (Ansible, Terraform).

2. **Local Dev Environment for R&D**:  
   Enables a safe environment to test configuration changes, troubleshoot, and build confidence—without impacting production systems.

---

## 🧱 Architecture Overview

### 🌐 Web Application Stack Components

| Service      | Purpose                              |
|--------------|--------------------------------------|
| Nginx        | Acts as a load balancer              |
| Apache Tomcat| Hosts the Java web application       |
| RabbitMQ     | Message broker (dummy implementation)|
| Memcached    | Caching layer for database           |
| MySQL        | Relational database backend          |
| NFS (optional)| Shared storage support              |

The flow of user interaction:
- User accesses the app via the browser using the **Nginx (Load Balancer)** IP.
- Request is forwarded to **Tomcat**, which hosts the Java-based social networking app.
- Login info is checked against **MySQL**.
- Responses are cached via **Memcached**.
- **RabbitMQ** simulates asynchronous messaging (for practice).

---

## 🛠️ Tools & Technologies

- **Oracle VirtualBox** – Hypervisor to create virtual machines
- **Vagrant** – Automates VM provisioning
- **Git Bash** – Command-line tool and Git client
- **IDE** – Optional (e.g., VS Code, Sublime Text, Notepad++)

---

## 📐 Automated Infrastructure Design

```
[ Vagrant ] ---> [ VirtualBox ] ---> [ Multiple VMs ]
                        |
                        |-- nginx (Load Balancer)
                        |-- tomcat (App Server)
                        |-- mysql (Database)
                        |-- memcached (Caching)
                        |-- rabbitmq (Queue Broker)
```

---

## 🔁 Execution Flow

1. **Install Prerequisites**
   - Oracle VirtualBox
   - Vagrant
   - Git Bash

2. **Clone the Repository**
   ```bash
   git clone -b local https://github.com/yourusername/vprofile-project.git
   cd vprofile-project/vagrant
   ```

3. **Launch VMs**
   ```bash
   vagrant up
   ```

4. **Verify Machines**
   - Ensure all VMs are up and accessible
   - Validate IP communication between VMs

5. **Provision Services (Automatically or Manually)**
   - `MySQL` → `Memcached` → `RabbitMQ` → `Tomcat` → `Nginx`

6. **Deploy the Java Web Application**
   - Build using Maven
   - Deploy to Tomcat

7. **Access the App**
   - Open browser → Visit Nginx load balancer IP

---

## 🔍 Troubleshooting Tips

- Ensure virtualization is enabled in your BIOS.
- If `vagrant up` fails due to network issues, check VirtualBox network settings.
- Use `vagrant ssh <vm-name>` to access individual VM shells.
- Confirm service ports are open and firewall rules aren't blocking traffic.

---

## 📚 Learning Benefits

- Understand the lifecycle of a full-stack web application.
- Practice setting up services often used in production.
- Learn DevOps tools and techniques in a safe, repeatable environment.

---

## 📎 Notes

- This is a simplified local version. Future projects will include:
  - Domain name setup
  - TLS/SSL
  - Containerization using Docker
  - Orchestration via Kubernetes
  - CI/CD pipelines with Jenkins or GitHub Actions

---

## 👏 Contributing

Have suggestions or want to improve the setup? Feel free to fork the repo and submit a pull request!

---

## 📝 License

This project is licensed under the [MIT License](LICENSE).
