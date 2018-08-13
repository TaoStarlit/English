# mathematic for CS

|want|how|attention|
|--|--|--|
|east north upward|let the x-axis be horizontal pointing to the East, (omit be to the), the ~ horizontal pointing north, ~ pointing vertically upwards|be and the are vertical upwards|
|movement, straight line, certain distance, vector|a ~ along a ~ for a ~ is called ~|https://www.englishgrammar.org/subject-attributes/   attribute-a prepositional phrase|
|plane, not same direction|P must not point in the same direction with Q||
|3 points, same line, plane|which are not all on the same line determine a plane|be not all on the same line|
|r=2q into equaton|Substituting this into the equation of the 2nd plane||
|1-s-t,s,t PQR|the part of the plane where all 3 parameters ~ ~ are between 0 and 1 is exactly the triangle with corners PQR| where all 3 parameters ... is exactly the triangle with corners P Q R|
|(2/3,1/3)-->(2,1)|You can avoid these by simply stretching the direction vector.||




## Analytic Geometry in three dimensions; vector spaces
An example would be to let the x-axis be horizontal pointing to the East, the y-axis horizontal pointing North, and the z-axis pointing vertically upwards.

15. vector and line movement

A movement along a straight line for a certain distance is call vector.

$$\left(
\begin{array}{ccc}
v_1\\
v_2\\
v_3
\end{array}\right)
$$

any 2 points $P$ and $Q$ determine a vector $\vec{PQ}$ whose coordinates are 

$$\left(
\begin{array}{ccc}
p_1-q_1\\
p_2-q_2\\
p_3-q_3
\end{array}\right)
$$

16. plane

The parametric representation of a plane has the form: $X=P+s \vec v+t \vec w$, where P is a point in space, and $\vec v$ and $\vec w$ are vectors (neither of which is the null vector). Furthermore, \vec w must not point in the same direction as \vec v, or otherwise only a line is generated.
Three points P, Q and R which are not all on the same line determine a plane:
$X=P+s\cdot \vec{PQ} + t \cdot  \vec{PR}$

17. intersection tasks

find the intersection line between 2 planes.

consider 2 planes $X_{s,t}$ $Y_{r,q}$, we equate them and transform them into three linear equations(3 axes) for the four unknown(two for each line). We solve the system with Gaussian elimination: s t r q for 1st to 4th column:

$\left(\begin{array}{ccc}1&-1&0&-1\\ 0&-1&-1&0\\0&0&-2&1\end{array}\right|\left.\begin{array}{ccc}-1\\1\\4\end{array}\right)$

we find that q can be chose freely and r computes to $-2+q/2$.  (get the $q$ and $r_q$, substituting to $Y_{r,q}$ we get the line) Substituting this into the equation of the 2nd plane $Y_{r,q}$, we obtain: 
we obtain which simplifies to

18. two point description of a line
$X=P+s\cdot\vec{PQ}=(1-s)\cdot P + s\cdot Q$ -- a convex combination of points -- another term for this is weighted average

19.three-point descriptioi of a plane: 
$X=P+s\cdot\vec{PQ}+t\cdot\vec{PR}$

$X=(1-s-t)\cdot P+s\cdot Q+t\cdot R$

The part of the plane where all three parameters s, t and 1-s-t are between 0 and 1 is exactly the triangle with corners P, Q and R.


20. vector space

the operations and laws of vectors in 10 and 11 on the last handout.  Any structre that carries these 2 operations(vector movement, scalar multification) and satisfies these laws is called a vector space.

21. Subspaces: if $\vec v$ is an element of some vector space then we can generate a subspace by considering all vectors of the form $s\cdot\vec v$. This contains the null vector ($\vec 0=0 \vec v$), is closed under addition, becauce: $a\vec v+ b\vec v=(a+b)\vec v$, and is closed under scalar multiplication because: $s(a\vec v)=(as)\vec v$

The same would be true if we took 2 vectors \vec v and \vec w and formed all expressions of the form $s\vec v + t \vec w$. Another way of looking at our parametric representations, then, is to say that we pick a point and allow all movements from a subspace to act on this point. This construction leads to what in general is called an affine subspace. In other words, lines and planes are affine subspaces of 2D/3D.

