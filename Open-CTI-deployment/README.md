# OpenCTI Deployment

##  Ubuntu Server Deployment

I started the deployment by installing Ubuntu Server.

- **Operating System:** Ubuntu Server 24.04.5 LTS Live Server (AMD64)
- **Virtualization:** VMware
- **Initial RAM:** 6 GB
- **Initial Hard Disk:** 60 GB
- **Network:** NAT using the shared host address

After setting up the Ubuntu Server, I created a login username and password.

---

##  OpenCTI Installation

I had to troubleshoot the OpenCTI installation process.

I first created the Docker environment and subsequently ran the OpenCTI installation command on Docker. The installation procedure was generated from the official OpenCTI page.

While running the installation, the download of the OpenCTI Docker Compose services took a lot of time and affected my network performance.

The services I was able to get running included:

- OpenCTI
- Elasticsearch
- RabbitMQ
- Redis
- OTX Connector
- Other connectors and supporting services

Some of the services experienced failures during installation, and I realized that my VM was not able to handle all the downloads and services running at once.

Because of this, I started installing some of the services one by one instead of downloading and running everything at once.

After installing the services, I ran Docker Compose commands on the Ubuntu CLI to check their health status.

---

##  OpenCTI Data Ingestion

### Adding the AlienVault OTX Connector

I added the AlienVault OTX connector to ingest data into OpenCTI.

After configuring the connector, I logged into the OpenCTI interface and went to the **Integration** page.

There, I found information about the queues, including:

- The amount of data waiting to be ingested
- How much data was being processed
- How fast the data was moving through the process

I immediately noticed that the logs were piling up.

There was a large amount of data that RabbitMQ was yet to process, while AlienVault OTX continued to ingest additional logs.

---

##  Initial Data Ingestion Period

The AlienVault OTX connector was ingesting logs from the beginning of **January 2026** through **September 2026**.

The amount of data being ingested was too much for my home lab environment.

The large ingestion workload caused my PC to lag and also affected the performance of OpenCTI.

There was a significant backlog of data waiting to be processed by RabbitMQ while AlienVault OTX continued ingesting more data.

This was making RabbitMQ unhealthy.

---

##  Troubleshooting the Ingestion Workload

Because the ingestion workload was becoming too heavy and could potentially cause my PC to crash, I had to troubleshoot the issue.

I stopped AlienVault OTX from ingesting data for a while.

I also decided to change the timeframe of the log ingestion to the last **three months**.

After making this change, I enabled AlienVault OTX again, and it started ingesting data from the new timeframe.

However, my PC was still lagging, and OpenCTI was also experiencing performance issues.

There was still a large backlog of data that AlienVault OTX had already ingested but RabbitMQ had not yet processed.

---

##  Resource Adjustment

Because the workload was still high, I increased the resources allocated to my Ubuntu VM.

### Updated Resources

- **RAM:** Increased to 8 GB
- **Hard Disk:** Increased to 100 GB

The purpose of increasing the resources was to reduce the workload on the system and improve the performance of the OpenCTI environment.

After doing this, I noticed that my RabbitMQ process still became unhealthy whenever I enabled AlienVault OTX.

I therefore decided to temporarily turn off AlienVault OTX and allow RabbitMQ to finish processing the existing backlog.

After the backlog was processed, I planned to turn AlienVault OTX back on and monitor the ingestion process.

---

##  Data Ingestion Backlog

I kept the AlienVault OTX ingestion turned off while the existing backlog was being processed.

I then refreshed the ingestion of the three-month dataset.

The ingestion process took approximately **three days**.

The large amount of data and the processing time showed that the volume of intelligence being ingested had a significant effect on the resources available in my home lab.

---

##  OpenCTI Deployment Outcome

Through the deployment process, I was able to:

- Install Ubuntu Server as the OpenCTI host.
- Deploy OpenCTI using Docker.
- Set up the OpenCTI supporting services.
- Configure the AlienVault OTX connector.
- Configure other OpenCTI connectors and supporting services.
- Ingest threat intelligence data into OpenCTI.
- Monitor the ingestion process through the OpenCTI Integration page.
- Identify a large data-processing backlog.
- Troubleshoot performance issues.
- Increase the VM's RAM and storage.
- Control the ingestion workload by temporarily stopping AlienVault OTX.
- Allow the existing backlog to finish processing.
- Continue working with the OpenCTI environment after the ingestion workload was reduced.
