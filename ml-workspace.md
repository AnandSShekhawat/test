# Azure Machine Learning

It is a cloud-based platform on Microsoft Azure used to build, train, deploy, and manage machine learning models at scale.

It provides tools for data scientists, ML engineers, and developers to manage the entire machine learning lifecycle (MLOps) in one place.

>Azure Machine Learning is a cloud service that helps teams build, train, deploy, and monitor machine learning models using scalable infrastructure and integrated tools.

### What You Can Do with Azure Machine Learning

Azure ML supports the full ML lifecycle.
| Stage               | What Azure ML Provides                     |
| ------------------- | ------------------------------------------ |
| Data preparation    | Data storage and dataset management        |
| Model training      | Training models using scalable compute     |
| Experiment tracking | Track experiments, parameters, and metrics |
| Model management    | Register and version models                |
| Deployment          | Deploy models as APIs or batch jobs        |
| Monitoring          | Monitor model performance in production    |


## Main Components of Azure Machine Learning

![](./media/ml1.png)

The screenshot shows the **left navigation pane of Azure Machine Learning inside Microsoft Foundry**. These sections help manage different parts of the **machine learning lifecycle (data → training → deployment → management)**.

Below is a **simple explanation of each item with an interview-friendly description**.

### Default Directory

**What it is:**
Represents the **Microsoft Entra ID tenant** you are currently using.

**Purpose:**
Shows the identity directory where your Azure resources and permissions are managed.

**Interview one-liner:**

> The directory represents the Azure tenant that manages authentication and access to ML resources.

### Workspaces

**What it is:**
The **central environment for ML development**.

**What it stores:**

* datasets
* experiments
* models
* compute resources
* pipelines

**Think of it as:**
A **project environment for machine learning work**.

**Interview one-liner:**

> An Azure ML workspace is the main container where all machine learning assets and experiments are managed.

### Feature Stores

**What it is:**
A **central repository for machine learning features**.

**Features = processed data used by ML models.**

Example:

```text
Raw data → cleaned features → ML model
```

**Why it is used**

* reuse features across models
* maintain consistency between training and inference

**Interview one-liner:**

> A Feature Store stores reusable ML features so they can be shared across models and pipelines.

### Hubs

**What it is:**
A **shared resource layer for multiple ML projects or teams**.

Hubs allow:

* shared compute
* shared connections
* governance policies
* resource management

**Example**

```text
Hub
 ├─ Project 1
 ├─ Project 2
 └─ Project 3
```

**Interview one-liner:**

> A Hub provides centralized management and shared resources for multiple AI projects.

### Registries

**What it is:**
A **central place to share ML assets across workspaces**.

Assets stored:

* models
* components
* environments

**Example**

```text
Model Registry
   ├─ churn-model v1
   ├─ churn-model v2
```

**Interview one-liner:**

> A registry allows sharing ML assets across multiple workspaces or teams.

![](./media/ml2.png)

## Shared Assets Section

These resources can be reused across ML pipelines.

### Components

**What it is:**
Reusable **steps in ML pipelines**.

Example pipeline:

```text
Data preparation
Model training
Model evaluation
Deployment
```

Each step can be saved as a **component**.

**Interview one-liner:**

> Components are reusable building blocks used in machine learning pipelines.

![](./media/ml3.png)

### Environments

**What it is:**
Defines the **runtime environment for ML jobs**.

Includes:

* Python version
* libraries
* dependencies

Example:

```text
Python 3.10
scikit-learn
pandas
tensorflow
```

**Interview one-liner:**

> An environment defines the software dependencies required to run ML training or inference.

![](./media/ml4.png)

### Models

**What it is:**
A **model registry inside the workspace**.

Stores:

* trained models
* model versions
* metadata

Example:

```text
fraud-detection-model
  ├ v1
  ├ v2
```

**Interview one-liner:**

> The model registry stores trained ML models and their versions for deployment and reuse.

![](./media/ml5.png)

### Data

**What it is:**
Registered datasets used for training or inference.

Examples:

* CSV datasets
* image datasets
* parquet files
* data lake datasets

