# Search
The search feature filters through datasets based on the search terms provided by the user. The search terms can be combined to narrow down the search results.

By default, every search field is AND meaning that the every term has to exist for in the resulting dataset.

!!! note "TODO"
    Add capabilities to customize the logical operators in the search, e.g., AND, OR, NOT.

## Usage

### User interface

#### GUI
The GUI provides a simple interface for the search. After defining the search terms, click the search button to retrieve the results. The search results will be displayed in a table format. The search results can be exported to a CSV file by clicking the export button.

### Download the search results
Following the search, you may download the imaging derived metrics of the datasets from the search results. You will get a single `.tar.xz` file with parquet files inside. You may read parquet files using the {{ pandas_read_parquet }} or {{ polars_read_parquet }} library in Python.

!!! note "Other languages"
    [Apache parquet](https://parquet.apache.org/ "Link to Apache parquet website") is a file format supported by most popular programming languages. You may find libraries for reading parquet files in your preferred language.
