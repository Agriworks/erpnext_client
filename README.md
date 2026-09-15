# ERPNext Client

A simple Python client for ERPNext. Use this to access data without needing to create raw HTTP requests.

## Installation

This package uses Poetry for dependency management. Install it in another project using:

```sh
poetry add git+https://github.com/Agriworks/erpnext_client.git
```

## Setup & Running

1. **Install dependencies**:
   ```sh
   poetry install
   ```

2. **Configure environment credentials**:
   ```sh
   cp .env.example .env
   ```
   Add your `ERPNEXT_USERNAME` and `ERPNEXT_PASSWORD` in `.env`.

3. **Run the example script**:
   ```sh
   poetry run python example.py
   ```

## Usage

Here's a simple example of how to use the ERPNext client:

```py
import os
from dotenv import load_dotenv
from erp_client.erp_next_client import ERPNextClient

load_dotenv()

# Initialize the client with your ERPNext instance URL
client = ERPNextClient(base_url="http://erp.csa-india.org")

# Login with your credentials
client.login(
    username=os.getenv("ERPNEXT_USERNAME"),
    password=os.getenv("ERPNEXT_PASSWORD")
)

# Fetch a dataset
dataset_id = "CC Daily Reports"
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
- Support for child tables and query reports
- Synchronize and pull datasets from a specific index
- Retrieve dataset schemas
- Built-in session management
