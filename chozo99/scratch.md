git@github-chozo99.com:chozo99/elasticsearch-learning-to-rank.git


git@github-chozo99.com:chozo99/hello-ltr.git


https://elasticsearch-learning-to-rank.readthedocs.io/en/latest/

https://en.wikipedia.org/wiki/IMDb
The Movie Database (TMDB)
https://www.google.com/search?q=imdb+tmdb&oq=imdb+tmdb&gs_lcrp=EgZjaHJvbWUqBwgAEAAYgAQyBwgAEAAYgAQyCAgBEAAYCBgeMgYIAhAAGB4yCAgDEAAYCBgeMggIBBAAGAgYHjIICAUQABgIGB4yCAgGEAAYCBgeMggIBxAAGAgYHjIKCAgQABiABBiiBDIKCAkQABiABBiiBNIBCDE3NTBqMGo3qAIAsAIA&sourceid=chrome&ie=UTF-8#ip=1




Learning to Rank applies machine learning to relevance ranking.
LTR 은 머신러닝에 관련성 순위를 적용합니다.
> LTR 은 relevance ranking 을 위해서 머신러닝을 사용합니다.

The Elasticsearch Learning to Rank plugin (Elasticsearch LTR) gives you tools to train and use ranking models in Elasticsearch.
ES LTR plugin 은 ES 에서 학습하고 랭킹모델을 사용할수 있는 툴을 제공합니다.

https://discuss.elastic.co/t/elasticsearch-learning-to-rank-v-1-0-rc-1-released/102357
What is Learning to Rank? It applies machine learning to relevance ranking. 
This plugin is currently serving search results on Wikipedia and Snagajob. 
It's been codeveloped between OpenSource Connections 2, Wikimedia Foundation 4, and Snagajob Engineering 4. Enjoy!

OpenSource Connections, Wikimedia Foundation, Snagajob Engineering 와 공동 개발되었음

https://github.com/o19s
OpenSource Connections 의 github 리포

o19s 는 k8s 처럼
OpenSourceConnections 에서 가운데 글자가 19자 라는 뜻의 약자;;;

==================================

Core Concepts

Learning to Rank (LTR) applies machine learning to search relevance ranking. 
> 검색 랭킹에 머신러닝을 사용했다.

What is Learning to Rank?
> 전통적인 머신러닝인 예측(regression 을 이용한 predict), 이나 분류(classification) 하고 다르다.
LTR 에서는 직접적인 예측을 하지는 않다. (In Learning to Rank, the function f we want to learn does not make a direct prediction.)
문서의 순위를 매기는데 사용됩니다. (Rather it’s used for ranking documents.)

LTR 은 쿼리에 따른 문서의 이상적인 순서를 사용자를 통해서 학습합니다.
> We want a function f that comes as close as possible to our user’s sense of the ideal ordering of documents dependent on a query. 

예측(function f) 결과 자체로는 의미가 없습니다. 이는 쿼리가 제공된 문서의 상대적 유용성에 대한 예측 값습니다.
>The value output by f itself has no meaning (it’s not a stock price or a category). It’s more a prediction of a users’ sense of the relative usefulnes of a document given a query.
LTR 에서는 ranking function f 를 사용

Judgments: expression of the ideal ordering
> 정답set 을 여기서는 golden sets 이라고 함, 검색에서는 개, 고양이를 맞추는게 아니기에
정답 set 이라고 할수 있는게 어려움
예를 들면
 When users search for “Rambo” we can indicate which movies ought to come back for “Rambo” based on our user’s expectations of search.
사용자가 람보를 검색했을때, 어떤 영화를 봤을때 람보가 생각나는 영화들을 표시해줄수도 있다.


Features: the raw material of relevance
> ranking function f: f(titleScore, descScore, popularity, rating, numKeywords)

https://livebook.manning.com/book/relevant-search/chapter-4/


* Logging features: completing the training set

Queries are given ids, and the actual document identifier can be removed for the training process.
> 쿼리들에 id 가 부여되고, 실제 문서의 식별자는 학습을 위해서 제거 될수 있습니다.

```
4   qid:1   1:0.0   2:21.5  3:100,...
4   qid:1   1:42.5  2:21.5  3:95,...
3   qid:1   1:53.1  2:40.1  3:50,...
...
```



With judgments and features in place,
judgments 와 features 가 갖추어진 상태에서



* Real World Concerns
Now that you’re oriented,
>이제 방향을 잡았으니,


* What the plugin does
Then other tools take over.
그런 다음 다른 도구가 대신합니다.


https://elasticsearch-learning-to-rank.readthedocs.io/en/latest/feature-engineering.html#getting-raw-term-statistics

sltr: Search LTR

Elasticsearch LTR comes with a query primitive
> Elasticsearch LTR에는 쿼리 기본 요소가 함께 제공됩니다.

A large number of statistics are available.
> 많은 수의 통계가 제공됩니다.


