# oci-arch-devops (devops_instance_group)

Rapid delivery of software is essential for efficiently running your applications in the cloud. Oracle DevOps service provides an end-to-end continuous deployment experience to developers. Oracle DevOps service includes deploying pipelines to automate your continuous software deployment process (CD) to Oracle Cloud Infrastructure (OCI) platforms: Container Engine for Kubernetes (OKE), Functions, and Compute instances.

For details of the architecture, see [_Build a Continuous Deployment Pipeline using Oracle Cloud Infrastructure DevOps service_](https://docs.oracle.com/en/solutions/build-pipeline-using-devops/index.html)

## Prerequisites

- Permission to `manage` the following types of resources in your Oracle Cloud Infrastructure tenancy: `vcns`, `internet-gateways`, `load-balancers`, `route-tables`, `security-lists`, `subnets`, and `instances`.

- Quota to create the following resources: 1 VCN, 3 subnets, 1 Internet Gateway, 1 NAT Gateway, 2 route rules, ...

If you don't have the required permissions and quota, contact your tenancy administrator. See [Policy Reference](https://docs.cloud.oracle.com/en-us/iaas/Content/Identity/Reference/policyreference.htm), [Service Limits](https://docs.cloud.oracle.com/en-us/iaas/Content/General/Concepts/servicelimits.htm), [Compartment Quotas](https://docs.cloud.oracle.com/iaas/Content/General/Concepts/resourcequotas.htm).

## Deploy Using the Terraform CLI

### Clone of the repo
Now, you'll want a local copy of this repo. You can make that with the commands:

    git clone https://github.com/oracle-quickstart/oci-arch-devops.git
    cd oci-arch-devops/devops_instance_group
    ls

### Prerequisites
First off, you'll need to do some pre-deploy setup.  That's all detailed [here](https://github.com/cloud-partners/oci-prerequisites).

Secondly, a sample `terraform.tfvars` file is provided in the repo. Please update the file with your tenancy details.

Alternatively, you can create a `terraform.tfvars` file and populate with the following information as well as any additional information for your deployment:

```
# Authentication
tenancy_ocid         = "<tenancy_ocid>"
user_ocid            = "<user_ocid>"
fingerprint          = "<finger_print>"
private_key_path     = "<pem_private_key_path>"

# SSH Keys
ssh_public_key  = "<public_ssh_key_path>"

# Region
region = "<oci_region>"

# Compartment
compartment_ocid = "<compartment_ocid>"

````

### Create the Resources
Run the following commands:

    terraform init
    terraform plan
    terraform apply

Note:
    In order to test the deployment, grab the public ip of the compute instance and paste it on the browser to see the application running.


### Destroy the Deployment
When you no longer need the deployment, you can run this command to destroy the resources:

    terraform destroy

## Architecture Diagram

![](./images/dev-ops-deployment-pipeline.png)
