# Metrics structuring for contribution

!!! note "Prerequisites"
    This article requires that you understand how data is stored on SynDB, we recommend reading through the [overview article](../dataset/0-overview.md) if you are uncertain.

This article is a guide for contributors who wish to upload their data to SynDB.

## Data structuring

### Schema
Each SynDB table has its [own schema]({{ source.dataset.schema_list_url }} "Link to GitHub where the overview is versioned"), which can be found on the GitHub repository. The schema defines the supported column names and their data types. The data must be structured in a way that is compatible with the schema of the table you are contributing to.

The column names and the data stored under them must be in a format that is compatible with the type. You can find the supported column names for each SynDB table in the . You may use the [glossary](#column-name-glossary) at the end of this article for reference.

### Sourcing raw data
You may upload the sourcing raw data files including meshes or SWL to SynDB. Place the absolute path to the file in your table file. The following are supported, and the main tracker for new formats:

- **Meshes** in `.glb` format, column name: `mesh_path`
- **SWC** files, `.swc`, column name: `swc_path`

### Requests for new metrics
You may request additional formats on the {{ discord.hyperlink }} channel. The SynDB team will review the request and consider adding the new format to the platform.

## Column name glossary

| **Key**                     | **Description**                                                                      |
|-----------------------------|--------------------------------------------------------------------------------------|
| `dataset_id`                | The unique identifier for the dataset, of type `uuid`.                               |
| `cid`                       | The unique identifier for a SynDB unit within the dataset, of type `uuid`.           |
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
| `parent_id`                 | The unique identifier of the parent component, of type `uuid`.                       |
| `parent_enum`               | An integer representing the type or category of the parent component, of type `int`. |
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
