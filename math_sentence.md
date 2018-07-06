## 20180706

-- linear model for KLIEP the optimization problem -- convex function and the feasible set is convex, equality constrains. So I turn to read the book.    

仿射集，集合内几个点的权值之和线性组合为1，依旧在集合内； 

A set $C\subseteq R^n$ is affline if the line through any two distinct points in $C$ lies in $C$.

(generalized to more points and in mathematical language):
a set $C$ is a affine set if for any distinct point $x_1,x_2,...,x_k \in C$, any $\theta_1,\theta_2,...,\theta_k \in R$, and $\theta_1+\theta_2,...+\theta_k=1$, 
we have $\theta_1x_1+\theta_2x_2,...+\theta_kx_k\in C$

凸集，仿射集的特例，权值必须大于0； 凸函数，定义域是凸集，而且任意两点直接的对应的弦大于曲线。

roughly, speaking, a set is convex set if every point in the set can be seen by every other point in the set. 
-- along an unobstructed straight path between them, where unobstructed means lying in the set.

a set $C\subseteq R^n$ is a convex set if for any distinct point $x_1,x_2,...,x_k \in C$, any $\theta_1,\theta_2,...,\theta_k>0$, and $\theta_1+\theta_2,...+\theta_k=1$, we have $\theta_1x_1+\theta_2x_2,...+\theta_kx_k\in C$

The convex hull of a set $C$, denoted $conv C$, is the set of all convex combinations of points in $C$: 
$conv C=\{\theta_1x_1+\theta_2x_2,...+\theta_kx_k|x_i\in C,\theta_i\geq0, i=1,...,k,\theta_1+\theta_2,...+\theta_k=1\}$



下降方法（函数值下降），三步：方向，步长，更新； 梯度下降，就是方向沿着负梯度走；

​	determine a descent direction; choose a step size; update

牛顿方法：很复杂，二阶梯度倒数（<u>哪个优先级先？为啥二阶？</u>）乘以一阶梯度，<u>作为Newton step. 不是方向吗？</u>

等式约束（P521 Chapter 10）: 回看P224 KKT optimality condition.  <u>KKT矩阵非奇异（可逆，满秩）等效的东西，为什么取这么多名字？？</u>  两种方法，降级为无约束问题，通过消掉等式约束项，或者解决对偶问题


