# Search Engines

## 1. Introduction

### 1.1 Information Retrieval

Gerard Salton, a pioneer in information retrieval and one of the leading figures from the 1960s to the 1990s, proposed the following definition in his classic 1968 textbook (Salton, 1968):
> Information retrieval is a field concerned with the structure, analysis, organization, storage, searching, and retrieval of information.
*Relevance* is a fundamental concept in information retrieval. Loosely speaking, a relevant document contains the information that a person was looking for when she submitted a query to the search engine. To address the issue of relevance, researchers propose *retrieval models* and test how well they work. A retrieval model is a formal representation of the process of matching a query and a document. It is the basis of *the ranking algorithm* that is used in a search engine to produce the ranked list of documents. An interesting feature of the retrieval models used in information retrieval is that they typically model *the statistical properties of text rather than the linguistic structure*. More advanced models do incorporate linguistic features, but they tend to be of secondary importance.
Another core issue for information retrieval is *evaluation*. Cyril Cleverdon led the way in developing evaluation methods in the early 1960s, and two of the measures he used, *precision and recall*, are still popular. *Precision* is a very intuitive measure, and is the proportion of retrieved documents that are relevant. *Recall* is the proportion of relevant documents that are retrieved.
The third core issue for information retrieval is the emphasis on users and their *information needs*. An information need is the underlying cause of the query that a person submits to a search engine.
### 1.2 Search Engines
A search engine is the practical application of information retrieval techniques to large-scale text collections.
The "big issues" in the design of search engines include the ones identified for information retrieval: *effective ranking algorithms, evaluation, and user interaction*. There are, however, a number of additional critical features of search engines that result from their deployment in large-scale, operational environments. Foremost among these features is *the performance of the search engine in terms of measures such as response time, query throughput, and indexing speed*. *Response time* is the delay between submitting a query and receiving the result list, *throughput* measures the number of queries that can be processed in a given time, and *indexing speed* is the rate at which text documents can be transformed into indexes for searching. An index is a data structure that improves the speed of search.
Another important performance measure is how fast new data can be incorporated into the indexes. Search applications typically deal with dynamic, constantly changing information. *Coverage* measures how much of the existing information in, say, a corporate information environment has been indexed and stored in the search engine, and *recency or freshness* measures the "age" of the stored information.
*Scalability* is clearly an important issue for search engine design. Designs that work for a given application should continue to work as the amount of data and the number of users grow. 
Search engines are used in many applications and for many tasks. To do this, they have to be *customizable or adaptable*. This means that many different aspects of the search engine, such as the ranking algorithm, the interface, or the indexing strategy, must be able to be tuned and adapted to the requirements of the application.
Practical issues that impact search engine design also occur for specific applications. The best example of this is *spam* in web search.

Major issues in information retrieval and search engines:![Information Retrieval & Search Engine Major Issues](https://github.com/rkq/docs/blob/master/pics/ir-se-major-issues.png)
## 2. Architecture of a Search Engine
Search engine components support two major functions, which we call *the indexing process* and *the query process*. The major building blocks of indexing process are *text acquisition, text transformation, and index creation*; the major building blocks of query process are *user interaction, ranking, and evaluation*.
## 3. Crawls and Feeds