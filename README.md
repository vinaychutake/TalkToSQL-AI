## TalkToSQL-AI - Quering structured data with Natural Language

#### Aim:
Using GenAI tools provide ability to run natural language queries on structured database(like CSV, excel, DB etc.) and generate human-readable insights.
Use free, open-source local LLM to generate queries, LLM provides us with core intelligence to understand and generate the response based on the schema prompts provided.


#### Code flow Outline:

1. Clean and store data in internal DB from external source (CSV, Excel, external DB etc.), Here we are taking example of CSV file<br>
2. Load LLM as core intelligence<br>
3. Create SQL Prompts based on DB Schema<br>
4. Generate SQL from natural language query<br>
5. Extract data for provided query<br>
6. Generate user response<br>


#### Setup/Installation

Install packages as below:<br>
pip install tqdm sentence-transformers accelerate bitsandbytes 

<br>Make sure you have NVIDIA Cuda installed as per your GPU, if no GPU then just install torch<br>
python -m pip install torch==2.5.1+cu124 --index-url https://download.pytorch.org/whl/cu124
