# Metrics structuring for contribution

!!! note "Prerequisites"
    This article requires that you understand how data is stored on SynDB, we recommend reading through the [overview article](../dataset/0-overview.md) if you are uncertain.

This article is a guide for contributors who wish to upload their data to SynDB.

## Data structuring

### Schema
Each SynDB table has its own schema, which can be found on our [GitHub repository]({{ source.dataset.schema_list_url }} "Link to GitHub where the overview is versioned"). The schema defines the supported column names and their data types. The data must be structured in a way that is compatible with the schema of the table you are contributing to.

The column names and the data stored under them must be in a format that is compatible with the type. You can find the supported column names for each SynDB table in the . You may use the [glossary](#glossary) at the end of this article for reference.

### Sourcing raw data
You may upload the sourcing raw data files including meshes or SWL to SynDB. Place the absolute path to the file in your table file. The following are supported:

- **Meshes** in `.glb` format, column name: `mesh_path`
- **SWC** files, `.swc`, column name: `swc_path`

This list is the main tracker for the supported formats.

### Requests for new metrics
You may request additional formats on the {{ discord.hyperlink }} channel. The SynDB team will review the request and consider adding the new format to the platform.

## Columns
Most column types are self-explanatory, but some require additional explanation.

### Identifiers and relations
The CID column defined in your table can have any unique hashable value, it will be replaced by a UUID when uploaded to SynDB. When uploading a relational dataset, the `cid` column in the parent will be used to correlate the relations to the children by their `parent_id`; meaning the hashable value in the parent `cid` column must match the `parent_id` in the child. `parent_enum` can be omitted as the compartments are defined at the tabular level, and will, therefore, be added automatically.

### Example
Notice the `parent_id` column in the child table, this is the `cid` of the parent table. The `parent_enum` column is not present in the child table, as it is defined at the tabular level.

#### Vesicle, child

| cid | neurotransmitter | voxel_radius | distance_to_active_zone | minimum_normal_length | parent_id | centroid_z | centroid_x | centroid_y |
|-----|------------------|--------------|-------------------------|-----------------------|-----------|------------|------------|------------|
| 0   | glutamate        | 26.9129       | 705.2450                | 23                    | 1         | 4505.232   | 1996.224   | 4953.6     |
| 1   | glutamate        | 25.5388       | 615.0213                | 23                    | 1         | 4505.232   | 1996.224   | 4953.6     |
| 2   | glutamate        | 29.5260       | 513.0701                | 23                    | 1         | 4505.232   | 1996.224   | 4953.6     |
| 3   | glutamate        | 30.5131       | 479.9224                | 23                    | 1         | 4505.232   | 1996.224   | 4953.6     |
| 4   | glutamate        | 28.3977       | 454.8248                | 23                    | 1         | 4505.232   | 1996.224   | 4953.6     |
| 5   | glutamate        | 30.2033       | 459.7557                | 23                    | 1         | 4505.232   | 1996.224   | 4953.6     |
| 6   | glutamate        | 33.4548       | 374.8131                | 23                    | 1         | 4505.232   | 1996.224   | 4953.6     |
| 7   | glutamate        | 32.0890       | 455.9293                | 23                    | 1         | 4505.232   | 1996.224   | 4953.6     |


#### Axon, parent
| voxel_volume   | mitochondria_count | total_mitochondria_volume | cid |
|----------------|--------------------|---------------------------|-----|
| 385668034.56   | 1                  | 93208043.52               | 1   |
| 1492089016.32  | 4                  | 412054179.84              | 2   |
| 327740497.92   | 0                  | 0                         | 4   |


### Glossary

| **Key**                     | **Description**                                                                      |
|-----------------------------|--------------------------------------------------------------------------------------|
| `dataset_id`                | The unique identifier for the dataset, of type `uuid`.                               |
| `cid`                       | The unique identifier for a SynDB unit within the dataset, of type `uuid`.           |
| `parent_id`                 | The CID of the parent component, of type `uuid`.                                     |
| `parent_enum`               | An integer representing the type or category of the parent component, of type `int`. |
| `polarity`                  | The polarity of the neuron, of type `ascii`.                                         |
| `voxel_volume`              | The volume of the voxel, of type `double`.                                           |
| `voxel_radius`              | The radius of the voxel, of type `double`.                                           |
| `s3_mesh_location`          | The location of the mesh in S3 storage, of type `smallint`.                          |
| `mesh_volume`               | The volume of the mesh, of type `double`.                                            |
| `mesh_surface_area`         | The surface area of the mesh, of type `double`.                                      |
| `mesh_area_volume_ratio`    | The ratio of the surface area to the volume of the mesh, of type `double`.           |
| `mesh_sphericity`           | The sphericity of the mesh, of type `double`.                                        |
| `centroid_z`                | The z-coordinate of the centroid, of type `double`.                                  |
| `centroid_x`                | The x-coordinate of the centroid, of type `double`.                                  |
| `centroid_y`                | The y-coordinate of the centroid, of type `double`.                                  |
| `s3_swb_location`           | The location of the SWB in S3 storage, of type `smallint`.                           |
| `terminal_count`            | The count of terminals, of type `int`.                                               |
| `mitochondria_count`        | The count of mitochondria, of type `int`.                                            |
| `total_mitochondria_volume` | The total volume of mitochondria, of type `double`.                                  |
| `neuron_id`                 | The unique identifier for the associated neuron, of type `uuid`.                     |
| `vesicle_count`             | The count of vesicles, of type `int`.                                                |
| `total_vesicle_volume`      | The total volume of vesicles, of type `double`.                                      |
| `forms_synapse_with`        | The unique identifier of the synapse that the component forms with, of type `uuid`.  |
| `connection_score`          | The score representing the strength or quality of the connection, of type `double`.  |
| `cleft_score`               | The score for the synaptic cleft, of type `int`.                                     |
| `GABA`                      | The concentration or presence of GABA neurotransmitter, of type `double`.            |
| `acetylcholine`             | The concentration or presence of acetylcholine neurotransmitter, of type `double`.   |
| `glutamate`                 | The concentration or presence of glutamate neurotransmitter, of type `double`.       |
| `octopamine`                | The concentration or presence of octopamine neurotransmitter, of type `double`.      |
| `serine`                    | The concentration or presence of serine neurotransmitter, of type `double`.          |
| `dopamine`                  | The concentration or presence of dopamine neurotransmitter, of type `double`.        |
| `cave_id`                   | The identifier of the cave structure, of type `int`.                                 |
| `pre_id`                    | The unique identifier of the pre-synaptic component, of type `uuid`.                 |
| `post_id`                   | The unique identifier of the post-synaptic component, of type `uuid`.                |
| `dendritic_spine_count`     | The count of dendritic spines, of type `int`.                                        |
| `neurotransmitter`          | The type of neurotransmitter present in a vesicle, of type `ascii`.                  |
| `distance_to_active_zone`   | The distance from the vesicle to the active zone, of type `double`.                  |
| `minimum_normal_length`     | The minimum normal length, of type `int`.                                            |
| `ribosome_count`            | The count of ribosomes within the endoplasmic reticulum, of type `int`.              |
