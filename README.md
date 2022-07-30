# SM3
SM3密码杂凑算法的消息填充过程：
对长度为l（l<2^64）比特的消息m，SM3密码杂凑算法首先将比特“1”添加到消息的末尾，再添加k各“0”，k是满足l+k+1同余448模512的最小非负整数，然后再添加一个64位比特串，该比特串是长度l的二进制表示，填充后的消息m^' 的比特长度为512的倍数。
SM3密码杂凑算法的迭代压缩过程：
将填充后的消息m^' 按512b进行分组：m^'=B^((0)) B^((1))…B^((n-1))，其中n=（l+k+65）/512，对m^'按照如下方式迭代：FOG i=0 TO（n-1），V^((i+1))=CF（V^((i))，B^((i))）；ENDFOR。其中CF是压缩后函数，V^((0))为256b初始值IV，B^((i))为填充后的消息分组，迭代压缩的结果为V^((ｎ))
整个过程是消息输入后转码为ASCII形式，然后是数据填充和迭代压缩两个过程,消息扩展主要包括循环左移、异或、置换，消息经过扩展函数之后长度变成512比特，然后进行压缩，主要包括循环左移、模加运算、抑异或操作、布尔函数FFj、GGj、置换操作，经过迭代压缩之后最终输出哈希结果。

