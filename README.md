---
page_type: sample
languages:
- python
products:
- azure
description: "This sample shows how to manage a load balancer using the Azure Resource Manager APIs for Python."
urlFragment: network-python-manage-loadbalancer
---

# Getting Started with Azure Resource Manager for load balancers in Python

This sample shows how to manage a load balancer using the Azure Resource Manager APIs for Python.

You can use a load balancer to provide high availability for your workloads in Azure. An Azure load balancer is a Layer-4 (TCP, UDP) type load balancer that distributes incoming traffic among healthy service instances in cloud services or virtual machines defined in a load balancer set.

For a detailed overview of Azure load balancers, see [Azure Load Balancer overview](https://azure.microsoft.com/documentation/articles/load-balancer-overview/).

![alt tag](./lb.JPG)

This sample deploys an internet-facing load balancer. It then creates and deploys two Azure virtual machines behind the load balancer. For a detailed overview of internet-facing load balancers, see [Internet-facing load balancer overview](https://azure.microsoft.com/documentation/articles/load-balancer-internet-overview/).

To deploy an internet-facing load balancer, you'll need to create and configure the following objects.

- Front end IP configuration - contains public IP addresses for incoming network traffic. 
- Back end address pool - contains network interfaces (NICs) for the virtual machines to receive network traffic from the load balancer. 
- Load balancing rules - contains rules mapping a public port on the load balancer to port in the back end address pool.
- Inbound NAT rules - contains rules mapping a public port on the load balancer to a port for a specific virtual machine in the back end address pool.
- Probes - contains health probes used to check availability of virtual machines instances in the back end address pool.

You can get more information about load balancer components with Azure resource manager at [Azure Resource Manager support for Load Balancer](https://azure.microsoft.com/documentation/articles/load-balancer-arm/).

## Tasks performed in this sample

The sample performs the following tasks to create the load balancer and the load-balanced virtual machines: 

1. Create a resource group
4. Create a public IP
5. Build the load balancer payload
  1. Build a front-end IP pool
  2. Build a back-end address pool
  3. Build a health probe
  4. Build a load balancer rule
  5. Build inbound NAT rule 1
  6. Build inbound NAT rule 2
6. Create the load balancer with the above payload
2. Create a virtual network (vnet)
3. Create a subnet
7. Create NIC 1
8. Create NIC 2
9. Find an Ubutnu VM image
10. Create an availability set
11. Create the first VM: Web1
12. Create the second VM: Web2
13. Delete the resource group and the resources created in the previous steps

## Run this sample

1. If you don't already have a Microsoft Azure subscription, you can register for a [free trial account](http://go.microsoft.com/fwlink/?LinkId=330212).

1. Install [Python](https://www.python.org/downloads/) if you haven't already.

2. We recommend using a [virtual environment](https://docs.python.org/3/tutorial/venv.html) to run this example, but it's not mandatory. You can initialize a virtual environment this way:

	    pip install virtualenv
	    virtualenv mytestenv
	    cd mytestenv
	    source bin/activate

3. Clone the sample repository.
    
	    git clone https://github.com/Azure-Samples/network-python-manage-loadbalancer.git    

4. Install the dependencies using pip.

	    cd network-python-manage-loadbalancer
	    pip install -r requirements.txt    

5. Create an Azure service principal, using 
[Azure CLI](http://azure.microsoft.com/documentation/articles/resource-group-authenticate-service-principal-cli/),
[PowerShell](http://azure.microsoft.com/documentation/articles/resource-group-authenticate-service-principal/)
or [Azure Portal](http://azure.microsoft.com/documentation/articles/resource-group-create-service-principal-portal/).

6. Export these environment variables into your current shell. 
    
	    export AZURE_TENANT_ID={your tenant ID}
	    export AZURE_CLIENT_ID={your client ID}
	    export AZURE_CLIENT_SECRET={your client secret}
	    export AZURE_SUBSCRIPTION_ID={your subscription ID}
    
7. Run the sample for public load balancer.
    
	    python example_public_load_balancer.py
   Or
   Run the sample for internal load balancer.
            
	    python example_internal_load_balancer.py
   
## More information

- [Azure SDK for Python](http://github.com/Azure/azure-sdk-for-python) 
