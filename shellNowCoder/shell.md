### 1文件行数

```shell
wc -l < nowcoder.txt
# 这个命令使用 wc 命令来统计文件的行数，-l 选项表示只统计行数。< nowcoder.txt 是重定向输入，将文件内容作为 wc 命令的输入。
cat nowcoder.txt |wc -l
# 这个命令先使用 cat 命令将文件内容输出到标准输出，然后通过管道将输出作为 wc 命令的输入，同样使用 -l 选项来统计行数。
sed -n '$=' nowcoder.txt
# 这个命令使用 sed 命令来处理文本，-n 表示不输出模式空间的内容，$= 表示打印最后一行的行号。
grep -n "" nowcoder.txt | awk -F: '{print }' | tail -n1 | awk -F: '{print $1}'
# 这个命令首先使用 grep 命令查找所有的行（相当于匹配空字符串，即所有行），-n 选项表示同时输出行号。然后通过管道将输出结果交给 awk 命令处理，-F: 表示以冒号为分隔符，'{print }' 打印行号，接着通过管道将结果交给 tail 命令取最后一行，最后再通过管道将结果交给另一个 awk 命令，再次以冒号为分隔符打印行号。
awk '{print NR}' nowcoder.txt | tail -n1
# 这个命令使用 awk 命令打印每一行的行号，'{print NR}' 表示打印行号，然后通过管道将结果交给 tail 命令取最后一行。
awk 'END{print NR}' nowcoder.txt
# 这个命令使用 awk 命令，在处理完整个文件后，END{} 中的命令会被执行，print NR 表示打印当前的行号。
```

### 2 打印文件最后五行

```shell
tail -n 5 nowcoder.txt

# 查看文件的前5行，可以使用head命令，如
head -5 nowcoder.txt
head -n 5 nowcoder.txt 
# 表示输出文件开头的5个字节；
head -c 5 nowcoder.txt
head 5 nowcoder.txt
# 查看文件的后5行，可以使用tail命令，如：
tail -5 nowcoder.txt
tail -n 5 nowcoder.txt
# 实时输出文件的最新更新内容
tail -f nowcoder.txt
# 输出文件的最后5行
tail -n 5 nowcoder.txt
# 输出从第5行开始到文件结尾的内容；
tail -n +5 nowcoder.txt
# 输出从倒数 第五行开始到文件结尾的内容
tail -n -5 nowcoder.txt
# 不加任何参数，默认输出10行
tail nowcoder.txt 
# 表示输出文件最后5个字节
tail -c 5 nowcoder.txt
# 查看文件中间一段，你可以使用sed命令，如：
sed -n ‘5,20p’ nowcoder.txt
# 这样你就可以只查看文件的第5行到第20行。
```

