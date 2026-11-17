Lab Description:

This lab contains a SQL injection vulnerability in the product category filter. The results from the query are returned in the application's response, so you can use a UNION attack to retrieve data from other tables. To construct such an attack, you first need to determine the number of columns returned by the query. You can do this using a technique you learned in a previous lab. The next step is to identify a column that is compatible with string data.

The lab will provide a random value that you need to make appear within the query results. To solve the lab, perform a SQL injection UNION attack that returns an additional row containing the value provided. This technique helps you determine which columns are compatible with string data. 

On the top of the webpage, the lab says the string i must find using a UNION attack:

<img width="1432" height="280" alt="image" src="https://github.com/user-attachments/assets/88c56f92-91fb-4535-aacc-23921db0f657" />

I intercept a request to a category filter and send it to repeater:

<img width="1914" height="1001" alt="image" src="https://github.com/user-attachments/assets/9ddeb2eb-ee6d-4a56-af61-59dd2fc6f8aa" />

After send three requests with NULL values, i discover the number of columns:
<img width="1552" height="877" alt="image" src="https://github.com/user-attachments/assets/2dda5721-4a24-4df5-9b8f-f04f570ccec7" />

I test every column and discover the second accepts strings, then its this column i will use:

<img width="1553" height="896" alt="image" src="https://github.com/user-attachments/assets/b766d80e-e4ab-4b78-8d4a-70a7155fbb21" />

<img width="1554" height="835" alt="image" src="https://github.com/user-attachments/assets/eaa31745-3353-4aba-a89d-6724cd9c5cf0" />

<img width="1754" height="503" alt="image" src="https://github.com/user-attachments/assets/239c8189-2e4f-4ced-9b5e-bd7c9c38247c" />

