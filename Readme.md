
# AI Choice Based Game

This is a branching choice based game where you can choose multiple choices and each of the choice taken will affect the choice of the future till you end up in the correct path. Made using OpenAI api and integrating it with an apache cassandra database, which has vector support to inject real time data in a memory buffer into this AI model. 

## LLMs limitations and overcoming it
LLMs like chatGPT can reason based on information, but the model can only reason based on data it trained on (September 2021). The main issue and bottleneck we face here is using real-time data and remebering large amount of data that the user inputs. To mitigate this issues we need to inject data into the model that we deem accurate and we want it to reason in the prompt and instruct the model to reason based on that information. This process is called RAG (Retrival Augumented Generation). So we are going to use a memory for the LLM so that it can know all of the previous replys for the future use. Langchain is used as an interface for LLM to integrate with other tools in this case cassandra database and function as a wrapper.

## Create a Vector Database
To provide real time data to LLM we need a very fast database to store and retrieve data for us, so i used a vector database from Datastaxs since it is free. First create a python file in the project folder and create a virtual environment.

1. Click [this link](https://www.datastax.com/lp/astra-registration?utm_medium=youtube_video&utm_source=datastax&utm_campaign=yt_influencers&utm_content=vector_search_tim_ruscica) and create an account.
2. After that click create database, select vector database, add a database name and keyspace name (needed for later) and create.
3. Database will take a few minutes to setup. After setup go to 'connect' to download the essentials to connect to database.
4. click 'generate token' to download your token details as a json to the folder of our project.
5. Then click 'get bundle' to download the secure bundle to our project folder.
6. Then install the driver package below which is also available in the installation step in the page.
    ```bash
    pip install cassandra-driver
    ```
7. Then copy the connection code given in the page into our python file. Check the code if the file name of the json token file is same as the name of the json file just downloaded if not change it. Also check for the naming of the secure connection bundle file.

## Packages Required
Install these packages.
```bash
pip install cassio openai langchain tiktoken
```
## OpenAI api key
Get the api key for openai from [this link](https://platform.openai.com/api-keys)  
