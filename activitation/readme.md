激活函数要求:单侧抑制,宽阔的兴奋域,稀疏激活

sigmoid:
  优点:求导方便
  缺点:梯度消失,输出不是zero-center的,幂运算比较耗时

tanh:解决了zero-center的问题

relu：
  优点：解决了梯度消失，计算速度快，收敛速度快
  缺点：输出不是zero-center的,死区问题避免设置很大的learning_rate

1.稀疏性在70%-85%之间比较好.过分的稀疏会减少模型的有效容量,导致模型无法学到有效特征.

relu好处:更快的收敛,缩小了是否进行预训练的代沟.


参考:http://www.cnblogs.com/neopenx/p/4453161.html

参考:https://zhuanlan.zhihu.com/p/25110450
