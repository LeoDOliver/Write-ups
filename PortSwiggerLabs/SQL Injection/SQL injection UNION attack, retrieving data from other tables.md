Lab Description:

This lab contains a SQL injection vulnerability in the product category filter. The results from the query are returned in the application's response, so you can use a UNION attack to retrieve data from other tables. To construct such an attack, you need to combine some of the techniques you learned in previous labs.
The database contains a different table called users, with columns called username and password.
To solve the lab, perform a SQL injection UNION attack that retrieves all usernames and passwords, and use the information to log in as the administrator user. 

The description already give me the names of tables and columns, so i dont need to worry in discover the correct names. Using burp i intercept a request to category Gifts and send it to repeater:

-----------------------------------------------------------------------------------------------------------------------------------
<img width="1560" height="948" alt="image" src="https://github.com/user-attachments/assets/1a1c99b2-d95a-4ef3-aba7-0ae22de2e156" />

------------------------------------------------------------------------------------------------------------------------------------
I start enumerating the number of columns, discovering the query uses two coluns

------------------------------------------------------------------------------------------------------------------------------------
<img width="1554" height="898" alt="image" src="https://github.com/user-attachments/assets/4d2606f4-caa4-4c8c-aef3-6565e092a190" />
<img width="1551" height="881" alt="image" src="https://github.com/user-attachments/assets/f9adbead-fda5-422e-ba81-b5df5a152061" />

------------------------------------------------------------------------------------------------------------------------------------
Next, i test each column to see the data type, both accept strings, so i dont need to use any function of concatenation

------------------------------------------------------------------------------------------------------------------------------------
<img width="1546" height="857" alt="image" src="https://github.com/user-attachments/assets/a9aaa5b3-f131-4b47-8432-b7a7bed4ec5d" />
<img width="1541" height="860" alt="image" src="https://github.com/user-attachments/assets/b7193610-7ff1-47c4-a610-5a4f53baf5ad" />

------------------------------------------------------------------------------------------------------------------------------------
Using the payload UNION SELECT username,password FROM users--, i retrieve the information:

------------------------------------------------------------------------------------------------------------------------------------
<img width="1545" height="819" alt="image" src="https://github.com/user-attachments/assets/09615f60-a200-4539-9300-413413ce25da" />
<img width="1585" height="861" alt="image" src="https://github.com/user-attachments/assets/6cf164ea-b653-49de-ac64-72cd11714612" />

------------------------------------------------------------------------------------------------------------------------------------
Then to finish the lab, i log in as administrator with the retrieved password:

------------------------------------------------------------------------------------------------------------------------------------
<img width="1831" height="796" alt="image" src="https://github.com/user-attachments/assets/e0b911aa-8182-4a48-8faa-0b416a75d8e8" />
