# Commands Reference

This document provides a comprehensive list of commands introduced in Chapter 3: “Creating and Configuring a GKE Cluster”. Each command is accompanied by a brief description to assist in understanding its purpose and usage.

Before creating a GKE cluster, ensure that the necessary Google Cloud services are enabled:

## Enable the Compute Engine API

```sh
gcloud services enable compute.googleapis.com
```

## Enable the Kubernetes Engine API

```sh
gcloud services enable container.googleapis.com
```

These commands activate the Compute Engine and Kubernetes Engine APIs, which are essential for managing GKE clusters.

## Creating a GKE Cluster via Command Line:

To create a new GKE cluster using the command line, Create a GKE cluster with specified parameters

```sh
gcloud container clusters create YOUR_CLUSTER_NAME \
 --region YOUR_CLUSTER_REGION \
 --num-nodes=1 \
 --machine-type=n1-standard-2
```

Replace YOUR_CLUSTER_NAME with your desired cluster name and YOUR_CLUSTER_REGION with your preferred region (e.g., us-central1). Adjust the --num-nodes and --machine-type flags as needed to fit your requirements.

## Authenticate and configure access to your GKE cluster

After creating your GKE cluster, you verify the cluster access and configure kubectl to interact with it:

```sh
gcloud container clusters get-credentials YOUR_CLUSTER_NAME --zone YOUR_CLUSTER_ZONE
```

Replace YOUR_CLUSTER_NAME and YOUR_CLUSTER_ZONE with your cluster’s specific name and zone. This command retrieves cluster credentials and sets up kubectl for cluster management.

## To verify the nodes in your cluster:

List all nodes in the GKE cluster

```sh
kubectl get nodes
```

This command displays the status of each node within your cluster.

## Creating a GKE Cluster Using Terraform

For infrastructure as code enthusiasts, here’s an example of how to create a GKE cluster using Terraform:

```tf
### main.tf

provider "google" {
    credentials = file("<PATH_TO_YOUR_GCP_SERVICE_ACCOUNT_KEY>")
    project = "<YOUR_GCP_PROJECT_ID>"
    region = "us-central1"
}

resource "google_container_cluster" "my_cluster" {
    name = "my-gke-cluster"
    location = "us-central1"

    node_pool {
        name = "default-pool"
        machine_type = "n1-standard-2"
        disk_size_gb = 100
        disk_type = "pd-standard"
        min_count = 1
        max_count = 3
    }

    master_auth {
        username = ""
        password = ""

        client_certificate_config {
            issue_client_certificate = false
        }
    }
}
```

Note: Replace <PATH_TO_YOUR_GCP_SERVICE_ACCOUNT_KEY> and <YOUR_GCP_PROJECT_ID> with your actual service account key path and project ID, respectively.

To initialize and apply this Terraform configuration:

1. Navigate to the directory containing your Terraform files.
2. Initialize the working directory:

```sh
terraform init
```

3. Preview the changes:

```sh
terraform plan
```

4. Apply the configuration:

```sh
terraform apply
```

Confirm with yes when prompted to create the GKE cluster.

This Terraform script sets up a GKE cluster with a single node pool. Customize parameters such as machine_type, disk_size_gb, and node counts to suit your specific needs.

Caution: Managing GKE clusters incurs costs. Ensure you understand the pricing details and remember to clean up resources when they are no longer needed to avoid unnecessary charges.

By following these commands and configurations, you can effectively create and manage a GKE cluster tailored to your requirements.
