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
syndb plugin cave init transfer --dataset_id <dataset_id> --cave_id <cave_id>
```
