# markdown常用语法
http://www.markdown.cn/
## 1. 标题
markdown 有6级标题语法，建议使用时，在“#”后面加上一个空格
````
#       一级标题
##      二级标题
###     三级级标题
####    四级级标题
#####   五级级标题
######  六级级标题
````

## 2. 列表
### 2.1 有序与无序
**有序列表：**直接在文字前面加上 1. 2. 3. 符号 ，并且与文字之间需用空格隔开
**无序列表：**在文字之前加上 “-” 或 “*” 或“+”

**无序**
- 一
- 二
- 三

**有序**

1. 一
2. 二
3. 三

### 2.2 列表项目中存在多个段落。每个段落要用4个空格或者一个制表符
1. This is a list item with two paragraphs. Lorem ipsum dolorsit amet, consectetuer adipiscing elit. Aliquam hendreritmi posuere lectus.

    Vestibulum enim wisi, viverra nec, fringilla in, laoreetvitae, risus. Donec sit amet nisl. Aliquam semper ipsumsit amet velit.
2.  Suspendisse id sem consectetuer libero luctus adipiscing.
### 2.3 列表项目中存在区域引用。区域应用要缩进。使用8个空格或者2个制表符
1. This is a list item with two paragraphs. Lorem ipsum dolorsit amet.

       > Vestibulum enim wisi, viverra nec, fringilla in, laoreetvitae, risus.

2. Suspendisse id sem consectetuer libero luctus adipiscing.

### 2.4 列表项目中若存在。 数字与句号组合问题，请用 数字+\+句号 转译。如：464\.

## 3. 加粗 斜体
加粗：采用“\*\*文字\*\*” 格式 。对文字进行加粗 如：**加粗**
斜体：采用“\*文字\*” 格式 。如:*斜体*
## 4. 分隔线 （ 另起一行，采用三个以上“-”，“_”，“*” 。如 ---，+++，***符号）

## 5. 反斜杠  （采用 \ 对特殊符号进行转译）
## 6. 链接
## 7. 代码框
采用 \`代码\` 格式

`public class aa{public aa(){}}`
## 8. 区域引用
采用> 符号，在每行前面添加>。
- 可以嵌套。保证每一个层级的符号> 和相同层级。比如第二层>>
- 引用符号，同时可以使用其他符号，比如列表，标题等。
- 引用符号，可以在每个段落首行前面添加引用符号即可。