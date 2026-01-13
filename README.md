# ☁️ Real-Time Weather Monitoring Dashboard on GCP

![GCP](https://img.shields.io/badge/Google_Cloud-4285F4?style=for-the-badge&logo=google-cloud&logoColor=white)
![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Flask](https://img.shields.io/badge/Flask-000000?style=for-the-badge&logo=flask&logoColor=white)
![Status](https://img.shields.io/badge/Status-Completed-success)

## 📖 Project Overview
This project is a cloud-native web application designed to provide accurate, real-time, and location-specific weather data. Deployed entirely on the **Google Cloud Platform (GCP)**, the system leverages a Service-Oriented Architecture (SOA) to ensure high availability, scalability, and security.

The dashboard allows users to search for cities globally and view current weather conditions along with a 24-hour temperature forecast.

## 🏗️ Architecture
The system follows a multi-tier architecture isolating the frontend and backend services for independent scaling.



![Architecture Diagram](https://github.com/user-attachments/assets/701b3b3a-d921-43c5-ac7e-a1f2d151628f)


### Key Components:
* []**Frontend:** A static responsive website (HTML, CSS, JS) hosted on **Cloud Storage** for low-latency global delivery.
* []**Backend:** A Python **Flask API** running on **Compute Engine** Virtual Machines (VMs)].
* []**Traffic Management:** A **Global External Application Load Balancer** (HTTPS) serves as the single entry point, handling SSL termination and routing traffic to the backend.
* [t]**Scalability:** The backend runs within a **Managed Instance Group (MIG)** across multiple zones (`us-central1-a`, `us-central1-b`) with auto-healing capabilities.
* **Database/External APIs:**
    * []**OpenStreetMap Nominatim API:** For geocoding city names to coordinates.
    * []**Open-Meteo API:** For retrieving real-time weather and forecast data.

## 🛠️ Tech Stack & Tools
| Category | Tools Used |
| :--- | :--- |
| **Cloud Provider** | Google Cloud Platform (GCP) |
| **Compute** | Compute Engine (GCE), Managed Instance Groups (MIG) |
| **Networking** | VPC, Cloud Load Balancing, Firewall Rules |
| **Storage** | Cloud Storage (GCS) |
| **Observability** | Cloud Monitoring, Cloud Logging |
| **Backend** | Python, Flask, Gunicorn, systemd |
| **Frontend** | HTML5, CSS3, JavaScript |

## 🚀 Key Features
* **High Availability:** Deployed across multiple zones; if one zone fails, the application remains operational.
* **Auto-Healing:** The Load Balancer performs health checks on the `/healthz` endpoint. Unhealthy instances are automatically replaced.
* **Security:**
    * **Custom VPC:** Backend resources are isolated in a private network (`cde-net`).
    * **Firewall Rules:** Inbound traffic to the backend is restricted to the Load Balancer's IP ranges only.
    * **HTTPS:** End-to-end encryption using SSL certificates.
* **Observability:** Integrated dashboards track CPU utilization, latency, and request rates with automated email alerts for high resource usage.

## 🔧 Setup & Implementation
1.  **Network Setup:** Created a custom VPC and configured firewall rules to allow internal traffic and Load Balancer health checks.
2.  **Backend Deployment:**
    * Created an Instance Template with a startup script to install Python, Flask, and Gunicorn.
    * Deployed a Regional Managed Instance Group (MIG) for auto-scaling.
3.  **Frontend Deployment:** Uploaded static assets to a public Cloud Storage bucket.
4.  **Load Balancing:** Configured a Global External Load Balancer to route `/api/*` requests to the MIG and all other traffic to Cloud Storage.

## Screenshots :
<img width="705" height="590" alt="image" src="https://github.com/user-attachments/assets/c5559892-3655-461c-b6d8-e086ad29af44" />
<img width="819" height="488" alt="image" src="https://github.com/user-attachments/assets/249c5569-cc77-4cb3-bc1d-9f27b9c4e035" />
<img width="691" height="645" alt="image" src="https://github.com/user-attachments/assets/cbd98bb4-7705-4f19-896c-527eea7f4ec5" />
<img width="557" height="778" alt="image" src="https://github.com/user-attachments/assets/6cfd8380-2c55-47e3-a7ff-d390d8c2fab8" />
<img width="696" height="681" alt="image" src="https://github.com/user-attachments/assets/70e9227b-1475-425a-96c2-c0587419cd62" />
<img width="672" height="659" alt="image" src="https://github.com/user-attachments/assets/dcff7b1a-32d0-4adb-87c1-c3c2546fe10e" />
<img width="739" height="729" alt="image" src="https://github.com/user-attachments/assets/b48b7bdf-c412-4700-bac2-13b493d85952" />

<img width="765" height="749" alt="image" src="https://github.com/user-attachments/assets/d9d38348-4af8-474d-a26e-cfa162ac8eac" />

<img width="1046" height="701" alt="image" src="https://github.com/user-attachments/assets/947e1d61-1fbe-4b6b-bae9-72da73fbbebc" />








## 📄 License
This project was developed as part of the Cloud Computing coursework at Albukhary International University.
