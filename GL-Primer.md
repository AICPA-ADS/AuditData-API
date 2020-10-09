# General Ledger Primer
The general ledger API is based on the AICPA Audit Standard with additional content added to support an API interface.

## Intent of the Standard

The intent of the standard is to facilitate the transfer of financial data between users across different systems. The primary purpose is to enable the extraction of detailed financial data for the performance of financial audits.  This is not the sole intent of the standard, and it the specification is wiritten in a manner to supoort the general transfer of financial data between systems for any range of purposes.

## General Ledger API Rest Points

The General leddger supports the following API end points:

* Journal entries
* Trial balance
* Accounts
* XBRL Trial Balance

### Journal entries

The journal entries end point allows a user to request journal entries for a specific entity for a specific time range. If no request parameter is defined then the system will attempt to return all available journal entries that the specific user making the request is permitted to see. 

To return data for a specific time range the user provides the start date and the end date.  This date refers to the effective date of the journal entry.

If the system contains jopurnal entry data for multiple entites then the sytem will detemine which entity information to return based on the user making the request.  This is system dependent.


### Trial Balance

The trial balance end point allows a uesr to request journal entries for a specific period end.  The end date must be provided.  The default trial balance will return values for the latest reporting period. If a start date is provided then the period from the specified start date to the specified end date will be provided if available.  All available periods can be queried using the period end-point. (see below)

Only one reporting period is returned at a time. 

Additional parameters can be provided to get budget information by passing a budget flag parameter with a value of budget.  If no value is provided the default value is the actual value.

If the system has information on mutiple entities the entity parameter allows information for a specific entity to be requested using a system assigned entity identifier. If the entity identifier is not provided the default entity is returned. This is implementation specific.

### Accounts

The accounts entry point allows a user to request the chart of accounts for a given entity.  The user can pass the entity identifier as a parameter to retrive the chart of accounts for that entity.  If no parameter is passed all the acconts of all entities available to the user are returned. Each account record includes the entity identifier.

The end points returns details of each account defined in the chart of the accounts for the entity.  This does not include balance or journal information. These details are available in the Traial Balance and Journal end points.

### Trial Balance XBRL


## Base Modules

The General Ledger module uses the base module to retrieve period and entity related information. The base module includes the following end points:
* Periods
* Entities

These end points provide meta data about the etiies and periods available from the API.  These endpoints are seperated out from the general ledger category as they would be used by other API modules.  The end points avialble in the base module are as follows:


### Periods

The periods end point allows the user to request the valid reporting periods of a given entity or all entities available to the requester.  No parameters are required for this end point.  However the user can request reporting periods by start date, end date and entity.  The start data parameter returns all reporting periods with an end date equal or greater than the end date. The end data parameter returns all reporting periods with an end date equal or less than the end date.

### Entities

The entities end point allows the user to request all available entities availble to the user on the system. The entities end point has one optional parameter for entity identifier. This parameter allows the user to get specific information about a specific entity. The end point returns the entity identifer the entity name and any subsidiariay entities.


