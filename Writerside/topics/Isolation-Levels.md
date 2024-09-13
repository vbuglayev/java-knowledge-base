# Isolation Levels

SQL databases use *isolation levels* to manage concurrent transactions, ensuring data consistency and integrity. The isolation levels vary in how they handle problems like dirty reads, non-repeatable reads, and phantom reads.

## 1. Read Uncommitted
- **Description**:
    - Lowest isolation level.
    - Allows dirty reads (reading uncommitted changes made by other transactions).
- **Issues**:
    - Dirty reads
    - Non-repeatable reads
    - Phantom reads

## 2. Read Committed
- **Description**:
    - Prevents dirty reads (only committed changes can be read).
- **Issues**:
    - Non-repeatable reads
    - Phantom reads

## 3. Repeatable Read
- **Description**:
    - Prevents dirty reads and non-repeatable reads (data read during a transaction remains consistent throughout).
- **Issues**:
    - Phantom reads

## 4. Serializable
- **Description**:
    - Highest isolation level.
    - Transactions are completely isolated (as if executed sequentially).
- **Issues**:
    - None (prevents all dirty reads, non-repeatable reads, and phantom reads).

## Trade-offs
- **Performance**: Higher isolation levels introduce more locking, potentially reducing concurrency and performance.
