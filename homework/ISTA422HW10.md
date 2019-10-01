// Name: TSQL HW09
// Author: James Smelser
// Date: September 14, 2019

-------------------------------------------------------------
# Homework, Chapter 10
## ISTA-420, T-SQL Fundamentals
1. What is the purpose of transactions? Why do we use transactions in SQL scripts?
- A transaction is a unit of work that might include multiple activities that query and modify data and
that can also change the data definition.
2. Briefly describe each of the ACID properties.
- Atomicity A transaction is an atomic unit of work, Consistency The term consistency refers to the state of the data that the relational database management system (RDBMS) gives you access to as concurrent transactions modify and query it,
Isolation ensures that transactions access only consistent data, Durability Data changes are always written to the database’s transaction log on disk before they are written to the data portion of the database on disk.
3. What do we mean when we talk about the granularity of locks?
- Lock granularity specifies which resource is locked by a single lock attempt.
4. What do we mean when we talk about the modes of locks?
- two main lock modes: exclusive and shared.
5. In your own words, describe blocking, and give an example.
- When a data resource is being used and another user tries to access that data at the same time.
6. What are the properties of locks? That is, list the column name and column type of thefields in
sys.dm tran locks.
- request_session_id AS sid, resource_type AS restype, resource_database_id AS dbid, DB_NAME(resource_database_id) AS dbname,
resource_description AS res, resource_associated_entity_id AS resid, request_mode AS mode, request_status AS status.
7. What are the properties of sessions? That is, list the column name and column type of the fields in
sys.dm exec connections.
- session_id AS sid, connect_time, last_read, last_write, most_recent_sql_handle.
8. What are the requests of sessions? That is, list the column name and column type of thefields in
sys.dm exec requests.
- session_id AS sid, login_time, host_name, program_name, login_name, nt_user_name, last_request_start_time, last_request_end_time.
9. What is an isolation level? Give an example of the operation of an isolation level.
- Isolation levels determine the level of consistency you get when you interact with data.
10. (Not in the book.) What do we mean when we say that an object is serializable?
- Serialization is the process of converting an object into a stream of bytes in order to store the object or transmit it to memory, a database, or a file.
11. What is a deadlock? Give an example of a deadlock?
- A deadlock is a situation in which two or more sessions block each other.
