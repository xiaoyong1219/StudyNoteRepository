## Elasticsearch

### Elasticsearch概述

`Elasticsearch`，简称`es`,`es`是一个开源的==高扩展==的==分布式全文检索引擎==，它可以近乎==实时的存储、检索数据==；本身扩展性很好，可以扩展到上百台服务器，处理PB级别（大数据时代）的数据，es也是用java开发并使用Lucene作为其核心来实现所有索引和检索的功能，但是它的目的是通过简单的==RESTful API==来隐藏Lucene的复杂性，从而让全文搜索变得简单。

据国际权威的数据库产品评测机构DB Engines的统计，在2016年1月，Elasticsearch已超过Solr等，成为排名第一的搜索引擎类应用。

### ES和Solr的差别

#### Elasticsearch简介

Elasticsearch是一个实时分布式搜索和分析引擎，它让你以前所未有的速度处理大数据成为可能。

它用于全文检索、结构化搜索、分析以及将这三者混合使用。

维基百科使用Elasticsearch提供全文检索并高亮关键字，以及输入实时搜索（searche-asyou-type）和搜索纠错（did-you-mean）等搜索建议功能。

英国卫报使用Elasticsearch结合用户日志和社交网络数据提供给他们的编辑以实时的反馈，以便于及时了解公众对新发表的文章的回应。

StackOverFlow结合全文搜索和地理位置查询，以及more-like-this功能找到相关的问题和答案。

GitHub使用Elasticsearch检索1300亿行代码。

Elasticsearch是一个基于Apache Lucene(TM)的开源搜索引擎。无论在开源还是专有领域，Lucene可以被认为是迄今为止最先进、性能最好、功能最全的搜索引擎库。

但是Lucene只是一个库，想要使用它，你必须使用java来作为开发语言并将其直接集成到你的应用中，更糟糕的是，Lucene非常复杂，你需要深入了解检索的相关知识来理解它是如何工作的。

Elasticsearch也是用java开发并使用Lucene作为器核心来实现所有索引和搜索的功能，但是它的目的是通过简单的==RESTFul API==来隐藏Lucene的复杂性，从而使全文检索变得简单。

#### Solr简介

Solr是Apache下的一个顶级开源项目，采用java语言开发，它是基于Lucene的全文搜索服务器，Solr提供了比Lucene更为丰富的查询语言，同时实现了可配置、高扩展，并对索引、检索性能进行了优化。

Solr可以独立运行，运行在Jetty、Tomcat等Servlet容器中，Slor索引的实现方法很简单，用==POST方法向Solr服务器发送一个描述Field及其内容的XML文档，Solr根据xml文档添加、删除、更新索引==。Solr搜索只需要发送HTTP GET请求，然后对Solr返回xml、==json==等格式的查询结果进行解析，组织页面布局。solr不提供构建UI的功能，Solr提供了一个管理界面，通过管理界面可以查询Solr的配置和运行情况。Solr是基于Lucene开发的企业级搜索服务器，实际上就是封装了Lucene。

Solr是一个独立的企业级搜索应用服务器，它对外提供了类似==Web-Service==的API接口。用户可通过http请求，向搜索引擎服务器提交一定格式的文件，生成索引，也可以通过提出查询请求，并得到返回结果。

#### Lucene简介

Lucene是Apache软件基金会Jakarta项目组的一个子项目，是一个开放源代码的全文搜索引擎工具包，但它不是一个完整的全文检索引擎，而是一个全文检索引擎的架构，提供了完整的查询引擎和索引引擎，部分文本分析引擎（英文和德文两种西方语言）。Lucene的目的是未软件开发人员提供一个简单易用的工具包，以方便的在目标系统中实现全文检索的功能，或者是以此为基础建立简单却强大的应用程式接口，能够做全文索引和搜寻。==在java开发环境里Lucene是一个成熟的免费开源工具。就其本身而言，Lucene是当前以及最近几年最受欢迎的免费java信息检索程序库。==人们经常提到信息检索程序库，虽然和搜索引擎有关，但不应该讲信息检索程序库与搜索引擎相混淆。

Lucene是一个全文检索引擎的架构，那什么是全文搜索引擎？

全文搜索引擎是名副其实的搜索引擎，国外具代表性的有Google，国内著名的有百度（baidu），它们都是通过从互联网上提取各个网站的信息（以网页文字为主）而建立的数据库中，检索与用户查询条件相匹配的记录，然后按照一定的排列顺序将结果返回给用户。

