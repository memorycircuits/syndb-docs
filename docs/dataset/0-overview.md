# Overview
The SynDB data platform is accessible through the API. By search, you may find and download high level metrics; by upload, you may share your data to become part of a meta-analytical study.

## Composition
The SynDB data platform is designed to provide a comprehensive and organized repository of high-resolution microscopy data and associated metadata. The composition of SynDB can be broken down into three main components: Metadata, Image Metrics, and Raw Data. Each of these components plays a crucial role in the functionality and utility of the platform.

### Metadata
The metadata is used to define and retrieve datasets. It stores metadata about the data in the respective dataset:

- Brain region
- Sourcing model animal
- Genetic manipulations (mutations)
- Microscopy method
- Publication information

The metadata is defined by the data owner during upload.

!!! warning "Dataset"
    You must split your dataset into individual SynDB datasets if any of these fields differ within your own dataset.

### Image metrics
The image metrics in SynDB are derived from high-resolution microscopy assays, processed using sophisticated algorithms and models. These metrics form the primary data of interest within the platform. Each neuronal compartment and structure has its own unique set of metric categories, which necessitates distinct database schemas. We will refer to these phenomena as SynDB tables in future references.

To facilitate efficient data management, every imaging metric is linked to a dataset via its ID. This linkage enables robust search capabilities by filtering through metadata, thus avoiding the need to handle terabytes of raw data directly. You can learn more about how dataset metadata filtration works in the article on [search](1-search.md).

The flexible data model of SynDB supports this functionality by defining specific parameters for each compartment and structure. These varied models are unified into comprehensive datasets through dataset metadata, which effectively organizes data groups across the platform. This unified approach ensures that users can efficiently access and analyze the vast array of imaging metrics available in SynDB.

### Raw data
Raw data is the original data from which the metrics are derived. The raw data is stored in the database and can be requested from its metric counterpart. Raw data sets currently include meshes and SWC files. These are included at the discretion of the data owner.
