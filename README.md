# Data_Analysis

### 该项目主要包含四部分：<br>
1、批量修改文件夹的简单Demo <br>
2、爬取国内疫情数据并绘制出地图进行可视化展示<br>
3、数据分析之对新闻进行分类<br>
4、电商数据各个纬度的数据分析

### 项目介绍

#### pyechart绘制疫情地图
1、通过爬虫，爬取国内疫情数据，并存储为json文件 <br>
2、解析json文件转存为excel文件 <br>
3、pandas读取excel表格数据，通过pyecharts工具进行可视化展示 <br>
[疫情地图](./epidemic.html)


#### 数据分析之新闻分类

##### 一、文本预处理
文本数据是一种非结构化数据，与传统分析数据不同。 文本预处理包含： 
1、缺失值的处理 <br>
2、重复值处理 <br>
3、文本内容清洗 <br>
4、分词 <br>
5、停用词处理

##### 二、词频统计，生成词云图
python中，wordcloud模块提供了生成词云图的模块

##### 三、TF-IDF文本向量化
对文本数据进行建模，有两个问题需要解决：<br>
1、模型进行数学运算，因此需要数值类型的数据，而文本不是数据类型数据<br>
2、模型需要结构化数据，而文本是非结构化数据<br>
将文本转化为数值特征向量的过程，称为文本向量化。将文本向量化，可以分为如下步骤：<br>
1、对文本分词，拆分成更容易处理的单词<br>
2、将单词转化为数值类型，即使用合适的数值来表示每个单词<br>
同样，需要注意的是，文本是非结构化数据，在向量化过程中，需要将其转化为结构化数据

TF-IDF<br>
通过CountVecorizer，我们能够将文本向量化。在向量化的过程中，我们使用每个文档中单词的词频数作为对应的特征的取值。这是合理的，因为单词出现的次数越多，就认为比单词出现的次数少的单词更加重要。<br>
然而，这是相对的，有些单词我们不能仅以当前文档的词频数来衡量，还要考虑语料库中，在其他文档出现的次数。因为有些单词，确实是非常常见的，其在预料库中所有文档中，可能会频繁出现，对于这样的词我们应该降低其重要性。<br>
TF-IDF可以用来调整单词在文档中的权重。其由两部分组成：<br>
1、TF(Term-Frequency)词频，指一个单词在文档中出现的次数<br>
2、IDF(Inverse-Document-Frequency)逆文档频率<br>
idf的计算方式：<br>
idf(t) = log(n/(1+df(t))<br>
其中n为语料库中的文档的总数，df(t)为语料库中含有单词t的文档个数。最终TF-IDF的值为：<br>
tf-idf(t,d) = tf(t,d) * idf(t) (词频*权重)<br>

##### 方差分析实现特征选择
特征选择<br>
使用词袋模型向量化后，会产生过多的特征，这些特征对计算和存储造成巨大的压力，同时，并非所有的特征对建模都有帮助，基于以上原因，我们将数据送入模型之前，先进行特征选择。<br>
我们可以使用方差分析(ANOVO)来进行特征选择，比如选择与目标分类变量最相关的2000个特征。方差分析用来分析来自不同总体的样本均值是否相等，进而可以用来检验分类变量与连续变量之间是否相关。检验方式为，根据分类变量的不同取值，将样本进行分组。首先计算组内差距SSE与组间差距SSM，然后计算：<br>
F = SSM/(c-1)/SSE/(n-c)<br>
其中n为样本数量，c为类别数量(分组数量)。得出F，服从自由度为(c-1,n-c)的F分布。因此我们可以根据该值的大小来判断不同分组的均值是否相等<br>

##### 朴素贝叶斯实现文本分类
使用贝叶斯公式实现分类与预测。朴素贝叶斯算法是基于概率的分类算法，其前提是要求特征之间独立。实际上使用的就是全概率公式与贝叶斯公式。朴素贝叶斯公式在文本分类场景中是非常合适的

#### 电商数据分析
对电商数据进行各个纬度的分析，并通过可视化的方式进行展示<br>
纬度包括以下方面：<br>
1.2018年至2019年各品类商品销售额情况<br>
2.2018年至2019年各地区商品销量情况<br>
3.2018年至2019年各地区经理的利润情况<br>
4.2018年与2019年各地区订单变化情况<br>
5.2019年各地区销售经理销售情况<br>
6.2019年各地区销售经理退货数<br>
7.2019年各地区销售经理实际销售额占比 <br>
8.2019年各地区经理销售额完成情况<br>
9.2019年各品类商品销售额贡献<br>
10.2019年各品类商品地区销售情况<br>
11.各品类商品的实际销量趋势<br>
12.2019年各地区新老客户利润占比<br>
13.2019年客户细分<br>
14.2019年各地区客户分布


