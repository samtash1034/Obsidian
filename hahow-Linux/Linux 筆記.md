su -：切換到root

 留言

exit：跳回上一個使用者

pwd：現在的位置

whoami：現在使用者名稱

~：家目錄

-：選項

.資料夾：隱藏檔

-l：long

-a：所有檔案包含隱藏檔

alas：可查看別名

ls -al /：後面可加 / 指定位置

sudo：超級使用者的指令（當你是root以外的使用者要用超級使用者的指令，要加上sudo，root本身則不用））

cp /etc/fstab .(可按tab兩次查看etc資料夾底下的所有檔案，檔案太多可按空白鍵跳下一頁，q為離開，.代表複製到當前位置)

rm /tmp/xx檔案：移除tmp資料夾底下的xx檔案  
rm aa bb：改變當前位置aa的名稱為bb

mv aa bb/：移動aa檔案到bb資料夾底下(bb/代表bb底下，不寫/也可以)

rm -rf xxx：recursive force(強制刪除xx資料夾及底下的東西)

xfs

每一個檔案都有些資訊（檔名、更動時間、權限、儲存區塊位置等），這些資訊都記錄在indoe（唯一的編號上

df：查看空間還剩多少、用了幾％

df（disk free) -h(human readable讓人容易閱讀)：查看還剩多少空間可以使用（顯示大小）

查詢此指令的相關操作  
man(manual) df  
info df

du(directory use) -h /xxx：這個資料夾目前使用多少G

du -d(deep) 1(1層) -h /：顯示根目錄這一層的所有資料夾目前使用多少（限制層數，不然會全部都列出來，包含子資料夾）

symbol link：ln(link) -s /aa資料夾 ccc(鏈接名稱)

ls -i：查看inode

ln aa資料夾（在同一層就不用/) bbb(硬連結名稱)

hard link的inode跟被指到的檔案相同

原檔案被刪除後，hard link 還是可以繼續看  
hard link無法指定到不同的分割區，也不能用在目錄資料夾上面

echo(迴聲) “xxx字串” aa檔案：把字串放到這aa檔案裡面（這檔案就會被產生）  
但這檔案不能被執行（rw-)，因此要改變權限可執行->chmod u+x aa檔名(change mode)，就會變到rwx就可以執行了（檔案也會變綠色）

echo “xx字串”：代表執行這個字串，就顯示此字串

執行檔案(./代表當前) ./aa檔案（他就會去執行echo “xxx”），因此會印出xx

wget url：下載網路上的檔案

vim：編輯  
dd：刪除整行  
gg：跳到第一行  
G：跳到最後一行  
q!：強制離開  
u：上一步  
yy:複製  
p:貼上

xx行＋ＧＧ：快速跳到第幾行

> 代表重導（redirect)

標準輸出：螢幕  
ls > myfile：把ls 輸出導入到myfile(原本顯示在螢幕上)  
myfile必須不存在不然會覆蓋過去  
cat myfile

想要加到後面則用 df >> myfile

0代表標準輸入  
1代表標準輸出  
2代表標準錯誤訊息輸出

例如：ls /abcde 2> myfile

把錯誤跟標準輸出導入到某一個檔案：ls /abcde > myfile 2>&1

wc(word count)  
hello , sam  
ctrl + d  
1 3 12(行數、字母數、字數)

< 重導輸入  
sudo wc < xxx檔案位置

｜ 管線 pipe line  
ls /usr/bin會輸出很多資料  
可透過ls /usr/bin | more讓他用分頁的方式呈現  
把｜左邊指令的輸出，送給右邊的指令輸入（more把資料分頁）

grep xxx(想要搜尋的字) xxxx(檔案)

因為ls出來的資料太多，所以透過這種方式來做搜尋  
ls /usr/bin | grep xxx(想要搜尋的字)

rpm -qa：列出已安裝的軟體套件  
rpm -qa | grep httpd

ubunut:sudo dpkg -l | grep http

which 和 locate 都限制於path這路徑

which xx指令  
查看指令位的路徑

locate 查找檔案或指令（可能要先updatedb)

不限於path路徑：find

find 從哪裡開始搜尋 -name xxx(檔名) 或 x.*

find /var/ -perm 755 (找755權限的資料夾)

find /root -ctime -2：找兩天內有變動過的資料夾

find /usr/ -size +5M：查找檔案大小 > 5 mega

#### [](https://hackmd.io/mpY7-qAfQ-y_4mtxoLQntQ#%E6%AA%A2%E8%A6%96%E6%AA%94%E6%A1%88%E5%85%A7%E5%AE%B9 "檢視檔案內容")檢視檔案內容

cat > text.txt(建立test資料夾並可以直接在裡面輸入內容)(ctrl + d 儲存)  
cat -n > data.txt(跟上面功能相同只是之後cat data.txt的時候會出現行號)

more：利用分頁的方式顯示  
less：除了分頁還可以在冒號後面打跳到指定的行數  
q：結束  
head：查看檔案前10行  
tail：查看檔案最後10行(很常用)

tail -f(follow) data.txt：追蹤這檔案的變動(可以開另一個session然後cat >> data.txt在最後一行加資料，此時原本的session就會看到資料被加進來了)  
ctrl + c：停止監控

ls -l /usr/bin | grep more：more比較常配合管線(|)的使用