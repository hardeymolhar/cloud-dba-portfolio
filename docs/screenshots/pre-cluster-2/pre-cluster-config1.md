# 🧱 Baseline (Pre-Cluster) Configuration – Secondary SQL Server (Node 2)

## 1. Objective
Establish the baseline configuration of the **Secondary SQL Server** instance before enabling Windows Failover Clustering (WSFC) or Always On Availability Groups.  
Unlike the primary node, this server was **rebuilt from a cloned operating system image and verified to have no existing SQL Server or SSMS installations** prior to setup.  
This ensures parity, reproducibility, and alignment with the primary node before cluster deployment.

> The pre-existing cluster configuration for both nodes can be referenced using the link below 👇🏾  
> **Note:** The **Disaster Recovery (DR) Server** was cloned, verified clean, and prepared for a new SQL Server Enterprise 2019 installation to ensure a consistent and error-free cluster configuration.

---

## 2. Baseline Verification – Post-Clone Environment
Screenshots confirm that **no SQL Server components or SSMS installations** existed on the cloned DR server prior to configuration.  
This validated that the server environment was clean and suitable for a fresh SQL Server 2019 deployment.

### Verification Screenshots
![PowerShell Verification](screenshots/pre-cluster-2/sql-ssms-verification.png)  
*Figure 1: PowerShell output confirming no SQL Server or SSMS installations present.*

![No SQL Installation](screenshots/pre-cluster-2/no-sql-installed.png)  
*Figure 2: Control Panel → Programs and Features showing no SQL Server components installed.*

![No SSMS Present](screenshots/pre-cluster-2/no-ssms-present.png)  
*Figure 3: Windows search confirming no SSMS detected.*


> These verifications confirm a clean environment before performing the SQL Server Enterprise 2019 installation.  
> The following sections capture the validated baseline configuration prior to cluster feature installation.

---

## 3. Server Overview
| Parameter | Value |
|------------|--------|
| Hostname | FIN-INCOASS-D-RC |
| Domain | fidelitybank.ng |
| IP Address | 10.120.7.21 |
| Subnet | 10.120.7.0/24 |
| OS Version | Windows Server 2019 Standard |
| SQL Server | Not Installed |
| SSMS | Not Installed |

### Screenshots
![Server Properties](screenshots/pre-cluster-2/server-properties.png)  
*Figure 4: Hostname, domain membership, and OS configuration.*

![IP Configuration](screenshots/pre-cluster-2/ip-configuration.png)  
*Figure 5: Static IP configuration, DNS, and gateway settings.*

![Failover Clustering Not Installed](screenshots/pre-cluster-2/failover-clustering-not-installed.png)  
*Figure 6: Failover Clustering feature not yet installed, confirming baseline state.*

---

## 4. Storage Layout
| Drive | Purpose | File System | Capacity |
|--------|----------|-------------|-----------|
| C: | Operating System | NTFS | 100 GB |
| E: | Data Files | NTFS | 5 TB |
| F: | Transaction Logs | NTFS | 2.5 TB |
| G: | Backups | NTFS | 300 GB |
| H: | Archive | NTFS | 5 TB |

![Storage Layout](screenshots/pre-cluster-2/storage-layout.png)  
*Figure 7: Drive layout confirming separation for data, logs, and backups.*

---

## 5. Baseline Validation Summary
| Validation Item | Status | Comments |
|-----------------|---------|-----------|
| Domain Join | ✅ | Joined to fidelitybank.ng |
| Static IP Assigned | ✅ | 10.120.7.21 |
| Windows Failover Clustering Installed | ❌ | Not yet installed |
| SQL Server Installed | ❌ | Verified clean environment |
| SSMS Installed | ❌ | Verified clean environment |
| Drives Configured | ✅ | Storage structure verified |
| Network Connectivity | ✅ | DNS and reachability confirmed |
| Witness Configured | ❌ | To be added post-cluster |

---

## 6. Notes
> This document represents the verified **baseline configuration for the Secondary SQL Server (Node 2)** prior to any SQL or cluster installation.  
> It confirms that the node was cloned from a clean image, validated through PowerShell and system verification, and aligned with enterprise standards in preparation for cluster setup.

---

## 7. Next Steps
1. Install **SQL Server Enterprise 2019** and **SQL Server Management Studio (SSMS)**.  
2. Validate SQL installation and service account configuration.  
3. Install **Windows Failover Clustering** feature on both nodes.  
4. Validate inter-node connectivity and DNS resolution.  
5. Create and configure the **Windows Cluster**.  
6. Configure **File Share Witness** on DC01.  
7. Enable and validate **Always On Availability Groups** post-cluster creation.

---

📁 **Screenshot Source Folder:**  
`/docs/screenshots/pre-cluster-2/`
