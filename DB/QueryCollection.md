### Query 모음
#### 전체 table 별 row count 구하기
```query
SELECT table_name, table_rows FROM information_schema.tables WHERE table_schema = 'DBNAME' ORDER BY table_name;
```
