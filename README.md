# ImmunoDB-archive
免疫组库数据库最新版本归档，以及通过R语言部署到本地

# 快速开始

直接运行以下代码，即可下载并读取各数据库到R环境中

- VDJdb
```R
download.file(
  url = "https://xget.xi-xu.me/gh/GongZheng-bio/ImmunoDB-archive/raw/refs/heads/main/VDJdb/vdjdb-2025-09-25.zip",
  destfile = "vdjdb-2025-09-25.zip"
)
# 解压文件
temp_dir <- tempdir()
utils::unzip(vdjdb_data_zip, exdir = temp_dir)
db_file_path <- file.path(temp_dir, "/database/vdjdb_full.txt")
unlink(temp_dir, recursive = TRUE) # 清理临时目录,recursive=TRUE表示删除目录及其内容

db_output <- read.csv(db_file_path,sep = "\t",header = TRUE)
db_output[db_output == ""] <- NA
```
- McPAS-TCR
```R
download.file(
  url = "https://xget.xi-xu.me/gh/GongZheng-bio/ImmunoDB-archive/raw/refs/heads/main/McPAS-TCR/McPAS-TCR-2020-09-10.csv",
  destfile = "McPAS-TCR.csv"
)

db_output <- read.csv(file = "McPAS-TCR.csv",sep = ",",header = TRUE)
db_output[db_output == ""] <- NA
```

- IEDB-AR
```R

```

- TBAdb
```R
download.file(
  url = "https://xget.xi-xu.me/gh/GongZheng-bio/ImmunoDB-archive/raw/refs/heads/main/TBAdb/TBAdb.xlsx",
  destfile = "TBAdb.xlsx"
)
# 第一张表：alpha+beta TCR
db_output <- readxl::read_excel("TBAdb.xlsx", sheet = "TCR-AB")
# 第二张表：delta+gamma TCR
db_output <- readxl::read_excel("TBAdb.xlsx", sheet = "TCR-GD")
# 第三张表：BCR
db_output <- readxl::read_excel("TBAdb.xlsx", sheet = "BCR")

db_output[db_output == "-"] <- NA
```

# 数据库简介
[VDJdb](https://vdjdb.cdr3.net/)：一个包含T细胞受体（TCR）序列及其已知抗原特异性的数据库，广泛用于免疫学研究和临床应用。
[McPAS-TCR](https://friedmanlab.weizmann.ac.il/McPAS-TCR/)：一个专注于T细胞受体（TCR）特异性的数据库，提供了大量的TCR-抗原配对信息。
[IEDB-AR](https://www.iedb.org/)：免疫表位数据库，包含了大量的抗原-抗体和抗原-T细胞受体相互作用数据。
[TBAdb](http://www.tbadb.org/)：一个专注于肿瘤浸润淋巴细胞（TIL）T细胞受体（TCR）序列的数据库，提供了丰富的TCR-抗原配对信息。

