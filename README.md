# League of Legends Wiki using RAG

### This is actually a fun first time project trying to create a RAG (Retrieval Augmented Generation) application. I was curious on how we could task LLMs (Large Language Models) to do something specific for us as in with our own custom knowledge. So, I decided to try and task a LM (Language Model) to answer any question related to a game i usually play (League of Legends).

- # How does RAG work?
### Firstly, the user would attempt to query the LM, but before giving the prompt to the LM we adjust the prompt by adding context. To get context we refer to a vector store (A database storing document embeddings and the documents stored in this case are from the League of Legends Wiki). We perform a similarity search between the user query and the document stored in the vector store to retrieve the most relevant documents. These relevant documents are the context that will be added in our prompt and would be given to the LM. Finally, with LM generative abilities it would then be able to answer our question since we gave it some context, even though the LM wasn't initially trained to answer such questions.

### So everytime a user tries and query the LM their prompt would be in this shape: 
    You are a helpful assistant that can answer questions about League of Legends champions based on the data given to you.

    Answer the following question: {question}
    By looking through the following data: {docs}
    
    Only use the data available to you to answer the question.
    If you feel like you don't have enough information to answer the question say "I don't know"

    Your answers should be verbose and detailed.

### I relied on Langchain / HuggingFace to make this. However, of course, it isn't perfect and its answers could possibly not satisfy you, nevertheless I find it very interesting the fact that its implementation is simple. It also shows how RAG can be used to create many useful applications.
### You can run this through Google Colab if you want, and I recommend using the T4 GPU or any cuda-related device.

### I learned by watching [Rishab Kumar](https://github.com/rishabkumar7), he made a Youtube assistant that can answer any questions related to the video of interest.
