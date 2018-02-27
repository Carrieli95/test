# -
相关论文调研结果
一、信息抽取的发展过程理论发展过程人工规则——>监督学习——>半监督学习和无监督学习可提取的实体内容演变：三个实体。人名，地点，组织机构职业职责。时间，金额，百分比，邮箱，电话等数字信息。医学领域中的蛋白质，药品和化学品。二、应用方式（理论）2.1 半监督学习相比于全监督学习来说，半监督学习仅仅需要提供少量的标注语料。于一开始传入这些有特点的语料，相当打开了机器的开关。基于这样的初始数据，机器开始检索文本中相对应的信息，如名称，并进行提取。同时，进一步找出示例中的共同点。必要因素——示例+规则（1）例子：生成书名和作者对应的二元组示例——初始传入样板{Isaac Asimov, The Robots of Dawn}规则——规定文本描述呈现[A-Z][A-Za-z .,&][A-Za-z.]格式的即为书名。 比如：大写设为A，其他为a，数字为0，标点为‘-’x = "G.M.": GetPattern(x) = "A-A-"x = "Machine-223": GetPattern(x) = "Aaaaaaa-000"进行简化后x = "G.M.": GetSummarizedPattern(x) = "A-A-"x = "Machine-223": GetSummarizedPattern(x) = "Aa-0"这样做的前提假设是，“同一个网站，文本描述的方式几近相同”。（2）实体识别示例——传入样本{Maury Cooper, a vice president at S&P}。（格式模板 {spelling,context}）规则——比如（rule 1: if the spelling is “New York” then it is a Location; rule 2: if the spelling contains “Mr.” then it is a Person; rule 3: if the spelling is all capitalized then it is an organization）若spelling符合上面的规则，则后面的context就会累积储存起来。其中，第一步传入的样本示例可以选择人为构想，也可以采用已有的NER系统进行生成。2.2 无监督学习首先，词汇聚类是无监督学习的主要方式。对同一领域的文本进行处理，我们可以得到一类具有相似特征的特征词组，换句话说，就是特定领域的代表词。利用开源包时，如WordNet，将文本以话题形式分开标签。新闻，快报，日常用语等。获得聚类词库后进行匹配搜索，有三个主要原则：a. 单词去尾（英语单复数问题，应用到汉语中，是否可以将火灾——>火？）b. 模糊分类（‘着火了’ 和 ‘着火’ Frederick 和Frederik可以互相匹配）c. 发音的模糊分类（英语中‘语音编码’，如Lewinsky和Lewinskey）其次，设定特征函数。      以一个三维特征函数为例：1）单词以大写字母开头返回true，其他返回false。2）储存单词长度3）全小写模式这样就得到一个储存信息的三元组，然后将其映射至数值空间。三、应用方法（实践）四、现有问题
