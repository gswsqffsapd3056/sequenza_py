# Module sequenza_py
使用Python部分重构sequenza R中的函数

## 重构理由
在使用 scarHRD `library(sequanza)` 处理大数据量NGS数据时，流程较容易中断，报出VROOM相关错误。  
提升VROOM size后，出现C 库bad-malloc提示。无法使用全部数据生成scarHRD结果。  
尝试使用python重构其中最容易中断的，读取seqz.gz并预处理步骤。

## 主要实现方法
1. R 中调用 reticulate 指定python环境，使用python重构preprocessing read.seqz.chr 函数，做数据交互。 或尝试简单更改scarHRD导入默认的sequenza参数
2. `environment(read.seqz.chr) <-  environment(sequenza::read.seqz.chr)` 替换被scarHRD library到环境中的sequenza函数
3. 调试运行
