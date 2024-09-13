# ACID

ACID is a set of properties that ensure reliable processing of database transactions. It stands for:

1. **Atomicity**:  
   Ensures that a transaction is all or nothing. If any part of the transaction fails, the entire transaction is rolled back, leaving the database unchanged.

2. **Consistency**:  
   Guarantees that a transaction brings the database from one valid state to another, maintaining data integrity.

3. **[Isolation](Isolation-Levels.md)**:  
   Ensures that the execution of transactions concurrently doesn't affect their outcome. Each transaction behaves as if it's the only one being processed.

4. **Durability**:  
   Ensures that once a transaction is committed, it will remain so, even in the event of a system failure.
