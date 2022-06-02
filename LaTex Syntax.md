


|Index|Syntax|Effection|
|:-:|:-:|:-:|
|1|\dfrac{1}{2}|$\dfrac{1}{2}$|
|2|a \pm b|$a \pm b$|
|3|\sqrt{b^2-4ac}|$\sqrt{b^2-4ac}$|
|4|\Gamma|$\Gamma$|
|5|\quad\forall|$\quad\forall$|
|6|\in\mathbb{N}|$\in\mathbb{N}$|
|7|\dots|$\dots$|
|8|\sum_{i=1}^{n}i|$\underset{i=1}{\overset{n}{\sum}}$|
|9|\infty|$\infty$|
|10|\underset{x \rightarrow \infty}{\lim}|$\underset{x \rightarrow \infty}{\lim}$|
|11|\int_{a}^{b}|$\int_{a}^{b}$|
|12|\partial|$\partial$

#### 行内公式
- `$ x = \cfrac{-b \pm \sqrt{b^2-4ac}}{2a} $` $ x = \cfrac{-b \pm \sqrt{b^2-4ac}}{2a} $
- `$ 1+2+3+\dots+(n-1)+n=\frac{n(n+1)}{2} $` $ 1+2+3+\dots+(n-1)+n=\frac{n(n+1)}{2} $
- `$ \overbrace{(a+b)+\underbrace{c+d}_{\text{虚数}}}^{\text {复数}}+(e+f)+\underline{(g+h)} $` $ \overbrace{(a+b)+\underbrace{c+d}_{\text{虚数}}}^{\text {复数}}+(e+f)+\underline{(g+h)} $
#### 块级公式
- $$ \Gamma(n)= (n-1)! \quad\forall{n} \in\mathbb{N} $$
- $$\int_{a}^{b} f(x)dx=F(b)-F(a)$$
- $$ \frac{\partial f(x)}{\partial x} = x^2 $$

```
$$ \begin{equation}
f(x)=
\begin{cases}
    x+2y^2-z+\frac{1}{x} & x=10\\
    -x & x < 1
\end{cases}
\end{equation}$$
```
$$ \begin{equation}
f(x)=
\begin{cases}
    x+2y^2-z+\frac{1}{x} & x=10\\
    -x & x < 1
\end{cases}
\end{equation}$$
```
$$\begin{array}{ccc}
 a_{11} &  a_{12} & a_{13}   \\
  a_{21}&  a_{22} & a_{23}  \\
  a_{31}&  a_{32} & a_{33}  
\end{array}$$
```
$$\begin{array}{ccc}
 a_{11} &  a_{12} & a_{13}   \\
  a_{21}&  a_{22} & a_{23}  \\
  a_{31}&  a_{32} & a_{33}  
\end{array}$$
```
$$\begin{vmatrix} 
      a & b \\
      c & d 
\end{vmatrix}$$
```
$$\begin{vmatrix} 
      a & b \\
      c & d 
\end{vmatrix}$$



```
$$\begin{Vmatrix} 
      a5 & b \\
      c & d 
\end{Vmatrix}$$
```
$$\begin{Vmatrix} 
      a5 & b \\
      c & d 
\end{Vmatrix}$$



```
$$\begin{equation}
\begin{bmatrix} 
      a4 & b \\
      c & d 
\end{bmatrix}
\end{equation}$$
```
$$\begin{equation}
\begin{bmatrix} 
      a4 & b \\
      c & d 
\end{bmatrix}
\end{equation}$$




```
$$\begin{equation}
\begin{pmatrix} 
      a2& b \\
      c & d 
\end{pmatrix}
\end{equation}$$
```
$$\begin{equation}
\begin{pmatrix} 
      a2& b \\
      c & d 
\end{pmatrix}
\end{equation}$$


```
$$\begin{equation}
\begin{Bmatrix} 
      a3 & b \\
      c & d 
\end{Bmatrix}
\end{equation}$$
```
$$\begin{equation}
\begin{Bmatrix} 
      a3 & b \\
      c & d 
\end{Bmatrix}
\end{equation}$$

- `$ \underset{e}{\overset{f}{_a^b\sum^d_c}}$` $ \underset{e}{\overset{f}{_a^b\sum^d_c}}$

- `$\underset{i=1}{\overset{n}{\sum}}$` $\underset{i=1}{\overset{n}{\sum}}$

$\overset{n}{\underset{i=1}{\sum}}$

$\underset{i=1}{\sum}$

$\prod$

$\beta$

$\Alpha$

$\Sigma$

$\pi$

$\infty$

$\epsilon$

$\omega$

```latex
$\underset{e}{\overset{f}{\sideset{_a^b}{_c^d} \prod}}$
```