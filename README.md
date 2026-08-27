# hank2000928-JJClab_HW4
參考筆記: https://github.com/wsunccake/sle15_notes/blob/master/practice/ch2.md  

-------
#1-2. 依目錄樹作答
答案：  
| 檔案          | Absolute Path                    |
| ------------ | --------------------------------- |
| `report.txt` | `/home/alex/documents/report.txt` |
| `sys.log`    | `/var/log/sys.log`                |

| 檔案           | Relative Path           |
| ------------ | ----------------------- |
| `report.txt` | `documents/report.txt`  |
| `sys.log`    | `../../var/log/sys.log` |

#1-2-3. 用 Absolute Path 切換目錄  
<img width="873" height="462" alt="image" src="https://github.com/user-attachments/assets/c7281f6a-b608-44b7-b51e-85ae5f9a4693" />  

答案分別為:  
cd/var/log  
cd dowloads    

#練習 2. 檔案權限與 chmod  
<img width="595" height="244" alt="image" src="https://github.com/user-attachments/assets/93814029-4b00-4f3b-a7eb-f268ab323a9d" />  

| 對象     | 權限    | 數字 |
| ------ | ----- | -: |
| Owner  | `rwx` |  7 |
| Group  | `r-x` |  5 |
| Others | `r--` |  4 |

#2-1. 解讀權限字串
<img width="883" height="143" alt="image" src="https://github.com/user-attachments/assets/f6f2b1a0-8a33-4012-b0d9-b2a1efdf915a" />

執行結果，輸出為test.txt和testdir的預設權限:  
<img width="475" height="240" alt="image" src="https://github.com/user-attachments/assets/1df75ff4-7c48-4124-a3b8-38970b96d83e" />

<img width="884" height="97" alt="image" src="https://github.com/user-attachments/assets/5c0985f0-ff48-4335-8516-e2a101612de8" />

執行結果，更改權限後再次確認:  
<img width="647" height="480" alt="image" src="https://github.com/user-attachments/assets/2a7aba8f-e073-482f-977c-4b690f833c02" />
