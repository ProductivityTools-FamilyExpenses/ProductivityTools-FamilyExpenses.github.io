


Full solution contains modules
 -
- PT.FamilyExpenses.mBank - should be run on the account where emails from mBank about the transactions are received

[PT.FamilyExpenses](https://docs.google.com/spreadsheets/d/1XJAduyj-wL-kVE12Ib93htKbiEyTXuzYOG7j4BedrOA/edit?gid=0#gid=0)


Workflow
- [PT.FamilyExpenses.Allegro](https://docs.google.com/spreadsheets/d/1sBC7PWM7DkCA4smf11Gg59tWT5R7JRIRaWqqpkIYgw8/edit?gid=609545681#gid=609545681) - should be run on the account where emails from Allegro are received.
  - The data in the Allegro sheet needs to be uploaded before mBank is executed. Trigger is set for every 4 hour.
  - Steps:
    - importAllegroEmailsToTrix
    - archiveElementsRowsOlderThan4Monhts
- [PT.FamilyExpenses.mBank](https://docs.google.com/spreadsheets/d/1XJAduyj-wL-kVE12Ib93htKbiEyTXuzYOG7j4BedrOA/edit?gid=0#gid=0) - should be run on the account where emails from mBank about the transactions are received
  - It should be run after hours, when the above script finishes. So during the night is good idea. Curretly run manually
  - Steps
    - importTransactionsFromGmail
    - setCatgoriesForTransactions
    - setAccountForTransactionsSheets
    - fillAllegroPurchase
- [PT.FamilyExpenses.AllTransactions](https://docs.google.com/spreadsheets/d/1Exdtvg5WLRB2kcT7X_isY_a_0hy7lZidmzW-HBRkgV0/edit?gid=659013003#gid=659013003) - The data analysis sheet. Data is copied to hide all the complxity of the process
  - Steps
    - //clearAllTransactions (optional)
    - copyDataToFinalSheet