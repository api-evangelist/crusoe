<!-- fetched 2026-10-13 from https://docs.crusoecloud.com/storage/object-storage/overview by sweep-shape-compat.py; text extracted from the provider's own page -->

Object storage overview | Crusoe Cloud Skip to main content 
 Use $5 in free credits to explore Serverless Inference and Serverless Fine-Tuning 
 Get started Managed AI Infrastructure Cloud Usage and billing Identity and security Developer resources API Crusoe Cloud
 v1 (Latest) 
 v1alpha5 
 Managed AI
 v1 (Latest) 
 Overview 
 Installing and configuring the CLI 
 Getting Started with Terraform 
 Creating a VM 
 Spin up your first GPU cluster 
 IaaS 
 Compute 
 Virtual Machines 
 Instance Templates 
 Images 
 Storage 
 Object Storage 
 Overview 
 Managing Object Storage API Keys 
 Managing Buckets 
 Using S3 Tools 
 Troubleshooting 
 Disks 
 Networking 
 VPC Network overview 
 VPC Networks 
 Firewall Rules 
 InfiniBand 
 Load Balancers 
 Interconnect locations 
 NVLink 
 Orchestration 
 Crusoe Managed Kubernetes (CMK) 
 Crusoe Managed Slurm 
 Container Registry 
 Overview 
 Quickstart with Docker 
 Managing Repositories 
 Managing Images 
 Pulling Images into a Kubernetes Cluster 
 CCR Token Rotation in Kubernetes 
 Observability 
 Command Center 
 Overview 
 Get started 
 Infrastructure and Topology Overview 
 Instance Health 
 Metrics 
 Logs 
 Telemetry Conduit 
 Diagnostics 
 Notifications 
 Notifications 
 IaaS 
 Storage 
 Object Storage 
 Overview 
 Copy page 
 On this page 
 Object storage overview
 Crusoe Cloud Object Storage provides high-performance, S3-compatible object storage designed for AI/ML workloads. Store and retrieve datasets, model checkpoints, training artifacts, and other unstructured data with the standard S3 format. It is ideal for petabyte-scale datasets and can be used to migrate data from other cloud providers to Crusoe.
 Key Features ​ 
 S3-Compatible API : Use existing S3 tools and libraries (boto3, s3cmd, rclone, aws s3 cli) without modification
 High Performance : Optimized for large file uploads and downloads common in ML workflows
 Regional Storage : Data stored in the same location as your VMs for low-latency access
 Versioning & Object Lock : Protect critical data from accidental deletion or modification
 Multipart Upload Support : Efficient handling of large files with automatic chunking
 Pre-Signed URL : Direct access to a private Objects without exposing your credentials
 Prerequisites ​ 
 Before using Object Storage, ensure the following:
 You have an active Crusoe Cloud Organization with Object Storage enabled. Contact your account team or Crusoe support if you do not see Object Storage in your Console.
 Your VMs are running in a location where the Object Storage bucket is created.
 Architecture ​ 
 Object Storage is a regional resource - buckets are created in specific locations and can only be accessed from VMs in the same location. This design ensures low-latency access and high throughput for data-intensive workloads.
 Object Storage Endpoints ​ 
 Each location has a dedicated Object Storage endpoint:
 https://object.<location>.crusoecloudcompute.com 
 For example:
 https://object.us-east1-a.crusoecloudcompute.com 
 https://object.us-southcentral1-a.crusoecloudcompute.com 
 Authentication ​ 
 Object Storage uses dedicated Object Storage API keys (access key and secret key pairs) for authentication. These are separate from your Crusoe Cloud API tokens and are managed through the Console or CLI. See Managing Object Storage API Keys for more information.
 Naming Rules ​ 
 Bucket Names ​ 
 Bucket names must:
 Be unique across a Crusoe Cloud region
 Be between 3 and 63 characters long
 Contain only lowercase letters, numbers, and hyphens
 Start and end with a letter or number
 Not contain consecutive hyphens
 Not be formatted as an IP address (e.g., 192.168.1.1)
 Object Storage Keys ​ 
 Object Storage uses dedicated AWS S3 style API keys (an access key and secret key pair) for authentication. These are separate from your Crusoe Cloud API tokens and are required for all Object Storage client operations. Each bucket user can have a maximum of 2 keys, similar to AWS S3 key restrictions. Object Storage access keys can only be viewed by the owner of the key.
 Getting Started ​ 
 Create an Object Storage API Key : Generate access credentials for Object Storage
 Create a Bucket : Set up an Object Storage bucket in your desired location
 Configure Your Object Storage Client : Point your tools to the Crusoe Object Storage endpoint
 Upload and Download Objects : Use standard S3 operations to manage your data
 See Managing Object Storage API Keys and Managing Buckets for detailed instructions.
 Supported S3 Features ​ 
 Crusoe Object Storage supports the following S3 features:
 Basic object operations (PUT, GET, DELETE, HEAD)
 Multipart uploads
 Bucket and object listing
 Bucket versioning
 Object locking (WORM - Write Once Read Many)
 Bucket tagging
 Object metadata
 Range requests (partial downloads)
 Presigned URLs
 Features not currently supported:
 Server-side encryption (SSE)
 Access Control Lists (ACLs) beyond bucket-level permissions
 Cross-region replication
 Lifecycle policies
 Event notifications
 Performance Characteristics ​ 
 Upload Speed : Optimized for large file uploads (64 MB+ objects recommended)
 Download Speed : High-throughput reads for training pipelines
 Multipart Upload : Automatic chunking for large files
 Concurrency : High concurrent request handling for distributed workloads
 For optimal performance:
 Use multipart uploads for files larger than 64 MB
 Increase concurrency settings in your S3 client
 Ensure your VM type has sufficient VPC network bandwidth
 Billing ​ 
 Object storage is priced at $0.06 per GiB per month, billed based on the average amount of data stored over the billing period.
 Pricing Unit ​ 
 Object Storage is priced per GiB per month. Storage usage is measured in binary gibibytes (GiB), where 1 GiB = 2 30 bytes (1,073,741,824 bytes). Similarly, 1 TiB = 2 40 bytes, or 1,024 GiB.
 Usage Calculation ​ 
 Object Storage usage is billed based on the amount of data stored in your object store, measured over time. Crusoe samples your Object Storage usage at regular intervals throughout each hour and computes the average usage (in GiB) for that hour. This average represents your consumption for that hour, expressed in GiB-Hours (GiB-Hr). Your total monthly usage is the sum of all hourly averages across the billing period. The monthly invoice reflects the total GiB-Hr consumed and the corresponding cost.
 For example, suppose your object store holds 100 GiB for the first hour and 150 GiB for the second hour. Your usage for those two hours is: (100 GiB × 1 hr) + (150 GiB × 1 hr) = 250 GiB-Hr. To estimate an equivalent monthly rate from a quoted $/GiB/month price, divide by the number of hours in the month (for example, 730 for a 30-day month).
 Billing Period ​ 
 Storage is billed monthly. There are no minimum storage duration requirements and no early deletion fees. You pay only for what you store, for as long as you store it.
 Restrictions ​ 
 Buckets are private by default and can only be accessed by the owner of the bucket.
 Object Storage endpoints are not reachable from the public internet.
 Only path style URLs are supported, no virtual hosted style URLs.
 Object Storage API keys cannot be rotated in place. Customers must create a new key and delete the old one.
 Storage tiering is not supported currently in Crusoe Cloud Object Storage
 Once versioning is enabled on a bucket, it cannot be disabled.
 Next Steps ​ 
 Managing Object Storage API Keys - Create and manage authentication credentials
 Managing Buckets - Create and configure storage buckets
 Using S3 Tools - Configure s3cmd, rclone, boto3, and other clients
 Troubleshooting - Common issues and solutions
 For VM-side connection latency, throughput, and reliability metrics for Object Storage traffic, see VM Telemetry .
 Previous
 Object Storage
 Next
 Managing Object Storage API Keys
 Key Features 
 Prerequisites 
 Architecture Object Storage Endpoints 
 Authentication 
 Naming Rules Bucket Names 
 Object Storage Keys 
 Getting Started 
 Supported S3 Features 
 Performance Characteristics 
 Billing Pricing Unit 
 Usage Calculation 
 Billing Period 
 Restrictions 
 Next Steps 
 Resources
 Cloud Status 
 Crusoe.ai 
 Cloud Console 
 Other
 Support 
 Trust Center 
 Terms of Use 
 Privacy Notice 
 2026 Crusoe, Inc. All rights reserved.
