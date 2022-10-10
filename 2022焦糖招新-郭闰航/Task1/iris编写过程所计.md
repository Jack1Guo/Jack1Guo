## train_test_split

能够将按照用户的需要指定划分为训练集和测试集

### 用法

（1）引入库

`from sklearn.model_selection import train_test_split`

（2）读入数据

`X_train,X_test,y_train,y_test=train_test_split(train_data,train_target,test_size=0.25, random_state=0,stratify=y) `

* train_data：待划分的样本特征集合	

* X_train：划分出的训练数据集数据
* X_test:划分出的测试数据集数据
* y_train:划分出的训练数据集的标签
* y_test:划分出的测试数据集的标签

* train_target：所要划分的样本结果

* test_size：样本占比，如果是整数的话就是样本的数量，若在0~1之间，为测试集样本数目与原始样本数目之比；若为整数，则是测试集样本的数目。

* random_state：是随机数的种子。

* 随机数种子：其实就是该组随机数的编号，在需要重复试验的时候，保证得到一组一样的随机数。比如你每次都填1，其他参数一样的情况下你得到的随机数组是一样的。但填0或不填，每次都会不一样。

## iris数据集

这个数据集里一共包括150行记录,其中前四列为花萼长度，花萼宽度，花瓣长度，花瓣宽度等4个用于识别鸢尾花的属性，第5列为鸢尾花的类别（包括Setosa，Versicolour，Virginica三类）.

（1）调用库

`from sklearn import datasets`

（2）生成数据集

`iris = datasets.load_iris()`

- 这个 iris 数据集里有 5 个属性，一个是描述，另外 4 个是：`data`、`feature_names`、`target`、`target_names`，分别就是属性值、属性名、类别、类别名

（3）获取属性

- dt = iris.data  *值*

  tg = list(iris.target) *类别* 

  fn = list(iris.feature_names) *属性*

  tn = list(iris.target_names) *属性值*

## relu激活函数

x<=0时，输出值为0；x>0时，输出为输入本身。

用法：`torch.nn.ReLU()`

# 编译问题

* 'int' object has no attribute 'softmax'

  使用`nn.softmax(input,dim = ?)`会导致这个报错

  正确的使用softmax应该有下面两种情况：`nn.Softmax()` `nn.functional.softmax(input)`

  但是发现无论哪种情况 ，后面指定纬度dim=？ 的情况下，系统都会报错。

  经网上资料查询，softmax函数在默认条件下的dim=1，这就满足了所需的dim=1.当括号里面没有设置维度变量的时候，程序就可以正常运行。
