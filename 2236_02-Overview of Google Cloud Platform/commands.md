## Important GCP Commands

### gcloud Authentication

- **Authenticate with GCP**
  ```sh
  gcloud auth login
  ```
  This command is used to authenticate the gcloud CLI with Google Cloud.

### Project Management

- **List all GCP projects**

  ```sh
  gcloud projects list
  ```

  Lists all projects associated with your Google Cloud account.

- **Set the default project**
  ```sh
  gcloud config set project PROJECT_ID
  ```
  Sets the specified project as the default.

### Compute Engine

- **List Compute Engine instances**
  ```sh
  gcloud compute instances list
  ```
  Displays all virtual machine instances running in the project.

### IAM (Identity and Access Management)

- **Create a new service account**

  ```sh
  gcloud iam service-accounts create SERVICE_ACCOUNT_NAME \
      --description="User account for XYZ" \
      --display-name="XYZ Account"
  ```

  Creates a service account with a specific name and description.

- **Assign IAM role to a service account**
  ```sh
  gcloud projects add-iam-policy-binding PROJECT_ID \
      --member="serviceAccount:SERVICE_ACCOUNT_EMAIL" \
      --role="roles/ROLE_NAME"
  ```
  Assigns a role to a specific service account.

### Cloud Storage

- **Create a new storage bucket**

  ```sh
  gcloud storage buckets create gs://BUCKET_NAME \
      --project=PROJECT_ID \
      --location=us-central1 \
      --storage-class=STANDARD
  ```

  Creates a Cloud Storage bucket with specified parameters.

- **Upload a file to Cloud Storage**
  ```sh
  gsutil cp local-file.txt gs://BUCKET_NAME/
  ```
  Copies a file from local storage to a Cloud Storage bucket.

### Networking

- **Create a new VPC network**

  ```sh
  gcloud compute networks create my-vpc --subnet-mode=auto
  ```

  Creates a VPC network with automatic subnet creation.

- **Create a subnet within the VPC**
  ```sh
  gcloud compute networks subnets create my-subnet \
      --network=my-vpc \
      --region=us-central1 \
      --range=192.168.0.0/24
  ```
  Defines a subnet within a specified VPC.

### Cloud Logging and Monitoring

- **Enable monitoring and logging APIs**
  ```sh
  gcloud services enable monitoring.googleapis.com logging.googleapis.com
  ```
  Activates monitoring and logging APIs for tracking cloud resources.

### Kubernetes Engine (GKE)

- **Create a new GKE cluster**

  ```sh
  gcloud container clusters create my-cluster --zone us-central1-a
  ```

  Creates a Kubernetes cluster in the specified zone.

- **List available GKE clusters**
  ```sh
  gcloud container clusters list
  ```
  Displays all existing Kubernetes clusters in the project.

### Cloud Functions

- **Deploy a Cloud Function**
  ```sh
  gcloud functions deploy my-function \
      --runtime python39 \
      --trigger-http \
      --allow-unauthenticated
  ```
  Deploys a serverless function with HTTP trigger.

### Cloud SQL

- **List Cloud SQL instances**

  ```sh
  gcloud sql instances list
  ```

  Shows all existing Cloud SQL database instances.

- **Create a new Cloud SQL instance**
  ```sh
  gcloud sql instances create my-sql-instance \
      --database-version=MYSQL_8_0 \
      --tier=db-f1-micro \
      --region=us-central1
  ```
  Creates a Cloud SQL instance with MySQL 8.0 in the specified region.

### Billing and Cost Management

- **Check IAM permissions for a user**
  ```sh
  gcloud projects get-iam-policy PROJECT_ID \
      --flatten="bindings[].members" \
      --format="table(bindings.role, bindings.members)" \
      --filter="bindings.members:user:EMAIL"
  ```
  Retrieves IAM policy details for a specific user.

### Conclusion

These commands provide a basic foundation for managing Google Cloud resources effectively using the `gcloud` CLI. They cover authentication, project management, IAM, networking, Kubernetes, Cloud Functions, and Cloud SQL operations.
