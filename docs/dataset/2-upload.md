# Upload

!!! note "Prerequisites"
    This article requires that you understand how data is stored on SynDB, we recommend reading through the [overview article](0-overview.md) if you are uncertain.

Uploading to SynDB is a multistep process, and requires understanding of the SynDB dataset model.

## The process

### Preparation

We recommend you to follow the guide in the exact sequence provided. This ensures the instructions are followed effectively and idiomatically.

#### Terms and conditions
You must accept the terms and conditions before uploading data. The terms include:
- Statement that the data is not false or misleading
- Redistribution rights
- Data licensing agreement with the license of your choice, see [guide to pick license](../guides/choose_dataset_license.md); the default license is [ODC-BY](../guides/choose_dataset_license.md#open-data-commons-odc-licenses "Allows use with proper credit to the original creator, ensuring acknowledgment while enabling broad use.").

#### Data standardization
Your imaging metrics must be in dataframe or tabular data format like Excel, CSV, or (even better) parquet. The column names must be in the SynDB standardized format. You can find supported column names for each SynDB table in the [schema overview]({{ source.dataset.schema_list_url }} "Link to GitHub where the overview is versioned").

Raw files including meshes or SWL files, you can upload them as well. You have to place the absolute path to the file in your table file. The following are supported (this list is upto date):

- **Meshes** in `.glb` format, column name: `mesh_path`
- **SWC** files, `.swc`, column name: `swc_path`

You may request additional formats on the {{ discord.hyperlink }} channel.

### Login
Once you enter the upload page, you will be prompted to log in to your SynDB account if you are not already; furthermore, you must verify your academic status by logging in to you institution's account.

### The upload
You can upload data using the CLI or the GUI. You could mix the usage of both as well, define the dataset in the GUI and upload using the CLI. We recommend that you only use the GUI for the first time.

#### 1. Assign IDs, and correlate relations
Each SynDB unit requires a unique ID assigned before being uploaded to the platform. The GUI does this automatically, but not the CLI. When you have multiple SynDB tables under one dataset it is expected that these have some relations with each other.

!!! warning "Dataset integrity"
    As it may lead to undefined behaviour, it is disallowed to upload SynDB table data that are unrelated under the same dataset!

    Meaning that you cannot upload a table of neurons and a table of synapses under the same dataset unless each synapse has a relation to a neuron from the respective table of neurons.

##### GUI
The GUI will automatically assign UUIDs to each SynDB unit. The relations are correlated based on the top-down hierarchy of the tables, you may find the latest version of the [hierarchy]({{ source.dataset.hierarchy_url }}) in the source on GitHub.

##### CLI
TODO

#### 2. Selecting or creating the SynDB dataset metadata
As mentioned, in the [overview article](0-overview.md), every dataset has a metadata defined by the data owner during the upload. You can either select an existing dataset or create a new one.

#### 3. Confirm and upload
Before the upload starts you will be prompted to confirm the dataset and the data you are uploading. Once you confirm, the upload will start. Should be relatively quick.

### Delete owned datasets
You may at any time delete datasets that you own. This will remove the dataset and all the data associated with it. The deletion is permanent and cannot be undone.
