---
output: html_document
---

# 生物数据 {#biodata}


>我们不产生数据，我们只是数据的搬运工

## 常用生物数据库

## 常见生物数据格式

- fasta
- fastq(encoding format check)
- gff/gtf/bed/... 
- vcf
- sam/bam

![NGS format](https://bioinf.comav.upv.es/courses/sequence_analysis/_images/ngs_map_read_file_formats.png)
![NGS format](https://bioinf.comav.upv.es/courses/sequence_analysis/_images/ngs_file_formats.png)

[UCSC注释文件](http://genome.ucsc.edu/FAQ/FAQformat.html)

[EDAM ontology](https://www.ebi.ac.uk/ols/ontologies/edam/terms?iri=http%3A%2F%2Fedamontology.org%2Fdata_3670)

### 生物数据下载

#### 测序数据下载
测序数据一般存储在NCBI的GEO/SRA数据库，或者EBI的ENA数据库。我们希望下载完整的数据，并在最短的时间内完成，对此有以下几种方法。

* 使用ENA获得数据的fastq.gz地址，fastq.gz文件可直接用于下游分析，而且ENA提供文件的md5 hash值，下载完成后可用`md5sum`检查文件完整性。可使用[Aspera](https://downloads.asperasoft.com)下载，Aspera是IBM开发的数据传输工具。其可在Windows/Linux/MAC多平台下运行。
ascp参数如下：
```bash
ascp -T -l 300m -P33001 -k1 -i asperaweb_id_dsa.openssh era-fasp@fasp.sra.ebi.ac.uk:/vol1/fastq/SRR874/009/SRR8740819/SRR8740819_2.fastq.gz .
# ascp [OPTION] SRC... DEST
# -T                               Disable encryption
# -l  MAX-RATE                     Max transfer rate
# -P  SSH-PORT                     TCP port used for SSH authentication
# -k  RESUME-LEVEL                 Resume criterion: 0,3,2,1
# -i  PRIVATE-KEY-FILE             Private-key file name (id_rsa)
```

* 下载sra数据，利用NCBI sratoolkit中`prefetch`命令

```bash
prefetch ACCESSION_ID
```
* 在获取sra或者fastq文件ftp链接后，使用`wget`,`curl`,`aria2c`，或者迅雷下载等
```bash
wget -c FTP_LINK
curl -O FTP_LINK
aria2c -j16 -x16 -c true FTP_LINK
```

#### 注释数据下载

#### 爬虫

### 数据格式转换
[UCSC ulity](http://hgdownload.soe.ucsc.edu/admin/exe/linux.x86_64/)
