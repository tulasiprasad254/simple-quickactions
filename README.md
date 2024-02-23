Hello, Sabari.
The following are my observations regarding Narration adjustments.
I followed the steps below to log sql queries in the Hibernate log file.
Step 1: Inject the extension file into batch domain IT4.
Step 2: Clean and build using Batch Server 2.
Step 3: Start the batch server.
Step 4: Complete the transactions for logging the class files.
Step 4: In the EM console, set the extension file log to trance 32 and the hibernate handler to trace 32.
Step 5: Completed the transaction in the UI, then extracted the log from ofss.log for the class.
All of the logs were found to be at a fine level.
Step 6: Navigated to the Hibernate log route; no log was discovered for Queries.
