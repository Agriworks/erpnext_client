# ERPNext Client

A simple Python client for ERPNext. Use this to access the data without needing to create raw HTTP requests.

## Installation

This package uses Poetry for dependency management. Install it using:

```sh
poetry add git+https://github.com/your-username/csa-erp-client.git

```

## Usage

Here's a simple example of how to use the ERPNext client:

```py
from erp_client.erp_next_client import ERPNextClient

# Initialize the client with your ERPNext instance URL
client = ERPNextClient(base_url="https://your-erp-instance.com")

# Login with your credentials
client.login(username="your_username", password="your_password")

# Fetch a dataset
dataset_id = "Your Dataset Name"
dataset = client.get_dataset(dataset_id)
print(f"Dataset contents:\n{dataset.head()}")

# Sync and pull dataset from a specific index
sync_data = client.sync_pull_dataset(dataset_id, last_index=0)
print(f"Synced data:\n{sync_data.head()}")

# Get dataset schema
schema = client.get_dataset_schema(dataset_id)
print(f"Dataset schema: {schema}")

```

## Features
- Simple authentication with ERPNext instance
- Fetch complete datasets as pandas DataFrames
- Synchronize and pull datasets from a specific index
- Retrieve dataset schemas
- Built-in session management


# Items in Progress

- Development a sync protocol to sync data from ERPNext to the client

