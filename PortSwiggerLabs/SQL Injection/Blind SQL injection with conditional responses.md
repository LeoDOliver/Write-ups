Lab Description:

This lab contains a blind SQL injection vulnerability. The application uses a tracking cookie for analytics, and performs a SQL query containing the value of the submitted cookie.
The results of the SQL query are not returned, and no error messages are displayed. But the application includes a Welcome back message in the page if the query returns any rows.
The database contains a different table called users, with columns called username and password. You need to exploit the blind SQL injection vulnerability to find out the password of 
the administrator user.

To solve the lab, log in as the administrator user. 

The lab description already tells me that there are a table called users, with username and password and the user i need to discover the password is the administrator, when i browse the application, i see the message Welcome Back!:


<img width="1909" height="902" alt="image" src="https://github.com/user-attachments/assets/6bf1f5d5-a041-48fa-9a32-c7a9732a7cf1" />

On Burp, i can see the cookie header TrackingId:

<img width="1870" height="757" alt="image" src="https://github.com/user-attachments/assets/228a7a88-2f40-4d02-9777-fd2eefca446b" />


