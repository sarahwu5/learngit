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