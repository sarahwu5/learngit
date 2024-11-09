# 1
在 Bash 中，包含空格的目录名需要用引号或转义字符来处理。  
这样是错误的
> $ cd Program Files  
bash: cd: too many arguments  

这样是正确的  
`cd "Program Files"`  
`cd Program\ Files`

# 2
命令中目录用的是左斜线/，转义字符用的是右斜线\

# 3
在使用pycharm过程中，文件名有不一样的颜色。
绿色：已经加入版本控制暂未提交
红色：未加入版本控制
蓝色：加入版本控制，已提交，有改动
白色：加入版本控制，已提交，无改动
灰色：版本控制已忽略文件
黑色：目录中文件不为空
暗绿色：目录中文件为空

# 4

```markdown
$$
\left[\begin{array}{l}
r_1 \\
r_2 \\
r_3
\end{array}\right] = \left[\begin{array}{l}
b_1 \\
b_2 \\
b_3
\end{array}\right] + \left[\begin{array}{lll}
w_{11} & w_{12} & w_{13} \\
w_{21} & w_{22} & w_{23} \\
w_{31} & w_{32} & w_{33}
\end{array}\right] \left[\begin{array}{l}
x_1 \\
x_2 \\
x_3
\end{array}\right] \quad (1.20)
$$
```

- `\left[` 和 `\right[` 用于创建大小合适的方括号。
- `\begin{array}{l}` 和 `\end{array}` 用于定义一个数组环境，其中 `l` 表示左对齐。
- 每一行的元素之间用 `&` 分隔，行与行之间用 `\\` 分隔。
- `w_{11} & w_{12} & w_{13}` 表示矩阵中的一行元素。
- `+` 表示矩阵的加法。
- `\quad` 表示在等号两边添加一些空格，使得等式更加美观。

这段代码在Markdown中将显示为一个矩阵等式，其中包含向量和矩阵的加法。请确保你的Markdown渲染器支持LaTeX语法，以便正确显示这些公式。如果你的渲染器不支持LaTeX，这些代码将不会被正确渲染。

# 5
\quad 和 \qquad 是LaTeX命令，用于在文本中添加水平空格。它们的主要区别在于添加的空间大小：

\quad 插入一个固定宽度的空间，通常等于当前字体大小的一个空格的宽度。
\qquad 插入的空间是 \quad 的两倍宽。