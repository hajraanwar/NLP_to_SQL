# Oracle LLM SQL Query Generator

## Overview
This project integrates an Oracle database with an LLM-based natural language interface to generate and execute SQL queries. Users can input natural language queries, and the system will generate SQL, execute it, and provide results in both structured and human-readable formats.

## Features
- Connects to an Oracle database
- Extracts schema details dynamically
- Uses Llama-3 for SQL query generation
- Executes SQL queries and fetches results
- Provides human-readable query explanations
- Includes a Gradio-based chatbot interface

## Installation
### Prerequisites
- Python 3.8+
- Oracle Instant Client
- cx_Oracle
- PyTorch
- Transformers (Hugging Face)
- Gradio

### Steps
1. Install required dependencies:
   ```sh
   !apt-get install libaio1
   !pip install cx_Oracle torch transformers gradio
   ```
2. Download and set up Oracle Instant Client:
   ```sh
   !mkdir -p /opt/oracle
   !wget https://download.oracle.com/otn_software/linux/instantclient/211000/instantclient-basic-linux.x64-21.1.0.0.0.zip
   !unzip -o instantclient-basic-linux.x64-21.1.0.0.0.zip
   !cp -r instantclient_21_1/* /opt/oracle/
   !sh -c "echo /opt/oracle > /etc/ld.so.conf.d/oracle-instantclient.conf"
   !ldconfig
   ```
3. Set up the environment variables:
   ```python
   import os
   os.environ["LD_LIBRARY_PATH"] = "/opt/oracle"
   ```

## Usage
### 1. Extract Database Schema
```python
schema = extract_schema()
print("Extracted Schema:", schema)
```

### 2. Generate and Execute SQL Queries
```python
user_query = "In the announcements table, dividend less than 1000"
query_results, explanation = execute_and_explain_query(connection_details, schema, user_query, tokenizer, model)
print("\nHuman-readable Explanation:", explanation)
```

### 3. Start Gradio Chatbot Interface
```python
demo.launch()
```

## Configuration
### Database Connection
Update the following dictionary with your database credentials:
```python
connection_details = {
    "host": "your_host",
    "port": 1521,
    "username": "your_username",
    "password": "your_password",
    "database_name": "your_db"
}
```

### LLM Model Configuration
Replace `YOUR HUGGING FACE TOKEN` in the `load_llm()` function with your Hugging Face API token.

## Future Enhancements
- Improve query validation and error handling
- Support additional LLM models for SQL generation
- Enhance Gradio UI with better user interaction
- Add authentication for database security

## Contributing
Feel free to submit issues or contribute by making pull requests.

## License
This project is licensed under the MIT License.

