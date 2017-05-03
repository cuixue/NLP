# NLP

cs224d: http://blog.csdn.net/han_xiaoyang/article/details/51567822
	
对于全连接:
参考 http://ufldl.stanford.edu/wiki/index.php/%E5%8F%8D%E5%90%91%E4%BC%A0%E5%AF%BC%E7%AE%97%E6%B3%95 ,了解反向传导的含义,传导在传残差.
$$\delta_i^{(l)} = (\sum\limits_{j = 1}^{{s_{l + 1}}}{W_{ji}^{(l)}\delta _j^{(l + 1)}}){f^{'}}(z_i^{(l)})$$

其中,f 为激活函数. 这样,在很多层反向传导的时候，就会发生梯度爆炸和梯度消失. 对于激活函数 tanh' < 1 ; sigmoid' < 0.25.

对于RNN：
参考 http://blog.csdn.net/u011414416/article/details/46724699 和 http://www.wildml.com/2015/10/recurrent-neural-networks-tutorial-part-3-backpropagation-through-time-and-vanishing-gradients/

其中，我们只需要计算三个参数,分别与 输出, 输入,隐层相连的三个参数,由于输入和隐层的参数会往后面传,因此在反向求导时,对于某个时刻的参数计算要依赖于其后面的所有部.因为参数是共享的,所以在计算每个参数的时候,要考虑到所有步.

由于此时也会出现连乘的情况.因此,会出现梯度消失.

 ![image](https://github.com/cuixue/NLP/blob/master/RNN.png)
 
 在考虑rnn时,每一个hidden_states都是一个rnn过程,相当于是一个切片. 当然,在矩阵计算时,这些都包含其中了.
 
 对于LSTM:
 
 这里面引入了几个门.这些门的组合控制了，我们需要传导什么信息.
  ![image](https://github.com/cuixue/NLP/blob/master/gates.png)
 为什么 会
  解决梯度消失的问题呢? 参考:https://www.quora.com/How-does-LSTM-help-prevent-the-vanishing-and-exploding-gradient-problem-in-a-recurrent-neural-network
  
  在lstm中，cell的激活函数是 identity function.
  
 memory cell:
$$c_t^l = i \otimes g + f \otimes c_{t - 1}^l$$

假设在时间t步，我们有残差$\frac{{\partial L}}{{\partial c_t^l}}$,根据链式法则,
$$\frac{\partial }{{\partial c_{t - 1}^l}}: = \frac{\partial }{{\partial c_{t - 1}^l}} + f \otimes \frac{{\partial L}}{{\partial c_t^l}}
$$

这里,forget get deceides how long to remain information


这里，rnn的优化方法,主要有两类:BPTT和RTRL.其中,BPTT是整个sequence都结束,更新一次参数.而RTRL是实时的,每个item更新一次参数.
参考: http://www.dlsi.ua.es/~mlf/nnafmc/pbook/node29.html




