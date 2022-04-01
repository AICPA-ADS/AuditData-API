# General Ledger Primer
The general ledger API is based on the AICPA Audit Standard with additional content added to support an API interface.

## Intent of the Standard

The intent of the standard is to facilitate the transfer of financial data between users across different systems. The primary purpose is to enable the extraction of detailed financial data for the performance of financial audits.  This is not the sole intent of the standard, and the specification is written in a manner to support the general transfer of financial data between systems for any range of purposes.

## General Ledger API Rest Points

The General ledger supports the following API end points:

* Journal entries
* Trial balance
* Accounts
* XBRL Trial Balance

### Journal entries

The journal entries end point allows a user to request journal entries for a specific entity for a specific time range. If no request parameter is defined, then the system will attempt to return all available journal entries that the specific user making the request is permitted to see. 

To return data for a specific time range the user provides the start date and the end date.  This date refers to the effective date of the journal entry.

If the system contains journal entry data for multiple entities then the system will return the journals based on the entity id that must be provided as a component of the request.

The journal entries include 4 different amounts that can be reported for each transaction with an associated currency. These are:
* Functional Amount
* Reporting (Presentation) Amount
* Local Amount
* Transaction Amount

#### Functional Amount
The functional amount is the primary currency in which the economic activity of the entity occurs. This is the entities operating currency and is determined by the management of the entity. The functional currency is typically the local currency of where the entity resides, but doesn't have to be.  An entity based in Deleware for example may conduct the majority of it operations in the UK and may decide to have a functionional currency of GBP vs USD.

#### Reporting (Presentation) Amount
The reporting amount refers to the currency that is used to report the financial statements. The functional currency of a subsidiary using GBP may differ from the functional currency of its parent company using USD that reports the consolidated results in USD. In this case the reporting currency of the subsidiary (USD) would differ from its functional currency of GPB.

#### Local Amount
The currency of the country where the entity is operating is referred to as the local currency. In most cases the local currency will be the same as the functional currency of the entity. A currency that is different than an entity's functional currency is for accounting purposes treated as a forign currency, and thus subject to Forign Exchange adjustments.

#### Transaction Amount
The transaction amount is the value in the currency in which the transaction occured. All journals should have a transactional amount.  This reflects that actual currency that was used to conduct the transcation.  For a domestic entity this will typically be the same as the functional currency. Every journal must have a Transaction amount and currency.



### Trial Balance

The trial balance end point allows a user to request journal entries for a specific period end.  The end date must be provided.  The default trial balance will return values for the latest reporting year. If a start date is provided, then the period from the specified start date to the specified end date will be provided if available.  All available periods can be queried using the period end-point. (see base modules below).  The start date must use the start date provided from the period rest point.

Only one reporting period is returned at a time. 

The opening balances returned are the opening balances after opening adjustments to retained earnings and adjustments for changes in accounting standards.  To define a traditional year to year comparison of a trial balance two API calls would be made for the period ends requested. The opening balances are equal to the end of period balance + opening period journals.

Additional parameters can be provided to get budget information by passing a budget flag parameter with a value of budget.  If no value is provided the default value is the actual value.

If the system has information on multiple entities the entity parameter allows information for a specific entity to be requested using a system assigned entity identifier. If the entity identifier is not provided the default entity is returned. This is implementation specific.

### Accounts

The accounts entry point allows a user to request the chart of accounts for a given entity.  The user can pass the entity identifier as a parameter to retrieve the chart of accounts for that entity.  If no parameter is passed all the accounts of all entities available to the user are returned. Each account record includes the entity identifier.

The end points returns details of each account defined in the chart of the accounts for the entity.  This does not include balance or journal information. These details are available in the Trial Balance and Journal end points.

### Trial Balance XBRL

The trial balance in XBRL end point allows the user to retrieve an XBRL instance of the trial balance in an XBRL-JSON format. The API allows the user to pass the end date, the entity identifier and a specific G/L account number.

## Structure of Returned Data

The data returned is generally flat.  The structure of the returned data deliberately  avoids  nested structures. This is to allow maximum flexibility to support transfer from as many systems as possible.  This means some data is repeated in every set of data returned such as the entity name. The journal entry data is the one exception however where the lines to the journal entry are nested as a child of the journal entry. This was not flattened as the majority of systems will have a one to many relationship defined for a specific  journal and the line items of the journal.

Not all data has to be returned in the return fields as in many systems the data defined in the standard will not be available.  The API however does define for each end point some minimal data fields that do have to be returned.  For example, a journal entry end point must return the following:

* Journal_ID
* Effective_Date
* GL_Account_Number
* Amount
* Amount_Currency
* Amount_Credit_Debit_Indicator

Requied fields are defined in the schema section of the [swagger](https://xbrlus.github.io/AuditData-API/#/) interface. Required fields are indicated with a red star.
## Base Modules

The General Ledger module uses the base module to retrieve period and entity related information. The base module includes the following end points:
* Periods
* Entities

These end points provide meta data about the entities and periods available from the API.  These endpoints are separated out from the general ledger category as they would be used by other API modules.  The end points available in the base module are as follows:

### Periods

The periods end point allows the user to request the valid reporting periods of a given entity or all entities available to the requester.  No parameters are required for this end point.  However, the user can request reporting periods by start date, end date and entity.  The start date parameter returns all reporting periods with an end date equal to or greater than the end date. The end date parameter returns all reporting periods with an end date equal or less than the end date.

### Entities

The entities end point allows the user to request all available entities available to the user on the system. The entities end point has one optional parameter for entity identifier. This parameter allows the user to get specific information about a specific entity. The end point returns the entity identifier the entity name and any subsidiary entities.


