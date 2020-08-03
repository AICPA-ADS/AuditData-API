
# AuditData-API
The purpose of the Audit Data API Working Group (Working Group) is to define an API standard for the transfer of financial audit data between two systems. The standard is open and licensed under an MIT license. Participation in the Working Group and contributions are open to all interested parties. The API standard intends to build upon the standards already developed by the AICPA  and to use the terms defined in that standard where applicable. 

## Status
Working Draft

View the standard in the Swagger viewer:
https://xbrlus.github.io/AuditData-API/


## Background
When auditors request client data to analyze in their audits, this data (audit data) is typically transferred to the auditor as discrete data files in a custom format. The scope of audit data covers information that is recorded in financial systems of the company, such as the following: 
1. General ledger including trial balance
1. Sales ledger
1. Purchase ledger 
1. Payroll
1. Inventory
1. PP&E registry
1. Receivables and payables ledgers

Various audit data standards have been proposed by the American Institute of CPAs (AICPA) and the International Organization for Standardization (ISO). Each of these initiatives define file formats for how the financial data should be expressed, but do not define the details of how transmission would occur. These standards also lack expressions of semantic meaning about the underlying data. 

The use of these audit data standards today requires companies to express their current systems in a file format syntax, such as CSV for the AICPA standard, and a database format for the ISO standard. However, these standards do not address how computers request this information, and do not define minimum standards for data transmission between two systems, independent of human involvement. 

The AICPA and XBRL US have initiated work to define an audit data transfer standard in an OPEN API format, that covers the areas listed above.

## Initial Scope
The initial scope of the APIs to be defined will cover General Ledger Transaction details and Trial balance values at a point in time. The scope will then expand to other financial subsystems. The Working Group will focus on developing and publishing the APIs, and promoting their adoption among auditees, ERP companies that work with them, and audit data extraction and analytics providers. 

### Data Security
The the API standard will not provide prescriptive guideance on security topics such as specific authentication/authorization schemes or in-transit data security, and will instead treat those as details to be chosen by between implementing parties. The standard may address additional security concerns by providing implementaiton notes, as required.

