
## 3 ways to imposing fairness :

1.pre-processing or extracting representions from the data to remove undesired biases

2.imposing fairness constraints into the learing mechanism so that produce fair outputs

3.post=processing the outputs of a model in order to make them fair



## Causal Baysian Networks

*causal effect* 

![image-20210309163705201](C:\Users\qtk\AppData\Roaming\Typora\typora-user-images\image-20210309163705201.png)

如上图所示，包含因果路径*causal path*$A\rightarrow Y$ 和无因果路径*non-causal path* $A\leftarrow C\rightarrow Y$

$p(Y|A)$  和 $p_{\rightarrow A}(Y|A)$ 的区别：

​		条件分布$p(Y|A)$ 衡量两条路径从$A$ 到 $Y$ 的信息（$A\rightarrow Y$ and $A\leftarrow C\rightarrow Y$ ）。

​		而 $A$ 到 $Y$ 的因果效应 *causal effect* 表示为$p_{\rightarrow A}(Y|A)$， 只衡量$A\rightarrow Y$ 的因果路径上的信息。

因此 *causal effect* 可以看作加了（因果路径限制条件）的条件分布。

![image-20210309163723778](C:\Users\qtk\AppData\Roaming\Typora\typora-user-images\image-20210309163723778.png)

*path-specific effect*

$Y_{\rightarrow A=a}$  定义为分布为 $p(Y_{\rightarrow A=a})$ 的**随机变量**，而 $p(Y_{\rightarrow A=a})$ = $p_{\rightarrow A=a}(Y|A=a)$， $Y_{\rightarrow A=a}$ 称作潜在结果，简记为$Y_{\rightarrow a}$ ，$Y_{\rightarrow a}$  是一个随机变量！

可以扩展潜在结果，使得允许沿着不同的causal path 分离 causal effect

考虑上图用CBN描述的大学录取场景：A 表示性别 Q资格 D院系 Y录取

 causal path $A\rightarrow Y$ 表示性别对录取结果的直接影响，两个人D，Q都一样，但能根据他们的性别导致区别对待。间接路径$A\rightarrow Q\rightarrow Y$ ，$A\rightarrow D\rightarrow Y$ 表示性别不同对资质和所报院系的影响，以及资质和所报院系对最终录取结果的影响

我们用$ A=a ,A=\bar{a} $分别表示女性和男性申请人，*path-specific potent outcome* 指定路径潜在结果 $Y_{\rightarrow \bar{a}}(Q_{\rightarrow a}, D_{\rightarrow a})$ 定义为分布等同于给定A下Y的条件分布，限制为causal path：A到Y使用$\bar a $另外两条使用$a$

它的分布  $p( Y_{\rightarrow \bar{a}}(Q_{\rightarrow a}, D_{\rightarrow a}) )=\sum_{Q,D}p(Y|A=\bar a ,Q,D)p(Q|A=a)p(D|A=a)$

$A=\bar a$ 关于 $A=a$ 的*path-specific effect* 定义为   `关于：with respect to`

![image-20210309180450925](C:\Users\qtk\AppData\Roaming\Typora\typora-user-images\image-20210309180450925.png)

> $p(Y_{\rightarrow \bar{a}}(Q_{\rightarrow a}, D_{\rightarrow a}))$  就是 $p(Y|A)$ 的causal effect， 只不过加了限制条件：A到Y使用$\bar a $另外两条使用$a$
>
> $p(Y_{\rightarrow a})$ 就是$p(Y|A=a)$  的causal effect

*path-specific counterfactual distribution*

我们考虑上一节的实际例子：一个女性个体没有被录取，我们可以回答相反情况下她是男性个体情况下是否被录取，沿着路径$A\rightarrow Y$。

为了理解分布 $p(Y_{\rightarrow \bar{a}}(Q_{\rightarrow a}, D_{\rightarrow a})|a^n=a,q^n,d^ny^n)$  能够被计算

![image-20210311142616925](fairness machine learing.assets/image-20210311142616925.png)
