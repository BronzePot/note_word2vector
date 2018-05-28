# word2vector学习笔记（c++源码）

## Word类

类成员：

成员类型  | 成员名称 | 成员作用
---------|----------|---------
 int32_t | index_ | 索引，词表中的位置
 string  | text_  | 词的字符串
 int32_t | count_ | 词频数
 Word*   | left_  | 指向哈夫曼树的左子树
 Word*   | right_ | 指向哈夫曼树的右子树

 成员函数：

 1.构造函数：参数为成员变量，左右指针的默认值为0
Word(int32_t index, String text, uint32_t count, Word *left = 0, Word *right = 0) : index_(index), text_(text), count_(count), left_(left), right_(right)

 2.禁用复制构造函数和复制函数

## Sentence类

类成员：

成员类型|成员名称|成员作用
-------|-------|-------|
vector&lt;Word*>|words_|Word* 数组,指向句子中包含的词，无重复词
vector&lt;String>|token_|string 数组，存储句子中词的字符串，有重复词
vector&lt;Tag>|tags_|？

## Word2Vec类

定义 SentenceP 为 std::shared_ptr&lt;Sentence>，指向句子类

定义 Vector 为 vector&lt;float>

类成员：

成员类型|成员名称|成员作用|备注
-------|-------|-------|-------|
vector&lt;Vector>|syn0_|参数|无
vector&lt;Vector>|syn1_|参数|无
vector&lt;Vector>|syn0norm_|参数|无
vector&lt;Vector>|syn1neg_|参数|negative sampling
vector&lt;int>|unigram_|参数|negative sampling
unordered_map&lt;String, WordP>|vocab_|构成词典|
