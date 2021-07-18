# Introduction

This document contains information on the test environments used to conduct testing for the EDB GlobalConnect Technology partners. The platforms where test resources are deployed typically fall under the following categories:

- Private (EDB) Cloud Platform: OpenStack
- Public Cloud Platform: AWS
- Partner Platform (Example): Nutanix

## Provisioning Test Resources


### On OpenStack

Virtual machines (and associated resources) are provisioned using the OpenStack console. The following steps show an example of how to create a VM instance.

**NOTE:** This is for informational purposes only. VMs with pre-installed products are available for testing and should be used whenever feasible.


1. Login to the OpenStack console (Rocky)

![](https://github.com/EnterpriseDB/tech-partner-program/blob/main/Lab%20Environment/images/Openstack%201.png)

2. On the dashboard click on Launch Instance button

![](https://github.com/EnterpriseDB/tech-partner-program/blob/main/Lab%20Environment/images/Openstack%202.png)

3. Fill in the details for:
Flavor (hardware configuration)
Instance Boot Source: where to create the instance from

![](https://github.com/EnterpriseDB/tech-partner-program/blob/main/Lab%20Environment/images/Openstack%203.png)

4. Create Keys (public and private) to login to the OpenStack instance. Copy and paste the contents of the public key and press import key pair button.

![](https://github.com/EnterpriseDB/tech-partner-program/blob/main/Lab%20Environment/images/Openstack%204.png)

5. Click on Launch button. Now the instance is displayed in the instances list.

![](https://github.com/EnterpriseDB/tech-partner-program/blob/main/Lab%20Environment/images/Openstack%205.png)

6. Assign a floating IP address which will be used to access this instance.

![](https://github.com/EnterpriseDB/tech-partner-program/blob/main/Lab%20Environment/images/Openstack%206.png)

### On AWS

Virtual machines (EC2 instances) are provisioned using the following methods:

- AWS console
- `tpaexec` utility (specific to EDB products)

**NOTE:** Once testing is completed, all provisioned resources should be released to avoid unnecessary charges.

#### Using AWS Console

1. Login to the [AWS console](https://275761063523.signin.aws.amazon.com/console)

![](https://github.com/EnterpriseDB/tech-partner-program/blob/main/Lab%20Environment/images/AWS%201.png)

2. Create EC2 instances by following the [AWS documentation](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/EC2_GetStarted.html).

#### Using `tpaexec` Utility

EC2 instances can be provisioned in order to deploy certain EDB products, such as BDR, using the `tpaexec` utility.

1. Install and configure the AWS CLI on a client machine to access the AWS environment by following the AWS documentation.

2. Install the `tpaexec` utility on the client machine using the TPAexec Installation Guide.

3. Provision the test resources:
    ```
    tpaexec provision <config-file>
    ```
	
See sample config-file for provisioning resources for BDR-Always-ON architecture using tpaexec.

For detailed information on how to use the tpaexec utility to provision resources on AWS, refer to the TPAexec documentation.

**NOTE:** All TPAexec related documentation requires EDB access credentials.

### On Partner Platform

Test resources on a partner platform are deployed per specific instructions for the platform, e.g., Nutanix.

## Installing Products

The following is the list of EDB products that may need to be installed for testing (list may grow). The products selected for testing vary according to the requirements of the partner.

[EDB Postgres Advanced](https://www.enterprisedb.com/docs/epas/latest/epas_guide/)

EDB Postgres Enterprise Manager (PEM)

EDB Failover Manager (EFM)

EDB Backup Recovery Manager (barman)

EDB Bi-Directional Replication (BDR)

Additionally, the following non-EDB products may need to be installed for testing depending on the partner:

Partner Product

Community Postgres


### On OpenStack

Follow these installation steps:

1. Copy ssh key (tpp-test.pem)to the client machine

2. Set appropriate permissions on the key file
    ```
    chmod 600 ./tpp-test.pem
    ```
3. Access the (CentOS7) VM via a ssh session using the provided key (tpp-test.pem):
    ```
    ssh -i ./tpp-test.pem centos@<host-address>
    ```
4. Install the product per the documentation provided above.

**NOTE:** This is for informational purposes only. VMs with pre-installed products are available for testing and should be used whenever feasible. Details provided in the Appendix section.


### On AWS

There are a few different installation methods depending on the product:

a. Manual installation by accessing the EC2 instance via ssh. Refer to the AWS documentation on how to access EC2 instances via ssh.

b. Install using the tpaexec utility (for EDB products only). Ensure the required test resources are already provisioned as outlined in the previous section.

```
tpaexec deploy <config-file>
```
	
See sample config-file for deploying BDR-Always-ON architecture using tpaexec.

For detailed information on how to use the tpaexec utility to deploy products on AWS, refer to the TPAexec documentation.

**NOTE:** All TPAexec related documentation requires EDB access credentials.

c. Install using provided AMI by following the AWS documentation.

### On Partner Platform

Details provided by partner.

## Testing Products

Specific EDB products are tested with the partner product per the requirements provided by the partner. The baseline tests for the products are listed in the test spreadsheet. Testing of additional features may be needed depending on the partner requirements.

### Sample Test Deployments

#### EDB Postgres Advanced and Tools

The following diagram shows EDB Postgres Advanced and associated tools deployed in a test environment:


#### EDB Postgres Extended with BDR-Always-ON
 
The following diagram shows the BDR-Always-ON architecture. For more details, refer to the BDR-Always-ON Architecture documentation.
 
**NOTE:** The documentation requires EDB access credentials.

