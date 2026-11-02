## Design and Implementation of LangChain Expression Language (LCEL) Expressions

### AIM:
To design and implement a LangChain Expression Language (LCEL) expression that utilizes at least two prompt parameters and three key components (prompt, model, and output parser), and to evaluate its functionality by analyzing relevant examples of its application in real-world scenarios.

### PROBLEM STATEMENT:
To develop an LCEL-based application using LangChain that accepts two input parameters, Topic and Industry, and generates meaningful explanations about the given topic and its real-world applications in the specified industry. The system uses a prompt template, an OpenAI chat model, and an output parser connected through the LCEL pipe operator.

### DESIGN STEPS:

#### STEP 1:
Import the required libraries and configure the OpenAI API key. Create a prompt template using two parameters: topic and industry.
#### STEP 2:
Initialize the ChatOpenAI model and create a StrOutputParser to convert the model response into a readable string.
#### STEP 3:
Connect the prompt, model, and output parser using the LCEL pipe (|) operator. Execute the chain using different inputs and display the generated responses.
### PROGRAM:
```
import sys
!{sys.executable} -m pip install -q langchain langchain-openai python-dotenv
import os
from getpass import getpass

from langchain_openai import ChatOpenAI
from langchain_core.prompts import ChatPromptTemplate
from langchain_core.output_parsers import StrOutputParser
api_key = getpass("Enter your OpenAI API key: ")

if not api_key.strip():
    raise ValueError("API key cannot be empty")

os.environ["OPENAI_API_KEY"] = api_key.strip()

print("API Key Configured Successfully")
prompt = ChatPromptTemplate.from_template(
    "Explain {topic} and describe its real-world application in {industry}."
)

print("Prompt Created Successfully")
model = ChatOpenAI(
    model="gpt-4o-mini",
    temperature=0
)

print("Model Created Successfully")
output_parser = StrOutputParser()

print("Output Parser Created Successfully")
chain = prompt | model | output_parser

print("LCEL Chain Created Successfully")
response = chain.invoke({
    "topic": "Internet of Things",
    "industry": "Smart Agriculture"
})

print(response)
```
### OUTPUT:
<img width="1361" height="740" alt="Screenshot 2026-11-02 154207" src="https://github.com/user-attachments/assets/e3b1fdbc-81ff-4346-a242-6550e729c4d4" />

### RESULT:
Thus, the LangChain Expression Language (LCEL) expression was successfully designed and implemented using two prompt parameters, Topic and Industry, and three key components: Prompt, Model, and Output Parser. The components were connected using the LCEL pipe (|) operator. The program generated meaningful responses for real-world applications in Smart Agriculture and Healthcare.
