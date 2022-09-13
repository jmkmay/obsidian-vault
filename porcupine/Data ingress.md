# Data ingress

Data ingress will come in the form of data sources. A data source is a unique entity with a set of rules as to how to acquire the data, and transform it into a storable entity (basic ETL job).

### Example: Census Data from Government of Canada
In this example, the data is accessed via a HTTP GET request.

It returns a JSON formatted text response.

It has a set of fields for each piece of data which may be heirarchical.

Each field may or may not map to a key in The Vault.