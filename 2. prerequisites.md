# 2. Prerequisites  

Before setting up **Airflow and Airbyte** on a **GCP VM**, ensure that you have the **necessary tools, accounts, and a clear understanding of the architecture**.  

This section will guide you through **everything you need** before deployment.  

## Tools and Resources Required  

### Google Cloud Platform (GCP) Access  
- A **GCP account** with permissions to create and manage **Compute Engine resources**  
- **Billing enabled** on the GCP project  

### Local Development Environment  
A machine with the following installed:  
- **VS Code** (latest version recommended)  
- **Remote - SSH extension** for seamless development  
- **SSH client** (default on Linux/macOS, or PuTTY/OpenSSH on Windows)  

### Software Dependencies (for the VM)  
- **Python 3.7+** for running Airflow  
- **Docker** for deploying Airbyte  
- **SSH keys** for secure access to the VM  

### Networking  
- A **stable internet connection**  
- Ability to **connect to the GCP VM via SSH**  

## High-Level Architecture  

A structured approach ensures that **Airbyte and Airflow work together efficiently**  

### Airbyte  
- Responsible for **syncing data** from source to destination  
- Runs as a **Docker service** on the VM  
- Provides an **API endpoint** for triggering sync jobs  

### Airflow  
- Orchestrates **workflows** and **triggers Airbyte jobs via API calls**  
- Runs as a **Python-based service** with its own **scheduler and webserver**  

### Communication Flow  
- **Airflow triggers Airbyte syncs** using **HTTP API calls**  
- **Logs and configuration files** are stored **separately** for each service  

### VS Code Remote-SSH  
- Used for **editing configuration files**, **writing Airflow DAGs**, and **troubleshooting directly on the VM**  

## Firewall and Networking Requirements  

Configure firewall and networking settings to allow communication:  

| **Service**       | **Port** | **Purpose** |
|------------------|---------|-------------|
| **SSH**          | 22      | Remote access to the VM |
| **Airflow Web UI** | 8080    | Access to Airflow’s dashboard |
| **Airbyte Web UI** | 8000    | Manage Airbyte connections |

**Security Best Practices:**  
- **Block all unnecessary ports** to minimize attack surface  
- Ensure **only authorized users** have access to critical services  

## Permissions and Roles  

### On GCP  
- Use **IAM roles** for access control  
- Assign **Compute Admin** or a similar role to manage the VM  

### On the VM  
- Create **separate Linux users** for **Airflow (airflow) and Airbyte (airbyte)**  
- Follow **least-privilege principles**  
  - Each user should have **access only to the directories and files they need**  

## Preparation Checklist  

Before proceeding, ensure you have:  
A **GCP account and project** with **Compute Engine API enabled**  
**VS Code with Remote - SSH extension installed**  
An **SSH key pair** (public and private) generated locally  
A **clear understanding of the ports** used by **Airflow (8080) and Airbyte (8000)**  

With all prerequisites in place, the next section will cover **GCP VM setup**, including **creating the VM, configuring users, and securing SSH access**.  


