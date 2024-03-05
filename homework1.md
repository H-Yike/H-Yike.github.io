## 1.统计文件行数及字符数
 //查看文件  
 cat test_command.gtf 
  
  //文件行数  
wc -l test_command.gtf  
   -> **8 test_command.gtf**   
//文件字符数 
wc -c test_command.gtf==  
   -> **636 test_command.gtf**   
## 2.利用 grep 等命令尝试筛选并输出示例文件中以 chr_ 起始，并且基因id为 YDL248W 的行。    
  
  **grep -E 'chr_.*YDL248W' test_command.gtf**   

chr_IV  ensembl gene    1802    2953    .       +       .       gene_id "YDL248W"; gene_version "1";    
chr_IV  ensembl transcript      802     2953    .       +       .       gene_id "YDL248W"; gene_version "1";    
chr_IV  ensembl start_codon     1802    1804    .       +       0       gene_id "YDL248W"; gene_version "1";  

## 3.利用 sed 等命令将示例文件中的 chr_ 替换为 chromosome_ 并输出每行的第1，3，4，5列。（无需改动原文件，只输出结果）
sed 's/chr_/chromosome_/g' test_command.gtf  

awk '{print $1, $3, $4, $5}' test_command.gtf  


## 4.互换示例文件的第2列和第3列，并且对输出结果利用 sort 命令依照第4和第5列数字大小排序，将最终结果输出到result.gtf文件中
awk '{temp=$2; $2 = $3; $3 = temp; print;}' test_command.gtf | sort -k 4,5 -n > result.gtf  

## 5.更改示例文件的权限，使得文件所有者及所在用户组用户可读、写、执行而其他用户只可读，展示权限修改前后的权限变化。  
//查看权限  
ls -hl test_command.gtf  
//指令    
chmod 774 test_command.gtf   
//前后变化    -rwxr--r--   ->    -rwxrwxr--