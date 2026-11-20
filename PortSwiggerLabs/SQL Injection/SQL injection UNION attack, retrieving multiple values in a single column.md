Lab Description:

 This lab contains a SQL injection vulnerability in the product category filter. The results from the query are returned in the application's response so you can use a UNION attack to retrieve data from other tables.
The database contains a different table called users, with columns called username and password.
To solve the lab, perform a SQL injection UNION attack that retrieves all usernames and passwords, and use the information to log in as the administrator user. 

Due to the lab description, i already know that the database has a table called users with the columns username and password, but it dont describe what DBMS software is in use, so i will need to test some payloads.

But first, lets test the injetion point:

-----------------------------------------------------------------------------------------------------------------------------------
<img width="1551" height="806" alt="image" src="https://github.com/user-attachments/assets/f336f435-5b20-4c19-bec1-cca1a4b58f3b" />

-----------------------------------------------------------------------------------------------------------------------------------
<img width="1549" height="857" alt="image" src="https://github.com/user-attachments/assets/dfd8240a-19e1-4156-9df4-f24a11c73f8e" />

I test with one column, i get an error, i test with two columns, i get a OK response, now i need to test which column accepts string data:

-----------------------------------------------------------------------------------------------------------------------------------
<img width="1548" height="760" alt="image" src="https://github.com/user-attachments/assets/45e96ee3-631f-437c-aa73-3ad603bec997" />

-----------------------------------------------------------------------------------------------------------------------------------
<img width="1554" height="846" alt="image" src="https://github.com/user-attachments/assets/c5460485-2ce9-4816-9e72-93b5c786b93a" />

The second column is what i will use, i will test some payloads to see what get me a sucessful response and in my first try i get it right:

-----------------------------------------------------------------------------------------------------------------------------------
<img width="1555" height="852" alt="image" src="https://github.com/user-attachments/assets/ad6bce39-7695-44b5-a36e-9d93e8b994c5" />

-----------------------------------------------------------------------------------------------------------------------------------
<img width="1914" height="801" alt="image" src="https://github.com/user-attachments/assets/0c256a01-0290-40e1-bb6b-2fd317f80586" />

