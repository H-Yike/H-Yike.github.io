## 1.统计文件行数及字符数
test@bioinfo_docker:~/homework$ cat test_command.gtf  
    chr_IV  ensembl gene    1802    2953    .       +       .       gene_id "YDL248W"; gene_version "1";
    chr_IV  ensembl transcript      802     2953    .       +       .       gene_id "YDL248W"; gene_version "1";
    chromosome_IV   ensembl exon    1802    2953    .       +       .       gene_id "YDL248W"; gene_version "1";
    chromosome_IV   ensembl CDS     1802    950     .       +       0       gene_id "YDL248W"; gene_version "1";
    chr_IV  ensembl start_codon     1802    1804    .       +       0       gene_id "YDL248W"; gene_version "1";
    chromosome_IV   ensembl stop_codon      2951    2953    .       +       0       gene_id "YDL248W"; gene_version "1";
    chromosome_IV   ensembl gene    762     3836    .       +       .       gene_id "YDL247W-A"; gene_version "1";
    chr_IV  ensembl transcript      3762    836     .       +       .       gene_id "YDL247W-A"; gene_version "1";   

test@bioinfo_docker:~/homework$ ==wc -l test_command.gtf==  
    **8 test_command.gtf**  
test@bioinfo_docker:~/homework$ ==wc -c test_command.gtf==  
    **636 test_command.gtf**   
## 2.利用 grep 等命令尝试筛选并输出示例文件中以 chr_ 起始，并且基因id为 YDL248W 的行。  
test@bioinfo_docker:~/homework$ **grep -E 'chr_.*YDL248W' test_command.gtf**  
    chr_IV  ensembl gene    1802    2953    .       +       .       gene_id "YDL248W"; gene_version "1";  
    chr_IV  ensembl transcript      802     2953    .       +       .       gene_id "YDL248W"; gene_version "1";  
    chr_IV  ensembl start_codon     1802    1804    .       +       0       gene_id "YDL248W"; gene_version "1";  
## 3.利用 sed 等命令将示例文件中的 chr_ 替换为 chromosome_ 并输出每行的第1，3，4，5列。（无需改动原文件，只输出结果）
test@bioinfo_docker:~/homework$ sed 's/chr_/chromosome_/g' test_command.gtf
    chromosome_IV   ensembl gene    1802    2953    .       +       .       gene_id "YDL248W"; gene_version "1";
    chromosome_IV   ensembl transcript      802     2953    .       +       .       gene_id "YDL248W"; gene_version "1";
    chromosome_IV   ensembl exon    1802    2953    .       +       .       gene_id "YDL248W"; gene_version "1";
    chromosome_IV   ensembl CDS     1802    950     .       +       0       gene_id "YDL248W"; gene_version "1";
    chromosome_IV   ensembl start_codon     1802    1804    .       +       0       gene_id "YDL248W"; gene_version "1";
    chromosome_IV   ensembl stop_codon      2951    2953    .       +       0       gene_id "YDL248W"; gene_version "1";
    chromosome_IV   ensembl gene    762     3836    .       +       .       gene_id "YDL247W-A"; gene_version "1";
    chromosome_IV   ensembl transcript      3762    836     .       +       .       gene_id "YDL247W-A"; gene_version "1";
 
test@bioinfo_docker:~/homework$ awk '{print $1, $3, $4, $5}' test_command.gtf  
    chr_IV gene 1802 2953
    chr_IV transcript 802 2953
    chromosome_IV exon 1802 2953
    chromosome_IV CDS 1802 950
    chr_IV start_codon 1802 1804
    chromosome_IV stop_codon 2951 2953
    chromosome_IV gene 762 3836
    chr_IV transcript 3762 836  

## 4.互换示例文件的第2列和第3列，并且对输出结果利用 sort 命令依照第4和第5列数字大小排序，将最终结果输出到result.gtf文件中
awk '{temp=$2; $2 = $3; $3 = temp; print;}' test_command.gtf | sort -k 4,5 -n > result.gtf  

## 5.更改示例文件的权限，使得文件所有者及所在用户组用户可读、写、执行而其他用户只可读，展示权限修改前后的权限变化。  
 ls -hl test_command.gtf  //查看权限  
  chmod 774 test_command.gtf  //指令
  
-rwxr--r--   ->    -rwxrwxr--//前后变化