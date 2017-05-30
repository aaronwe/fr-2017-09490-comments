# About
Scrapes the comments pertaining to national monuments, e.g. the comment at
https://www.regulations.gov/document?D=DOI-2017-0002-34328

# Setup
```sh
conda env create -f environment.yml
```

Use psql and run:
```sql
CREATE DATABASE benm
    WITH 
    ENCODING = 'UTF8'
    CONNECTION LIMIT = -1;
CREATE USER benmuser WITH PASSWORD 'Ki3nslkj4nb';
GRANT ALL ON DATABASE benm TO benmuser;
\connect benm
ALTER SCHEMA public OWNER TO benmuser;
ALTER DATABASE benm OWNER TO benmuser;
ALTER DEFAULT PRIVILEGES 
    FOR USER benmuser
    IN SCHEMA public
    GRANT SELECT, INSERT, UPDATE, DELETE ON TABLES TO benmuser;
```

# Environment
```sh
source activate benm
jupyter notebook
```