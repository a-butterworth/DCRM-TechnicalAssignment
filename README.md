# CRM Technical Assignment - Power Platform

This solution was built as part of a technical assignment to demonstrate my ability to build and automate within Power Platform. The aim was to create a simple CRM system with core account management functionality, automated data generation, duplicate detection, and validation.

---

## What I Built

- A fully functional model-driven CRM app using Dataverse and Power Automate  
- Two main tables: `Account` and `Assistant`  
- Custom form with required fields and dropdowns  
- Flow to generate unique Sort Codes and Account Numbers  
- Duplicate detection rules to block saving accounts with the same email, name, or address  
- Input validation using Power Platform's built-in field settings  
- Searchable views with Quick Find enabled for Sort Code and Account Number  

---

## Key Features Implemented

### Account Table (`Account`)
- Fields: Name, Address, Email, Account Type (Choice), Initial Deposit, Currency (Choice), Sort Code, Account Number  
- Validation: Required fields enforced; deposit cannot be 0  

### Assistant Table
- Related to Account using lookup field  
- Fields: Name, Email, Phone Number

  ### Currency Table
- Created a separate Currency table and related it to the Account table via a lookup field
- Allows dynamic management of currencies without needing to modify the form or choice fields
- Supports adding, editing, or removing currencies directly from the data layer
- Enables future enhancements like exchange rate integration or reporting by currency

### Flows
- Sort Code & Account Number Generator  
  - `Do Until` loop ensures uniqueness  
  - Prevents creation of duplicate numbers  
- Duplicate Detection  
  - Built-in Dataverse rules used  
  - Triggered on save; blocks exact matches  

### Search & Views
- Quick Find View updated to include Sort Code and Account Number  
- Active Accounts view allows full searching and editing  

---

## Technical Notes

- Used built-in Power Platform validation for required fields and formatting  
- Used Power Automate expressions like:  
  - `concat(string(rand(10,99)), '-', string(rand(10,99)), '-', string(rand(10,99)))` for Sort Code  
  - `string(rand(10000000, 99999999))` for Account Number  
- Built logic to prevent saving accounts with duplicate email, name, or address using exact-match rules and first 5 and last matching characters for name.  
- Used Set Variable and Compose with dynamic content to build expressions  
- Carefully handled Do Until loop structure and error handling (e.g., match checks, circular dependency avoidance)  

---

## Screenshots (see /screenshots folder)

- Model-driven app UI  
- Account form with validation  
- Power Automate flow (overview and loop logic)  
- Duplicate detection rules (email, name, address)  
- Quick Find View setup  
- Search in action for Account Number  

---

## Notes / Trade-offs
 
- Did not implement optional bonus features like postcode API or CI/CD deployment due to time focus on core completion.  

---

## Deployment

All customizations were done in a Power Platform development environment. This repo includes:
- `/screenshots/` folder  
- This `README.md`  

---

## What I'd Add Next (if needed)

- API integration for address lookup (postcode.io)  
- Document upload using SharePoint or Azure Blob  
- Email notification via Power Automate  
- Relevance Search and highlighting potential duplicates before save  

---

