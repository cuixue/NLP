# NLP

cs224d: http://blog.csdn.net/han_xiaoyang/article/details/51567822
	
对于全连接:
参考 http://ufldl.stanford.edu/wiki/index.php/%E5%8F%8D%E5%90%91%E4%BC%A0%E5%AF%BC%E7%AE%97%E6%B3%95 ,了解反向传导的含义,传导在传残差.
$$\delta_i^{(l)} = (\sum\limits_{j = 1}^{{s_{l + 1}}}{W_{ji}^{(l)}\delta _j^{(l + 1)}}){f^{'}}(z_i^{(l)})$$

其中,f 为激活函数. 这样,在很多层反向传导的时候，就会发生梯度爆炸和梯度消失. 对于激活函数 tanh' < 1 ; sigmoid' < 0.25.

对于RNN：
参考 http://blog.csdn.net/u011414416/article/details/46724699 和 http://www.wildml.com/2015/10/recurrent-neural-networks-tutorial-part-3-backpropagation-through-time-and-vanishing-gradients/

其中，我们只需要计算三个参数,分别与 输出, 输入,隐层相连的三个参数,由于输入和隐层的参数会往后面传,因此在反向求导时,对于某个时刻的参数计算要依赖于其后面的所有部.因为参数是共享的,所以在计算每个参数的时候,要考虑到所有步.

 ![image](https://github.com/cuixue/NLP/RNN.png)






