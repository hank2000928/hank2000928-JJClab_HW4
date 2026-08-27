# hank2000928-JJClab_HW4
參考筆記: https://github.com/wsunccake/sle15_notes/blob/master/practice/ch2.md  

-------
# 1-2. 依目錄樹作答
答案：  
| 檔案          | Absolute Path                    |
| ------------ | --------------------------------- |
| `report.txt` | `/home/alex/documents/report.txt` |
| `sys.log`    | `/var/log/sys.log`                |

| 檔案           | Relative Path           |
| ------------ | ----------------------- |
| `report.txt` | `documents/report.txt`  |
| `sys.log`    | `../../var/log/sys.log` |

# 1-2-3. 用 Absolute Path 切換目錄  
<img width="873" height="462" alt="image" src="https://github.com/user-attachments/assets/c7281f6a-b608-44b7-b51e-85ae5f9a4693" />  

答案分別為:  
> cd/var/log  
> cd downloads    

# 練習 2. 檔案權限與 chmod  
<img width="595" height="244" alt="image" src="https://github.com/user-attachments/assets/93814029-4b00-4f3b-a7eb-f268ab323a9d" />  

| 對象     | 權限    | 數字 |
| ------ | ----- | -: |
| Owner  | `rwx` |  7 |
| Group  | `r-x` |  5 |
| Others | `r--` |  4 |

# 2-1. 解讀權限字串
<img width="883" height="143" alt="image" src="https://github.com/user-attachments/assets/f6f2b1a0-8a33-4012-b0d9-b2a1efdf915a" />

執行結果，輸出為test.txt和testdir的預設權限:  
<img width="475" height="240" alt="image" src="https://github.com/user-attachments/assets/1df75ff4-7c48-4124-a3b8-38970b96d83e" />

<img width="884" height="97" alt="image" src="https://github.com/user-attachments/assets/5c0985f0-ff48-4335-8516-e2a101612de8" />

執行結果，更改權限後再次確認:  
<img width="647" height="480" alt="image" src="https://github.com/user-attachments/assets/2a7aba8f-e073-482f-977c-4b690f833c02" />

# 2-3. 檔案與目錄上的 r、x

| 對象        | 權限  | 意義                |
| --------- | --- | ----------------- |
| File      | `r` | 可以讀取檔案內容          |
| File      | `x` | 可以執行該檔案           |
| Directory | `r` | 可以讀取目錄中的檔名清單      |
| Directory | `x` | 可以進入／穿越該目錄，存取其中項目 |

補充思考題：    

> 目錄只有 r、沒有 x 時，ls 與 cd 可能出現什麼現象？  
> 答: x = 能否 traverse / 進入這個目錄。  

<img width="888" height="235" alt="image" src="https://github.com/user-attachments/assets/b666e719-678b-41a7-a866-2800af7dd040" />

> 答: umask可以理解成：建立新檔案／目錄時，要從預設權限中拿掉哪些權限。
>> 若有
>>> 一般檔案：666  
>>> 目錄：    777  
>>> 執行 umask 027，則:  
    
| 類型        |  基礎 | umask |    最後 |  
| --------- | --: | ----: | ----: |    
| File      | 666 |   027 | `640` |  
| Directory | 777 |   027 | `750` |  
    
> file的部分，6-7<0，故為0。以下為實機操作。
<img width="668" height="482" alt="image" src="https://github.com/user-attachments/assets/b145f960-1e0d-4ae9-b191-fe5d1f59ae71" />  

# 2-5. 特殊權限：SUID、SGID、Sticky Bit
<img width="675" height="238" alt="image" src="https://github.com/user-attachments/assets/7fbbbf78-fa76-425b-9eaf-b2ffd93ba05e" />

> 答: 
>> SUID — Set User ID: 主要用在執行檔。一般程式執行時使用「執行者」的權限。有 SUID 時則執行程式時暫時使用「檔案 Owner」的權限。
>>>
>> SGID — Set Group ID: SGID 對「執行檔」和「目錄」意義不同。對執行檔執行時採用該檔案所屬 Group 的權限。對目錄更常用的是，在此目錄                         下新增的檔案，會繼承目錄的 Group。所以共同工作資料夾常使用 SGID。
                        設定<chmod g+s directory>，數字<chmod 2755 directory>前面的「2」就是 SGID。
>>>
>> Sticky Bit: 舉例來說執行<ls -ld /tmp>可輸出<drwxrwxrwt>，最後的「t」就是 Sticky Bit。它的用途在於，即使很多使用者都能在這個目
                錄新增檔案，也不能任意刪除其他使用者的檔案。
