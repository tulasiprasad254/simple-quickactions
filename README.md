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

Here’s the corrected version in good English:

Step 1:

The process in CZ_MDM_OBP_UPD_ACCT_DTL_W will take records of closed or purged accounts, fetch the instruction, and insert them into CZ_MW_AC_AUTO_DEBIT_INSTR_DLT.

Note:
We need to maintain some form of identification for records that have been cancelled or reassigned. Currently, we use the TXN_REF_NO column in CZ_MW_AC_AUTO_DEBIT_INSTR_DLT. If the TXN_REF_NO column is not present, we need to add an additional column in the CZ_MW_AC_AUTO_DEBIT_INSTR_DLT_DRV table and insert the reason for those records.

Step 2:

Those records will follow the autodebit deletion process and, after deletion, will be stored in the outbound logs table CZ_OUTBOUND_NOTICES_D.

Step 3:

The cancellation letter records from the outbound logs table, with eventid: ACH_Cancellation, are loaded into CZ_ACH_CHANGE_NOTICES_D. The cancellation reason is not set, causing the query to fail, and the reason will be inserted as follows:

To resolve this, compare the account number with CZ_MW_AC. If it matches, insert the cancellation reason as R02 in CZ_ACH_CHANGE_NOTICES_D, which indicates the account is closed.