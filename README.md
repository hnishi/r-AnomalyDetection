r-AnomalyDetection
==================

## Original Document

https://yokkuns.hatenadiary.org/entry/20120930/1348978641

## Setup

環境：ubuntu18 on AWS EC2

R の環境構築はお好きなように。
私は、Rstudio-serverを立てた。
構築手順をAppendix（下記）に記載。

### ubuntu側

```
sudo apt install libxml2-dev
sudo apt install libcurl4-openssl-dev
```

### パッケージのインストール

```R
install.packages("reshape2")
install.packages("ggplot2")
install.packages("RFinanceYJ")
install.packages("quantmod")
```

## 使用例

以下を参照
r-AnomalyDetection/ChangeAnomalyDetection/R/analysis01.Rmd 

## Appendix

### Rstudio server on EC2 (ubuntu 18) のセットアップ

```bash
sudo apt install r-base
sudo apt install gdebi-core
wget https://download2.rstudio.org/server/bionic/amd64/rstudio-server-1.2.5001-amd64.deb
sudo gdebi rstudio-server-1.2.5001-amd64.deb
sudo rstudio-server start
```

[Download RStudio Server - RStudio](https://www.rstudio.com/products/rstudio/download-server/)

#### Account of Rstudio-server

> ユーザ名とパスワードは、ubuntuのユーザ名とパスワードを入力します。

https://www.virment.com/setup_rstudio_server_ubuntu/

I changed a password

```bash
sudo passwd ubuntu
```

user: ubuntu
pass: ubuntu

#### 別のユーザーを作成する場合
　
ubuntu ユーザを新規に作成する
 
```bash
sudo adduser rstudio
```

今回は、
user: rstudio
password: rstudio

その他はデフォルトで作った。

#### Execute R script in R-studio

- １行ずつ実行

`Ctrl-Enter`

### Enter Rstudio-server

EC2 セキュリティグループ
インバウンドルール
カスタムTCPでポート8787を許可する

ブラウザで以下にアクセス

`http://<YOUR PUBLIC IP>:8787/`

ubuntu のユーザでログイン
