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
test@bioinfo_docker:~/homework$ **grep -E 'chr_.*YDL248W' test_command.gtf**  
    chr_IV  ensembl gene    1802    2953    .       +       .       gene_id "YDL248W"; gene_version "1";  
    chr_IV  ensembl transcript      802     2953    .       +       .       gene_id "YDL248W"; gene_version "1";  
    chr_IV  ensembl start_codon     1802    1804    .       +       0       gene_id "YDL248W"; gene_version "1";  

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
    