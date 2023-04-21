# PostgreSQL_practice

## psql을 통한 DB 접속

- `psql`
    - postgreql 터미널 시작
    
    ```jsx
    ...
    # localhost의 5432 port로 Postgresql 접속을 시도. Target DB는 현재 사용자 이름과 동일한 'draidev'
    [draidev@localhost ~]$ psql
    
    # localhost의 5432 port로 Postgresql 접속을 시도. 접속 User는 'postgres'이며 Target DB는 접속 User와 동일한 'postgres'
    [draidev@localhost ~]$ psql -U postgres
    
    # 192.168.0.165의 5432 port로 Postgresql 접속을 시도. 접속 User는 'draidev'이며 Target DB는 현재 사용자 이름과 동일한 'browndwarf'
    [draidev@localhost ~]$ psql -h 192.168.0.165
    
    # 192.168.0.165의 5432 port로 Postgresql 접속을 시도. 접속 User는 'posgres'이며 Target DB는 접속 User와 동일한 'draidev'
    [draidev@localhost ~]$ psql -h 192.168.0.165 -U posgres
    
    # 192.168.0.165의 5432 port로 Postgresql 접속을 시도. 접속 User는 'draidev'이며 Target DB는 'price'
    [draidev@localhost ~]$ psql -h 192.168.0.165 -U draidev price
    [draidev@localhost ~]$ psql -h 192.168.0.165 -U draidev -d price
    
    # 192.168.0.165의 9000 port로 Postgresql 접속을 시도. 접속 User는 'draidev'이며 Target DB는 'price'
    [draidev@localhost ~]$ psql -h 192.168.0.165 -p 9000 -U draidev price
    [draidev@localhost ~]$ psql -h 192.168.0.165 -p 9000 -U draidev -d price
    
    # -W 옵션 : 비밀번호를 입력하도록 요구합니다.
    [draidev@localhost ~]$ psql -U lockard_ai -d lockard_ai -W
    password: 
    ```
    
    - `-f`
        - 지정된 파일에서 SQL 쿼리를 읽어서 실행하는데 사용됩니다. 즉, **`-f`** 옵션은 특정 파일에 저장된 SQL 쿼리를 실행하는 데 사용됩니다. 다음은 **`-f`** 옵션을 사용하여 SQL 쿼리를 파일에서 읽어오는 예제입니다.
            
            ```sql
            psql -U username -d dbname -f path/to/sqlfile.sql
            ```
            
        - 이 외에도 **`-f`** 옵션은 **`-q`** 옵션과 함께 사용하여 쿼리 실행 결과를 출력하지 않을 수도 있습니다. 예를 들어, 다음과 같이 **`-q`** 옵션과 함께 **`-f`** 옵션을 사용할 수 있습니다.
            
            ```
            psql -U username -d dbname -q -f path/to/sqlfile.sql
            ```
            
        - 위의 명령어는 **`-q`** 옵션으로 실행 결과를 출력하지 않도록 지정하고, **`-f`** 옵션으로 SQL 쿼리가 저장된 파일을 지정합니다. 이 명령어는 저장된 파일(**`path/to/sqlfile.sql`**)에서 SQL 쿼리를 읽어와 **`psql`** 클라이언트로 실행하며, 실행 결과는 출력하지 않습니다.
