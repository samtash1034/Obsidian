####  軟體套件 RPM 查詢 query 

rpm(Red Hat Package Manager)：將預先編譯好的一個套件軟體包裝起來，直接在系統裡面安裝，省去編譯的工作

rpm -qa(query all)：查詢全部套件

rpm -qa | grep gzip

rpm -qi(information) gzip：詳細資訊

rpm -ql(list) gzip：列出軟體套件所安裝的檔案清單

rpm -qf /etc/fstab：查看是哪一個軟體所安裝的(setup-2.12.2-7.el8.noarch)

<br/>

#### 安裝 RPM 軟體套件 install

光碟讀取進來

blkid 

rmp -ivh(install) xxxx

rpm -e mc：移除軟體

dnf：新版軟體套件管理指令

<br/>


#### YUM 與 DNF 套件管理

YUM：yellow dog update modified

yum：會把所有相依的套件一起打包下載回來並安裝( rpm 則要依序安裝依賴的相關套件)

DNF：dandified(美化) yum：有人說它是 yum4.0


<br/>


#### 軟體檔案庫 repo 管理，EPEL 擴充軟體庫，remi 安裝 PHP 7.4

dnf repolist：列出軟體庫

dnf search php：軟體庫去搜尋有沒有 phpy

EPEL：extra package enterprise linux：額外的檔案庫 (repository)

htop：從epel去安裝

php在remi裡面