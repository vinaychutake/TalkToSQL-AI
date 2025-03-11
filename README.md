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

Install packages as below:
pip install tqdm sentence-transformers accelerate bitsandbytes 

<br>Make sure you have NVIDIA Cuda installed as per your GPU, if no GPU then just install torch
>python -m pip install torch==2.5.1+cu124 --index-url https://download.pytorch.org/whl/cu124

<br>

#### Usage Notes
Notebook shows input and outputs implemented in a flow. You can check detailed comments added to understand analysis.<br>
1.  `extract_dataframe` function has been created for more tech savvy people who might want to just extract dataframe and work on top of it
2. And for normal usecases users can use `generate_query_response` which will return human readable text based on the extracted data.

Sample Query:
> generate_query_response("Give me ID of operation having the lowest non-zero total amount submitted ?")

Model Response:
> '\n    ### Model Response: Answer: The operation with the lowest non-zero total amount submitted is **RP 020625 2**.\n\n    ### Context SQL: SELECT Operation_Id FROM repo_table WHERE Total_Amt_Submitted_Billions > 0 ORDER BY Total_Amt_Submitted_Billions ASC LIMIT 1\n    '

Response contains human readable answer provided by LLM and SQL query for context so users can verify on their own if model understood their query correctly and has extracted what they have intended and if response is not false positive/negative, hallucination or misinterpreted.
