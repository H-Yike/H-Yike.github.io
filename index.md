# HYK的Github page
## PART1 课堂笔记 
### 1.1  A few questions
+ What is gene？  
+ Which organism has the largest genome?  
+ Why do humans have so few genes?  
  --Because percent of genome not coding for protein.  
  
### 1.2 Sequencing technologies 
### 1.3 算法(algorithm) & 模型(model)  
算法是指一种逻辑规则指定的流程，用于解决问题的思想和方法。  
模型是在训练数据上运行算法后保存的“东西”，它表示用于进行预测所需的规则、参数和任何其他特定于算法的数据结构。

## PART2 About homework  
### 1.1) Vim的使用  
-> 打开docker app   
-> cmd输入 **docker exec -it Huang_YK bash** (Huang_YK 是我的container名称)  
-> 输入 vim 文件名（存在或不存在都可)  
-> i:INSERT模式，可输入文字  
-> Esc退出输入模式，进入命令模式  
-> 输入“:”，将进入底线命令模式
-> :w 保存  :q 退出vim :wq 保存并退出 :q! 强制退出

### 1.2) 如何把网络学堂下载到host(windows 11)里的文件共享给Docker(Linux)?  
-> 打开cmd  
-> docker cp 文件所在的宿主机路径 容器名称:/container内路径
  
### 1.3) Github, github desktop与 VScode  
1. 在Github上创建repository  
2. 在Github desktop 上 File->Add local repository  
3. 用VScode打开  
4. 可以修改或添加文件（通过改文件名后缀可以直接改格式）  
5. Ctrl+s快速保存  
6. 在Github desktop 上 **Commit to main**  
7. Push to origin

## PART3 本学期Bioinformatics的学习计划  
 **课前预习!**  

| 时间  | 学习内容 |  
| :---: | :------:|  
| 第2-3周 |Linux 私房菜，chapter 1-3，Blast|    
|第4周|NGS,Mapping,R语言基础教程|  
|第5周|DNA-seq,R语言基础教程|  
|第6-7周|RNA-seq,GO,KEGG,R语言基础教程|    

后续计划将根据前几周的情况安排。

