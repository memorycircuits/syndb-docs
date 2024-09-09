# External sources

SynDB support migrating data from other platforms to varying degrees.


## CAVE
Only `valid_synapses_nt_np` datasets from CAVE are supported.

Initialize cave first:
```bash
syndb plugin cave init
```

Upload to your dataset:
```bash
syndb plugin cave init transfer --dataset-id <syndb-dataset_id> --cave-datastack-name <cave-datastack-name>
```

!!! note "Dataset"
    The `syndb-dataset_id` is the UUID of the SynDB dataset that will be associated with the CAVE data. You can either press `tab` to autocomplete the dataset ID, `syndb plugin cave init transfer --dataset-id<press TAB here>`, or copy and paste from the dataset management page on the GUI.