从搜索结果来源的角度，全文搜索引擎又可分为两种，一种是拥有自己的检索程序（Indexer），俗称“蜘蛛”（Spider）程序或者”机器人“（Robot）程序，并自建网页数据库，搜索结果直接从自身的数据库中调用，如上面提及的百度和谷歌。另一种则是租用其他引擎的数据库，并按自定的格式排列搜索结果，如Lycos引擎。

#### Elasticsearch和Solr比较

1. ES基本是开箱即用，非常简单，Solr安装略微复杂一些。

2. Solr利用Zookeeper进行分布式管理，而Elasticsearch自身带有分布式协调管理功能；

3. Solr支持更多格式的数据，比如JSON、XML、CSV，而Elasticsearch仅支持JSON文件格式；

4. Solr官方提供的功能更多，而Elasticsearch本身更注重于核心功能，高级功能多有第三方插件提供，例如图形化界面需要Kibana友好支撑；

5. Solr查询快，但更新索引时慢（即插入删除慢），多用于电商等查询多的应用；

   - Elasticsearch建立索引快（即查询慢），即实时性查询快，用于Facebook、新浪等搜索；

   - Solr是传统搜索应用的有力解决方案，但Elasticsearch更适用于新兴的实时搜索应用。

6. Solr比较成熟，有一个更大、更成熟的用户、开发和贡献者社区，而Elasticsearch相对开发维护者较少，更新太快，学习使用成本较高。

​     

### Elasticsearch安装





### ES核心概念





### IK(elasticsearch-analysis-ik)分词器插件

> 什么是分词器？

分词：即把一段中文或者英文等字符划分为一个个的关键字，我们在搜索的时候会把自己的信息进行分词，会把数据库中或者索引库中 的数据进行分词，然后进行一个匹配操作，默认的中文分词器是将每个字看成一个词，比如”我爱狂神“，会被分成“我”，“爱“，”狂“，”神“。

`IK`提供了两个分词算法，`ik_smart` 和`ik_max_word`，其中`ik_smart`为最少切分，`ik_max_word`为最小粒度切分。 

> 安装

1. 下载地址：https://github.com/medcl/elasticsearch-analysis-ik/releases

2. 下载完毕之后，放到`Elasticsearch`的插件目录`plugins`

   ![image-20210207154013143](images/image-20210207154013143.png)

3. 重启观察`Elasticsearch`，可以看到`ik`分词器被加载了

   ![image-20210207161507419](images/image-20210207161507419.png)

4. 验证

   ```shell
   # 可以通过这个命令来查看加载进来的插件
   elasticsearch-plugin list
   ```

   看到加载的插件清单中包含了 `ik`分词器

   ![image-20210207161849871](images/image-20210207161849871.png)

5. 使用`kibana`验证

   > 查看不同分词器的分词效果

   - `ik_smart`

     ![image-20210207162343733](images/image-20210207162343733.png)

   - `ik_max_word` ，最小粒度划分，穷尽词库的可能

     ![image-20210207162606564](images/image-20210207162606564.png)



### Rest风格说明

一种软件架构风格，而不是标准，只是提供了一组设计原则和约束条件，它主要用于客户端和服务器交互类的软件，基于这个风格设计的软件可以更简洁，更有层次，更易于实现缓存等机制。

基本Rest命令说明

method|url地址|描述
--|--|--
PUT|localhost:9200/索引名/类型名称/文档id|创建文档（指定文档id）
POST|localhost:9200/索引名称/类型名称|创建文档（随机文档id）
POST|localhost:9200/索引名称/类型名称/文档id/_update|修改文档
DELETE|localhost:9200/索引名称/类型名称/文档id|删除文档
GET|localhost:9200/索引名称/类型名称/文档id|通过文档id查询文档
POST|localhost:9200/索引名称/类型名称/_search|查询所有数据

> 基础测试（使用**kibana**操作） http://localhost:5601

1. ##### 创建一个索引

```
PUT /索引名称/~类型名称~/文档id
{
	请求体
}
```

![image-20210202111236255](images/image-20210202111236255.png)

在Elasticsearch-head界面可以看到索引和数据都已经成功创建

![image-20210202111559352](images/image-20210202111559352.png)