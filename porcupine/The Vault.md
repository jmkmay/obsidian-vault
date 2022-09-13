# The Vault

The Vault is the term for the relational storage center of the project. It is a fully connected data warehouse that is queryable via and key or relationship.

The Vault should ideally be hot swappable. Data that exists as a Data Source should be able to be slotted into a new Vault on demand. Just create an interface and new set of mapping rules, and rerun the data ingress routine for each Data Source.

**THE CURRENT DATABASE SYSTEM REMAINS UNKNOWN**

## Database Candidates

### DynamoDB

Extremely efficient but requires knowledge of the data structure prior to creating a schema for each Data Source. Also very difficult to design a query schema for handling complex relationships.

### BigQuery

Very good at performing complex queries. Has a funky data structure in the form of tables and schemas (similar to an RDBMS by the looks of it). I've read about weird performance quirks where you want to try to keep everything in the same table, but some forms of data ingress require creation of a new table...

May be a good candidate if growth exceeds The Vault's ability to keep up with performance.

### neo4j

Best in the business when it comes to querying and maintaining relationships between data. Also the most expensive. Also doesn't offer a hosted solution via any of the Cloud providers.

### Neptune

Amazon's "managed" Graph Database. Data ingress comes in the form of S3 files. Neptune parses S3 files and generates a queryable dataset.