**Interview one-liner:**

> The data section manages datasets used for machine learning experiments and training.

![](./media/ml6.png)

## Admin

Administrative configuration of ML resources.

### Quota

**What it is:**
Defines **resource limits for compute usage**.

Examples:

* number of GPUs
* CPU cores
* cluster size

**Why it matters**

Prevents excessive resource consumption.

**Interview one-liner:**

> Quotas define limits on compute resources such as CPUs, GPUs, and clusters used in Azure ML.

### Simple Architecture View

```text
Azure ML
   │
   ├─ Workspaces → ML project environments
   │
   ├─ Feature Store → reusable ML features
   │
   ├─ Registries → shared models/assets
   │
   └─ Shared assets
        ├─ Components → pipeline steps
        ├─ Environments → dependencies
        ├─ Models → trained models
        └─ Data → datasets
```

### Quick Interview Cheat Sheet

| Component     | Purpose                           |
| ------------- | --------------------------------- |
| Workspace     | Main ML project container         |
| Feature Store | Store reusable ML features        |
| Hub           | Shared resources across projects  |
| Registry      | Share ML assets across workspaces |
| Components    | Reusable pipeline steps           |
| Environments  | Software dependencies             |
| Models        | Model version registry            |
| Data          | Registered datasets               |
| Quota         | Compute resource limits           |

---

✅ **One-line summary**

> Azure Machine Learning organizes the ML lifecycle through workspaces, shared assets, registries, and compute management to build, train, and deploy machine learning models efficiently.

## Create Workspace 

### Basic 

| Field                    | What it is                                                     | Purpose / Why it is needed                                                                 |
| ------------------------ | -------------------------------------------------------------- | ------------------------------------------------------------------------------------------ |
| **Subscription**         | The Azure subscription where the workspace will be created.    | Determines billing and resource ownership for the ML workspace.                            |
| **Resource Group**       | A logical container that holds related Azure resources.        | Helps organize and manage resources such as the ML workspace, storage, and compute.        |
| **Name**                 | Unique name of the Azure Machine Learning workspace.           | Identifies the ML workspace where experiments, models, and pipelines are managed.          |
| **Region**               | The Azure datacenter location where the workspace is deployed. | Determines where the ML resources and compute infrastructure will run.                     |
| **Storage Account**      | Azure storage associated with the workspace.                   | Stores datasets, experiment outputs, logs, and model artifacts.                            |
| **Key Vault**            | Secure Azure service for managing secrets and credentials.     | Stores sensitive information such as API keys, passwords, and connection strings securely. |
| **Application Insights** | Azure monitoring and logging service.                          | Tracks performance, logs, and telemetry for ML experiments and deployed models.            |
| **Container Registry**   | Azure Container Registry used for storing Docker images.       | Stores container images used for training environments and model deployments.              |

### Simple Architecture View

```text
Azure ML Workspace
      │
      ├── Storage Account → stores datasets & model outputs
      ├── Key Vault → stores secrets & credentials
      ├── Application Insights → monitoring & logs
      └── Container Registry → Docker images for training/deployment
```

> An **Azure Machine Learning workspace** is the central environment for ML development and automatically integrates services like **Storage, Key Vault, Application Insights, and Container Registry** to support training, deployment, and monitoring of machine learning models.

![](./media/ml7.png)

### Inbound Access

Below is a **concise tabular explanation of the “Inbound Access” tab** when creating a workspace in Azure Machine Learning.

