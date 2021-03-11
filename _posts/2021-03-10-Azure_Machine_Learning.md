# Azure Machine Learning

Azure Machine Learning is a cloud-based platform for building and operating machine learning solutions in Azure. It includes a wide range of features and capabilities that help data scientists prepare data, train models, publish predictive services, and monitor their usage. Most importantly, it helps data scientists increase their efficiency by automating many of the time-consuming tasks associated with training models; and it enables them to use cloud-based compute resources that scale effectively to handle large volumes of data while incurring costs only when actually used.

![azure ml](/images/01-01-what-is-azure-ml.jpg)


Built on the Microsoft Azure cloud platform, Azure Machine Learning enables you to manage:

Scalable on-demand compute for machine learning workloads.
Data storage and connectivity to ingest data from a wide range sources.
Machine learning workflow orchestration to automate model training, deployment, and management processes.
Model registration and management, so you can track multiple versions of models and the data on which they were trained.
Metrics and monitoring for training experiments, datasets, and published services.
Model deployment for real-time and batch inferencing.






## Azure MAchine Learning Workspace

To use Azure Machine Learning, you create a workspace in your Azure subscription. You can then use this workspace to manage data, compute resources, code, models, and other artifacts related to your machine learning workloads.

A workspace is a context for the experiments, data, compute targets, and other assets associated with a machine learning workload.

The assets in a workspace include:

- Compute targets for development, training, and deployment.
- Data for experimentation and model training.
- Notebooks containing shared code and documentation.
- Experiments, including run history with logged metrics and outputs.
- Pipelines that define orchestrated multi-step processes.
- Models that you have trained.

### Workspaces as Azure Resources

Workspaces are Azure resources, and as such they are defined within a resource group in an Azure subscription, along with other related Azure resources that are required to support the workspace.

![workspace](/images/azure_ml_01-02-workspace.png)

The Azure resources created alongside a workspace include:

- A storage account - used to store files used by the workspace as well as data for experiments and model training.
- An Application Insights instance, used to monitor predictive services in the workspace.
- An Azure Key Vault instance, used to manage secrets such as authentication keys and credentials used by the workspace.
- A container registry, created as-needed to manage containers for deployed models.

For each one of the resources listed above there are associated costs even is the workspace in not used. So you must delete the worspace id you do not want to consume your credits1.



## Compute Resources

There are four kinds of compute resource you can create:

- Compute Instances: Development workstations that data scientists can use to work with data and models.
- Compute Clusters: Scalable clusters of virtual machines for on-demand processing of experiment code.
- Inference Clusters: Deployment targets for predictive services that use your trained models.
- Attached Compute: Links to existing Azure compute resources, such as Virtual Machines or Azure Databricks clusters.

### Creating a Workspace

You can create a workspace in any of the following ways:

1. In the Microsoft Azure portal, create a new Machine Learning resource, specifying the subscription, resource group and workspace name.
2. Use the Azure Machine Learning Python SDK to run code that creates a workspace. 

For example, the following code creates a workspace named aml-workspace (assuming the Azure ML SDK for Python is installed and a valid subscription ID is specified):

```Python
from azureml.core import Workspace
    
    ws = Workspace.create(name='aml-workspace', 
                      subscription_id='123456-abc-123...',
                      resource_group='aml-resources',
                      create_resource_group=True,
                      location='eastus'
                     )
```

3. Use the Azure Command Line Interface (CLI) with the Azure Machine Learning CLI extension.

For example, you could use the following command (which assumes a resource group named aml-resources has already been created):

```Python
az ml workspace create -w 'aml-workspace' -g 'aml-resources'
```

## Azure Machine Learning studio 

Azure Machine Learning studio is a web-based tool for managing an Azure Machine Learning workspace.

![Azure Machine Learnign Studio](/images/azure_ml-01-03-aml-studio.jpg)

To use Azure Machine Learning studio, use a a web browser to navigate to [https://ml.azure.com](https://ml.azure.com) and sign in using credentials associated with your Azure subscription. You can then select the subscription and workspace you want to manage.

A previously released tool named Azure Machine Learning Studio provided a free service for drag and drop machine learning model development. The studio interface for the Azure Machine Learning service includes this capability in the designer tool, as well as other workspace asset management capabilities. The old tool still availale as "Azure Machine Learning Studio **Classic**".

Azure Machine Learning Studio Classic miss many features present in Azure Machine Learning Worspace, but there is 100% free service plan available.

## The Azure Machine Learning SDK

While graphical interfaces like Azure Machine Learning studio make it easy to create and manage machine learning assets, it is often advantageous to use a code-based approach to managing resources. 

Azure Machine Learning provides software development kits (SDKs) for Python and R, which you can use to create, manage, and use assets in an Azure Machine Learning workspace.

### Installing the Azure Machine Learning SDK for Python

You can install the Azure Machine Learning SDK for Python by using the pip package management utility.

```Python
pip install azureml-sdk[notebooks,automl,explain]
```

For more information about installing the Azure Machine Learning SDK for Python, see the [SDK documentation](https://aka.ms/AA70rq7).
