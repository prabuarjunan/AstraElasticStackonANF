# Run the ELK stack on AKS and Azure NetApp Files
## Introduction

How to run the ELK stack (Elasticsearch, Logstash, and Kibana) on Azure Kubernetes Service (AKS), a managed Kubernetes offering from Microsoft and backed by Azure NetApp files.
The solution is not only easy to create, configure, and organize a cluster of preconfigured virtual machines to run containerized applications. The Azure NetApp files systems also back the solution as persistent volume.

Azure NetApp Files is widely used as the underlying shared file-storage service in various scenarios. These include migration (lift and shift) of POSIX-compliant Linux and Windows applications, SAP HANA, databases, high-performance compute (HPC) infrastructure and apps, and enterprise web applications.


## Configuration 

As part of the configuration, you will implement the below steps
1.	Deploy your Kubernetes cluster using the Azure Kubernetes Service (AKS)
2.	Create a storage class defining your storage requirements like replication factor, snapshot policy, and performance profile
3.	Deploy Elasticsearch as a StatefulSet on Kubernetes
4.	Deploy Kibana replica set on Kubernetes
5.	Ingest data from Logstash into Elasticsearch, and visualize it through the Kibana dashboard
6.	Test failover by killing or cordoning nodes in your cluster
7.	Take a consistent application backup with 3DSnap and restore the Elasticsearch cluster.

## Setup a Azure Kubernetes Service (AKS)
This article assumes that you have an existing AKS cluster. If you need an AKS cluster, see the AKS quickstart <a href="https://azure.microsoft.com/en-us/global-infrastructure/services/?products=netapp&regions=all" title="About Me">using the Azure CLI</a>
 or <a href="https://azure.microsoft.com/en-us/global-infrastructure/services/?products=netapp&regions=all" title="About Me">using the Azure portal</a>.
<br />Important
<br />Your AKS cluster must also be <a href="https://azure.microsoft.com/en-us/global-infrastructure/services/?products=netapp&regions=all" title="About Me">in a region that supports Azure NetApp Files.</a>
<br />You also need the Azure CLI version 2.0.59 or later installed and configured. 
<br />Run az --version to find the version. If you need to install or upgrade, see <a href="https://docs.microsoft.com/en-us/cli/azure/install-azure-cli" title="About Me">Install Azure CLI</a> 
<br />It would be best to deploy a multiple node Kubernetes cluster based on the default AKS configuration.
![image](https://user-images.githubusercontent.com/31085459/151629080-1f0686e1-37ad-4f48-87ae-cf6f4840ff58.png)