| Field                                | What it is                                                                                                                 | Purpose / Why it is needed                                                                             |
| ------------------------------------ | -------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------ |
| **Public network access**            | Controls whether the workspace can be accessed over the public internet. Options include **Disabled** or **All networks**. | Used to restrict or allow internet access to the workspace for security purposes.                      |
| **Disabled (Public network access)** | Blocks all public internet traffic to the workspace. Access is only allowed through private endpoints.                     | Used in highly secure or enterprise environments where internet access must be restricted.             |
| **All networks**                     | Allows the workspace to be accessed from any network over the internet.                                                    | Commonly used in labs, development environments, or when open access is acceptable.                    |
| **Workspace inbound access**         | Defines private network access to the workspace using **Private Endpoints**.                                               | Enables secure communication between Azure resources and the ML workspace within a private network.    |
| **Private Endpoint (Add)**           | Allows creating a private endpoint connected to a specific virtual network and subnet.                                     | Ensures traffic to the workspace flows through Azure's private network instead of the public internet. |
| **Subnet**                           | A segment of a virtual network used for private endpoint connections.                                                      | Controls network isolation and traffic routing within the VNet.                                        |
| **Private DNS Zone**                 | Azure DNS service that maps the private endpoint to the workspace’s private IP address.                                    | Ensures internal resources resolve the workspace hostname to its private IP.                           |

> The **Inbound Access configuration in Azure Machine Learning** controls how clients connect to the workspace, allowing either **public internet access or secure private network access through private endpoints**.


![](./media/ml8.png)

### Outbound 


| Option                           | What it is                                                                                                                   | Purpose / When to use                                                                               |
| -------------------------------- | ---------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------- |
| **Public**                       | Allows compute resources in the workspace to access public internet resources without restrictions.                          | Suitable for development, testing, or labs where unrestricted internet access is acceptable.        |
| **Allow Internet Outbound**      | Allows compute resources to access both public internet resources and private resources within virtual networks.             | Used when workloads need to access external services and internal private resources simultaneously. |
| **Allow Only Approved Outbound** | Restricts outbound network traffic so compute resources can only communicate with explicitly approved services or endpoints. | Used in highly secure enterprise environments where strict network control is required.             |

### Concept

Outbound access defines **how Azure Machine Learning compute resources communicate with external services** such as:

* Azure Storage
* Container registries
* external APIs
* internet resources

### Simple Architecture View

```text
Azure ML Workspace
        │
        ├─ Public → unrestricted internet access
        │
        ├─ Allow Internet Outbound → internet + private network access
        │
        └─ Allow Only Approved Outbound → restricted access to approved services only
```


> **Outbound Access in Azure Machine Learning controls how workspace compute resources communicate with external services, allowing either unrestricted internet access or restricted communication with approved endpoints for enhanced security.**

![](./media/ml9.png)

### Identity 


| Field                              | What it is                                                                                                                    | Purpose / When to use                                                                                      |
| ---------------------------------- | ----------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------- |
| **Managed Identity**               | An Azure feature that allows services to authenticate securely to other Azure services without storing credentials.           | Used so the ML workspace can securely access resources like Storage, Key Vault, or Container Registry.     |
| **System Assigned Identity**       | An identity automatically created and managed by Azure for the workspace. It is tied to the lifecycle of the workspace.       | Recommended for most scenarios where the workspace needs secure access to Azure resources.                 |
| **User Assigned Identity**         | A standalone identity created separately and then assigned to one or more Azure resources.                                    | Used when multiple services need to share the same identity or permissions.                                |
| **Storage Account Access Type**    | Defines how the workspace accesses the associated storage account. Options include credential-based or identity-based access. | Controls authentication method when accessing datasets, logs, and model artifacts stored in Azure Storage. |
| **Credential-based Access**        | Uses stored credentials or keys to authenticate with the storage account.                                                     | Simpler setup but less secure compared to identity-based access.                                           |
| **Identity-based Access**          | Uses Azure managed identity and RBAC permissions to access storage securely.                                                  | Preferred in enterprise environments for improved security and credential management.                      |
| **High Business Impact Workspace** | A setting for workspaces that handle sensitive or regulated data.                                                             | Enables additional data protection controls and limits diagnostic data collection.                         |

### Concept

Identity settings control **how the Azure ML workspace securely interacts with other Azure services** without embedding secrets or credentials.

### Simple Architecture View

```text
Azure ML Workspace
        │
        ├── Managed Identity
        │       │
        │       ├── Access Storage Account
        │       ├── Access Key Vault
        │       └── Access Container Registry
```


> **The Identity configuration in Azure Machine Learning enables secure authentication between the workspace and other Azure services using managed identities instead of storing credentials.**

![](./media/ml10.png)