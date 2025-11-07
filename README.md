# ImmunoDB-archive
免疫组库数据库最新版本归档，以及通过R语言部署到本地

# 快速开始

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
  url = "https://xget.xi-xu.me/gh/GongZheng-bio/ImmunoDB-archive/raw/refs/heads/main/McPAS-TCR/McPAS-TCR.csv",
  destfile = "McPAS-TCR.csv"
)

db_output <- read.csv(file = "McPAS-TCR.csv",sep = ",",header = TRUE)
```

- IEDB-AR
```R

```

- TBAdb
```R
download.file(
  url = "https://xget.xi-xu.me/gh/GongZheng-bio/ImmunoDB-archive/raw/refs/heads/main/TBAdb/TBAdb-2020-09-10.xlsx",
  destfile = "TBAdb-2020-09-10.xlsx"
)
# 第一张表：alpha+beta TCR
db_output <- readxl::read_excel("TBAdb-2020-09-10.xlsx", sheet = "TCR-AB")
# 第二张表：delta+gamma TCR
db_output <- readxl::read_excel("TBAdb-2020-09-10.xlsx", sheet = "TCR-GD")
# 第三张表：BCR
db_output <- readxl::read_excel("TBAdb-2020-09-10.xlsx", sheet = "BCR")
```

