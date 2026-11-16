Lab Description:

This lab contains a SQL injection vulnerability in the product category filter. The results from the query are returned in the application's response, so you can use a UNION attack to retrieve data from other tables. The first step of such an attack is to determine the number of columns that are being returned by the query. You will then use this technique in subsequent labs to construct the full attack.

To solve the lab, determine the number of columns returned by the query by performing a SQL injection UNION attack that returns an additional row containing null values. 

To solve this lab, i start Burp and enable FoxyProxy to redirect the traffic to burp´s proxy. i choose a request to category and send it to repeater:

-----------------------------------------------------------------------------------------------------------------------------------------------------
<img width="1902" height="731" alt="image" src="https://github.com/user-attachments/assets/d2ae4284-43c0-406d-b09a-b2788b6f2760" />

----------------------------------------------------------------------------------------------------------------------------------------------------
i type the payload: 

--------------------
UNION SELECT NULL--
--------------------
---------------------------------------------------------------------------------------------------------------------------------------------------
<img width="1789" height="957" alt="image" src="https://github.com/user-attachments/assets/ea0d798b-5305-48b8-8030-419bba62b97d" />

---------------------------------------------------------------------------------------------------------------------------------------------------
But as you can see in the image, i need to URL Encode the payload, so i highlight the paylod and use the shortcut Crtl + U to encode correctly:

-----------------------------------------------------------------------------------------------------------------------------------
<img width="1890" height="953" alt="image" src="https://github.com/user-attachments/assets/268c3cf1-2453-4dc9-9882-0f535b4c033e" />

-----------------------------------------------------------------------------------------------------------------------------------
<img width="1776" height="721" alt="image" src="https://github.com/user-attachments/assets/ea3cb976-e101-4df0-addd-8d46a81dfd7b" />

-----------------------------------------------------------------------------------------------------------------------------------
I send the first request:

-----------------------------------------------------------------------------------------------------------------------------------
<img width="1872" height="961" alt="image" src="https://github.com/user-attachments/assets/b0aad2d4-fd10-41cb-a004-a001fc799a27" />

-----------------------------------------------------------------------------------------------------------------------------------
It returns a error, i add a NULL to the end of the payloand e send again:

-----------------------------------------------------------------------------------------------------------------------------------
<img width="1609" height="920" alt="image" src="https://github.com/user-attachments/assets/97634137-d28b-44b9-bd5e-e13cb368c8fe" />

-----------------------------------------------------------------------------------------------------------------------------------
Another error, i add another NULL and send the request again:

-----------------------------------------------------------------------------------------------------------------------------------
<img width="1676" height="899" alt="image" src="https://github.com/user-attachments/assets/aaca157b-fd55-4ca3-94b3-26b65014c207" />

-----------------------------------------------------------------------------------------------------------------------------------
And that´s it, i discovered the number of columns using UNION and NULL values.
