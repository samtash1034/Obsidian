
#### Linux的使用者帳號與群組

cat /etc/group：查看所有群組

groupadd 群組名稱：建立群組

cat /etc/passwd：帳號資料檔
【 mike:x:1001:1002::/home/mike:/bin/sh 】
名稱、密碼、使用者id、群組id、目錄

useradd 使用者名稱：建立使用者(幫我們創立一個跟使用者名稱一樣的group，並且在shadow檔幫我們建立使用者資料)

* 使用useradd可能 home 目錄不會被創建，因此這裡使用assuser

cat /etc/shadow(陰影)：查看密碼

#### 新增群組與帳號、刪除帳號

id sam：列出這帳號的資訊

useradd -g rd(群組名稱) tom(帳號名稱)：建立帳號時指定群組，這樣就不會建立名稱是自己的群組

usermod(修改) -G sales(一個帳號可以在不同群組內) tom：幫已存在使用者加到另一個群組(附屬群組)
附屬群組會覆蓋舊的附屬群組

想要添加一個以上的附屬群組：usermod -G sales,manager tom

刪除帳號：userdel -r(有加r的話連home目錄都會刪掉) tom
Ubuntu：userdel - tom(不刪除home)

#### 刪除群組，讓使用者無法登入

刪除群組：groupdel xxx群組名稱(群組必須沒有人才可以刪)

設定使用者的密碼：passwd tom

chsh tom->/sbin/nologin：不讓tom login

#### 檔案權限管理與變更

r：4(2^2)
w：2(2^1)
x：1(2^0)


chmod 755 data.txt(變更權限)

u：user
g：group
o：other

chmod o-rx data.txt(-rx代表把rx變成-)
chmod o=r data.txt(=r代表變成r)
chmod og=r data.txt(一次變更other和group)
chmod g+x data.txt(用加的方式，其他不會變)
chmod a=r data.txt(a=all)

#### 目錄資料夾的權限

跟檔案有些不同：
r：列出目錄內容
w：可在目錄中編輯、刪除檔案
x：可進入該目錄


