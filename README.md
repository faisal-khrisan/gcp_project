# ☁️ Real-Time Weather Monitoring Dashboard on GCP

![GCP](https://img.shields.io/badge/Google_Cloud-4285F4?style=for-the-badge&logo=google-cloud&logoColor=white)
![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Flask](https://img.shields.io/badge/Flask-000000?style=for-the-badge&logo=flask&logoColor=white)
![Status](https://img.shields.io/badge/Status-Completed-success)

## 📖 Project Overview
[cite_start]This project is a cloud-native web application designed to provide accurate, real-time, and location-specific weather data[cite: 24, 26]. [cite_start]Deployed entirely on the **Google Cloud Platform (GCP)**, the system leverages a Service-Oriented Architecture (SOA) to ensure high availability, scalability, and security.

[cite_start]The dashboard allows users to search for cities globally and view current weather conditions along with a 24-hour temperature forecast, visualized using Chart.js[cite: 327].

## 🏗️ Architecture
[cite_start]The system follows a multi-tier architecture isolating the frontend and backend services for independent scaling[cite: 35].



![Architecture Diagram](https://github.com/user-attachments/assets/701b3b3a-d921-43c5-ac7e-a1f2d151628f)
*(Note: Upload the image from the PDF/Screenshot to your repo and link it here)*

### Key Components:
* [cite_start]**Frontend:** A static responsive website (HTML, CSS, JS) hosted on **Cloud Storage** for low-latency global delivery[cite: 50, 324].
* [cite_start]**Backend:** A Python **Flask API** running on **Compute Engine** Virtual Machines (VMs)[cite: 67].
* [cite_start]**Traffic Management:** A **Global External Application Load Balancer** (HTTPS) serves as the single entry point, handling SSL termination and routing traffic to the backend[cite: 52, 71].
* [cite_start]**Scalability:** The backend runs within a **Managed Instance Group (MIG)** across multiple zones (`us-central1-a`, `us-central1-b`) with auto-healing capabilities[cite: 55, 68].
* **Database/External APIs:**
    * [cite_start]**OpenStreetMap Nominatim API:** For geocoding city names to coordinates.
    * [cite_start]**Open-Meteo API:** For retrieving real-time weather and forecast data.

## 🛠️ Tech Stack & Tools
| Category | Tools Used |
| :--- | :--- |
| **Cloud Provider** | Google Cloud Platform (GCP) |
| **Compute** | Compute Engine (GCE), Managed Instance Groups (MIG) |
| **Networking** | VPC, Cloud Load Balancing, Firewall Rules |
| **Storage** | Cloud Storage (GCS) |
| **Observability** | Cloud Monitoring, Cloud Logging |
| **Backend** | Python, Flask, Gunicorn, systemd |
| **Frontend** | HTML5, CSS3, JavaScript, Chart.js |

## 🚀 Key Features
* [cite_start]**High Availability:** Deployed across multiple zones; if one zone fails, the application remains operational[cite: 56].
* **Auto-Healing:** The Load Balancer performs health checks on the `/healthz` endpoint. [cite_start]Unhealthy instances are automatically replaced[cite: 57, 69].
* **Security:**
    * [cite_start]**Custom VPC:** Backend resources are isolated in a private network (`cde-net`)[cite: 75].
    * [cite_start]**Firewall Rules:** Inbound traffic to the backend is restricted to the Load Balancer's IP ranges only[cite: 59].
    * [cite_start]**HTTPS:** End-to-end encryption using SSL certificates[cite: 81].
* [cite_start]**Observability:** Integrated dashboards track CPU utilization, latency, and request rates with automated email alerts for high resource usage.

## 🔧 Setup & Implementation
1.  [cite_start]**Network Setup:** Created a custom VPC and configured firewall rules to allow internal traffic and Load Balancer health checks[cite: 183, 184].
2.  **Backend Deployment:**
    * [cite_start]Created an Instance Template with a startup script to install Python, Flask, and Gunicorn[cite: 221].
    * [cite_start]Deployed a Regional Managed Instance Group (MIG) for auto-scaling[cite: 243].
3.  [cite_start]**Frontend Deployment:** Uploaded static assets to a public Cloud Storage bucket[cite: 329].
4.  [cite_start]**Load Balancing:** Configured a Global External Load Balancer to route `/api/*` requests to the MIG and all other traffic to Cloud Storage[cite: 54].

## 📄 License
[cite_start]This project was developed as part of the Cloud Computing coursework at Albukhary International University[cite: 3].
