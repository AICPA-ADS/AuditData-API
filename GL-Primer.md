# General Ledger Primer
The general ledger API is based on the AICPA Audit Standard with additional content added to support an API interface.

## Intent of the Standard

The intent of the standard is to facilitate the transfer of financial data between users across different systems. The primary purpose is to enable the extraction of detailed financial data for the performance of financial audits.  This is not the sole intent of the standard, and it the specification is wiritten in a manner to supoort the general transfer of financial data between systems for any range of purposes.

## API Rest Points

The General leddger supports the following API end points:

* Journal entries
* Trial balance
* Periods
* Entities
* Accounts
* XBRL Trial Balance

### Journal entries

The journal entries end point allows a user to request journal entries for a specific entity for a specific time range. If no request parameter is defined then the system will attempt to return all available journal entries that the specific user making the request is permitted to see. 

To return data for a specific time range the user provides the start date and the end date.  This date refers to the effective date of the journal entry.

If the system contains jopurnal entry data for multiple entites then the sytem will detemine which entity information to return based on the user making the request.  This is system dependent.
