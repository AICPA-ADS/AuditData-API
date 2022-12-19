
# AuditData-API
The purpose of the Audit Data API Working Group (Working Group) is to define an API standard for the transfer of financial audit data between two systems. The standard is open and licensed under an MIT license. Participation in the Working Group and contributions are open to all interested parties. The API standard intends to build upon the standards already developed by the AICPA  and to use the terms defined in that standard where applicable. 

## Status
Working Draft

View the standard in the Swagger viewer:
https://aicpa-ads.github.io/ or in the redoc viewer https://aicpa-ads.github.io/AuditData-API/redoc.html


## Background
When auditors request client data to analyze in their audits, this data (audit data) is typically transferred to the auditor as discrete data files in a custom format. The scope of audit data covers information that is recorded in financial systems of the company, such as the following: 
1. [General ledger including trial balance](https://github.com/xbrlus/AuditData-API/blob/master/GL-Primer.md)
1. Sales ledger / Accounts Receivable
1. Purchase ledger / Accounts Payable
1. Inventory
1. PP&E registry
1. Payroll

Various audit data standards have been proposed by the American Institute of CPAs (AICPA) and the International Organization for Standardization (ISO). Each of these initiatives define file formats for how the financial data should be expressed, but do not define the details of how transmission would occur. These standards also lack expressions of semantic meaning about the underlying data. 

The use of these audit data standards today requires companies to express their current systems in a file format syntax, such as CSV for the AICPA standard, and a database format for the ISO standard. However, these standards do not address how computers request this information, and do not define minimum standards for data transmission between two systems, independent of human involvement. 

The AICPA and XBRL US have initiated work to define an audit data transfer standard in an OPEN API format, that covers the areas listed above.

## Scope
The  scope of the APIs covers the following:
* General Ledger Transaction details 
* Trial balance values at a point in time
* Sales Ledger and Accounts Receivable
* Purchase Ledger and Accounts Payable
* Inventory

In addition the API's cover the definition of Users and Entities. These can be used across the different scope area's using consistent keys.

The Working Group focused on developing and publishing the APIs, and promoting their adoption among auditees, ERP companies that work with them, and audit data extraction and analytics providers. 

The API does not cover Property Plant and Equipment or Payroll.

### Data Security
The the API standard will not provide prescriptive guidance on security topics such as specific authentication/authorization schemes or in-transit data security, and will instead treat those as details to be chosen between implementing parties. The standard may address additional security concerns by providing implementation notes, as required.