22. Bases. 

A set of *generators* ($s\vec v + t \vec w$) that can not be made any smaller is called a **basis** of the subspace. The number of elements of a basis is called the **dimension** of the subspace.


23. Codes: Subspaces in GF(2)^2 are used as linear codes in coding theory.

24. Practical advice.

note: sometimes your computation will produce a direction vector with fractions as coordinates. You can avoid these by simply stretching the direction vector.


## 1 Linear System and Gaussian Elimination
linear:
# exponent
An equation with one or more unknowns is called linear if the unknowns appear on their own, without exponent
## 2 Special Case
1. contradictory equation: no solution
2. irrelevant equation: the equation does not constrain the value of x in any way

(addition is commutative)
x+ (y+z) = (x+y) +z (addition is associative)
x ∗ y = y ∗ x (multiplication is commutative)
x ∗ (y ∗ z) = (x ∗ y) ∗ z (multiplication is associative)
x ∗ (y+z) = x ∗ y+x ∗ z (multiplication distributes over addition)
x ∗ (y+z) = x ∗ y+x ∗ z (multiplication distributes over addition)

## 3 Analytic Geometry in the plane

|want|how|attention|
|--|--|--|
|coordinate system, axes,axis, horizontal/vertical|consist of, refer to as, (in __ direction)|3rd-person singular, passive struture, [i:z] and [is], the x-axis|  
|right angle, intersection point, origin|be at ~ to each other|the axes are at ~, their ~ is called the |

1. **Cartesian Coordiante System and points in the plane**. Recall the idea of a **coordinate system**:
2. 2 axes, x-axis and y-axis

it consists of 2 axes, usually referred to as the x-axis (in horizontal direction) and the y axis (in vertical direction).


3. coordinates 

A corrodinate system allows us to identify a point P in with its coordiante.

$$\left(\begin{array}{cc}
p_1 \\
p_2 
\end{array}\right)
$$

4. distance between $p$ and $q$:\
$d=\sqrt {(q_1-p_1)^2+(q_2-p_2)^2}$

5. vectors; straight line movement

$$ P'=P+\vec v $$

$$\left(\begin{array}{cc}
v_1 \\
v_2 
\end{array}\right)
$$

$$\left(\begin{array}{cc}
p_1+v_1 \\
p_2+v_2 
\end{array}\right)
$$


6. the length of vector, unit vector, null vectoer

$$|\vec v|=\sqrt {v_1^2+v_2^2}$$

$$
\frac {\vec v}{|\vec v|}=\left( \frac {v_1/|\vec v|} {v_2/|\vec v|}\right)
$$

7. factor/scalar.   scalar multiplication

$$
\frac 1 2 \vec v=\left(\begin{array}{cc}v_1/2 \\ v_2/2 \end{array}\right)
$$

8. representing straight lines (parametric representation + parameter): $X=P+s\cdot\vec v$ is called a **parametric representation**.   the **parameter** is s
9. Instersection two lines: the intersection point satisfies: X=Y.  the parameter $s$ and $t$ is the **unknows**. --> get the soltion --> s will tell us how far in the direction v *we have to move* from P in order to reac the point of intersection.

$$
\left(\begin{array}{cc}
p_1+sv_1\\
p_2+sv_2
\end{array} 
\right)
=X=Y=
\left(\begin{array}{cc}
q_1+tw_1\\
q_2+tw_2
\end{array} 
\right)
$$







# in 5.3 density fitting

## spherical, Gaussian

In the Gaussian kernel model, the Gaussian shape is spherical and its width is control by a single bandwidth parameter \sigma, which is chosen by cross-validation.

## Bernoulli
Bernoulli distribution is the discrete probability distribution of a random variable which takes the value 1 with probability $p$ and the value 0 with probability $q=1-p$

$$
P(x=k;p)=\left\{
\begin{aligned} 
& p,& k=1\\
& 1-p,& k=0
\end{aligned}    
    \right .
$$






The assigment:
1.3

the objectives of your research 
the significance
the aims of the stakeholder

paper:
imbalanced learning

bayesian network. 


Q function

inference       --->  estimation Q  

variational inference:

1.prior distrition  ---- not only gaussian
1. contional distribution
