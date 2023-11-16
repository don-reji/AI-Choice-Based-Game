
# AI Choice Based Game

This is a branching choice based game where you can choose multiple choices and each of the choice taken will affect the choice of the future till you end up in the correct path. This is made using OpenAI api and integrating it with an apache cassandra database, which has vector support which means we can inject real time data in a memory buffer into this AI model.

## LLMs limitations and overcoming it
LLMs like chatGPT can reason based on information, but the model can only reason based on data it trained on (September 2021). The main issue and bottleneck we face here is using real-time data and remebering large amount of data that the user inputs. To mitigate this issues we need to inject data into the model that we deem accurate and we want it to reason in the prompt and instruct the model to reason based on that information. This process is called RAG (Retrival Augumented Generation). So we are going to use a memory for the LLM so that it can know all of the previous replys for the future use.

## Create a Vector Database
To provide real time data to LLM we need a very fast database to store and retrieve data for us, so i used a vector database from Datastaxs since it is free.

1. Click [this link](https://www.datastax.com/lp/astra-registration?utm_medium=youtube_video&utm_source=datastax&utm_campaign=yt_influencers&utm_content=vector_search_tim_ruscica) and create an account.

2. After that click create database, select vector database, add a database name and keyspace name (needed for later) and create.