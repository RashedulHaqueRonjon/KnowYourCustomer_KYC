# Medical Equipment KYC Survey System 🏥

A comprehensive Know Your Customer (KYC) data collection system designed for medical equipment suppliers to gather detailed information about healthcare institutions, their equipment, personnel, and future requirements.

## 📋 System Overview

This system consists of 9 interconnected HTML forms that collect various aspects of institutional data, backed by a robust SQL Server database with 16 tables, full CRUD operations, and comprehensive reporting capabilities.

KnowYourCustomer_KYC - Medical KYC Forms and Database Schema
GitHub License

This repository contains a set of HTML forms and a corresponding SQL database schema designed for a "Know Your Customer" (KYC) process in a medical or institutional context.

The forms are simple HTML structures intended to be integrated into a larger web application or used as templates for data collection.

📁 Project Structure
KnowYourCustomer_KYC/
├── forms/
│   ├── form1_institution.html
│   ├── form2_contacts.html
│   ├── form3_doctors.html
│   ├── form4_equipment.html
│   ├── form5_testcount.html
│   ├── form6_future.html
│   ├── form7_satisfaction.html
│   ├── form8_market_intelligence.html
│   └── form9_survey_info.html
├── sql/
│   └── MedicalKYC_DB.sql
├── LICENSE
└── README.md

📝 Files Included
HTML Forms (forms/)
These files represent the front-end structure for the KYC data collection:

File Name			                  Description
form1_institution.html	        Institutional details and primary information.
form2_contacts.html		          Key contact persons and their roles.
form3_doctors.html		          Information regarding affiliated doctors.
form4_equipment.html	          Details about medical equipment and infrastructure.
form5_testcount.html		        Data on test volumes and counts.
form6_future.html		            Future plans and strategic outlook.
form7_satisfaction.html	        Customer satisfaction and feedback.
form8_market_intelligence.html	Market and competitive intelligence data.
form9_survey_info.html	        General survey and meta-information.

Database Schema (sql/)
File Name			      Description
MedicalKYC_DB.sql		SQL script for creating the database and tables to store the KYC data.

🔗 Original Project Reference
This project is a derivative work and a specialized subset of the forms and database structure from the following repository:

MVC UI Template - ASP.NET Core Customer Management System https://github.com/RashedulHaqueRonjon/mvc-ui-template

For the complete, production-ready ASP.NET Core MVC application with full CRUD operations, advanced search, sorting, and pagination, please refer to the original repository.

## 🗂️ Database Architecture

### Database: `MedicalKYC_DB`

**Server:** SQL Server 2016+  
**Total Tables:** 16  
**Views:** 2  
**Stored Procedures:** 31 (24 CRUD + 7 Reporting)

### Core Tables

#### 1. **SupplierInstitutions** (Supplier Master Data)
- Tracks medical equipment suppliers and manufacturers
- Fields: Company info, contact details, local representatives, ISO compliance
- **Key Fields:** SupplierID, SupplierName, Country, ContactDetails, ISO13485_Compliant

#### 2. **Institutions** (Healthcare Facilities)
- Main table for hospitals, diagnostic centers, and medical institutions
- Fields: Name, location, classification, ownership type
- **Key Fields:** InstitutionID, InstitutionName, Type, Classification, Location

#### 3. **Employees** (Sales & Service Team)
- Company employees conducting surveys and visits
- Fields: Employee details, designation, territory, contact info
- **Key Fields:** EmployeeID, EmployeeCode, Name, Territory, Department

#### 4. **ContactPersons** (Institution Personnel)
- Key decision-makers, doctors, purchase officers at institutions
- Fields: Name, designation, contact details, role type
- **Key Fields:** ContactPersonID, ContactName, ContactType, InstitutionID

#### 5. **InstrumentEquipment** (Equipment Master)
- Catalog of all medical equipment types
- Fields: Equipment specs, manufacturer, model, technical details
- **Key Fields:** EquipmentID, EquipmentName, Type, Manufacturer, ModelNumber

#### 6. **InstrumentReagents** (Consumables & Reagents)
- Reagents and consumables for equipment
- Fields: Reagent details, storage conditions, inventory levels
- **Key Fields:** ReagentID, ReagentName, EquipmentID, ExpiryDate, StockLevel

#### 7. **InstrumentEquipmentParts** (Spare Parts)
- Spare parts catalog for maintenance
- Fields: Part details, compatibility, pricing, stock levels
- **Key Fields:** PartID, PartName, EquipmentID, StockLevel, EstimatedCost

#### 8. **InstitutionInstruments** (Installed Equipment)
- Links equipment to institutions (actual installations)
- Fields: Serial numbers, location, warranty, service contracts
- **Key Fields:** InstitutionInstrumentID, InstitutionID, EquipmentID, Status

#### 9. **Visits** (Field Visits)
- Records of all institution visits
- Fields: Visit details, purpose, results, follow-up dates
- **Key Fields:** VisitID, InstitutionID, EmployeeID, VisitDate, VisitType

#### 10. **SurveyQuestions** (Question Bank)
- Standardized survey questions
- Fields: Question text, category, type, required status
- **Key Fields:** QuestionID, QuestionText, QuestionCategory, QuestionType

#### 11. **SurveyResponses** (Survey Answers)
- Stores all survey responses
- Fields: Response text, ratings, verification status
- **Key Fields:** ResponseID, VisitID, QuestionID, ResponseText, ResponseRating

#### 12. **ComplaintRequests** (Customer Complaints)
- Tracks service requests and complaints
- Fields: Complaint details, priority, SLA, resolution
- **Key Fields:** ComplaintID, TicketNumber, Type, Status, Priority

#### 13. **MaintenanceRecords** (Service History)
- Complete maintenance and service history
- Fields: Maintenance type, issues, solutions, costs
- **Key Fields:** MaintenanceID, InstitutionInstrumentID, Date, Type, Result

#### 14. **MaintenanceParts** (Parts Used in Service)
- Links parts used in maintenance activities
- Fields: Part ID, quantity, costs
- **Key Fields:** MaintenancePartID, MaintenanceID, PartID, Quantity

#### 15. **EquipmentDocuments** (Document Repository)
- Stores paths to equipment documents
- Fields: Document type, path, upload details
- **Key Fields:** DocumentID, EquipmentID, DocType, DocPath

#### 16. **StockMovements** (Inventory Tracking)
- Tracks reagent and parts inventory movements
- Fields: Item type, quantity, movement type, reference
- **Key Fields:** StockMovementID, ItemType, ItemID, Quantity, MovementType

### Database Views

#### 1. **vwInstitutionSummary**
- Comprehensive institution overview with aggregated statistics
- Shows: Total contacts, instruments, machines, visits, last visit date

#### 2. **vwInstrumentInventory**
- Equipment inventory summary across all institutions
- Shows: Total units installed, BCOC supplied units, installation locations

### Stored Procedures

#### CRUD Operations (24 procedures)
- **Suppliers:** Create, Read, Update, Delete
- **Institutions:** Create, Read, Update, Delete
- **Employees:** Create, Read, Update, Delete
- **ContactPersons:** Create, Read, Update, Delete
- **Equipment:** Create, Read, Update, Delete
- **Visits:** Create, Read, Update, Delete
- **Complaints:** Create, Read, Update, Delete
- **Maintenance:** Create, Read, Update, Delete

#### Reporting Procedures (7 procedures)
1. `spSearch_Institutions_ByLocationOrType` - Search institutions
2. `spVisits_GetByEmployee` - Employee visit history
3. `spComplaints_Report_ByStatus` - Complaints analytics
4. `spMaintenance_Report_History` - Maintenance history
5. `spEquipment_Utilization_Summary` - Equipment usage stats
6. `spComplaint_Maintenance_LinkReport` - Complaint-to-service tracking
7. Additional custom reporting procedures

---

## 📝 Survey Forms (9 Forms)

### Form 1: Institution Information 🏢
**Purpose:** Capture basic institution details  
**Database Mapping:** `Institutions` table  
**Stored Procedure:** `sp_Institutions_Create`

**Key Sections:**
- Basic Details (Name, Location, Address, Division)
- Institution Classification (Category, Type, Ownership)
- Business Classification (Class A/B/C)

**Sample Fields:**
- Institution Full Name*
- Location/Area*, District*, Division
- Institution Category* (Medical College, Diagnostic Center, etc.)
- Institution Type* (Government/Private/NGO/International)
- Business Ownership* (Proprietorship/Partnership/Corporate/Government)
- Institution Classification* (Class A/B/C)

**Visual Features:**
- Purple gradient header
- Grid-based responsive layout
- Form validation
- Auto-sync between header and form fields

---

### Form 2: Key Influential Person / Decision Maker 👤
**Purpose:** Capture decision-maker information  
**Database Mapping:** `ContactPersons` table (ContactType = 'Key Person')  
**Stored Procedure:** `sp_ContactPersons_Create`

**Key Sections:**
- Person Details (Name, Title, Designation)
- Contact Information (Phone, Email, Preferred Method)
- Availability & Business Card Info

**Sample Fields:**
- Title (Mr./Ms./Dr./Prof.)
- First Name*, Last Name
- Designation* (Lab In-Charge, Purchase Officer, Director, CEO, etc.)
- Department, Phone*, Email
- Preferred Contact Method
- Available Hours
- Business Card Available (Yes/No)
- Online Profile Links (LinkedIn, etc.)

**Visual Features:**
- Dynamic add/remove person entries
- Checkbox group for multiple designations
- Serial number tracking
- Remove button for entries 2+

---

### Form 3: Doctors / Consultants Information 👨‍⚕️
**Purpose:** Capture medical professional contacts  
**Database Mapping:** `ContactPersons` table (ContactType = 'Doctor')  
**Stored Procedure:** `sp_ContactPersons_Create`

**Key Sections:**
- Doctor Details (Title, Name, Qualifications)
- Specialization & Department
- Contact & Availability Info

**Sample Fields:**
- Title* (Dr./Prof./Assoc. Prof./Consultant)
- First Name*, Last Name
- Qualifications (MBBS, BDS, MD, MS, FCPS, FRCS, PhD, MPH)
- Department/Specialization*
- Designation (Head of Department, etc.)
- Phone*, Email
- Preferred Contact Method
- Available Hours
- Online Profiles (LinkedIn, ResearchGate)

**Visual Features:**
- Medical-specific title options
- Multiple qualification checkboxes
- Professional profile links
- Color-coded sections

---

### Form 4: Installed Instruments & Medical Equipment 🔬
**Purpose:** Document all installed equipment  
**Database Mapping:** `InstrumentEquipment` + `InstitutionInstruments` tables  
**Stored Procedure:** `sp_Equipment_Create` + Institution linking

**Key Sections:**
- Equipment Type & Classification
- Manufacturer Details
- Installation & Ownership Info
- Service Contract Details

**Sample Fields:**
- Serial Number
- Instrument Type* (Semi-Automatic/Automatic/Manual)
- Equipment Name/Category*
- Department* (Biochemistry, Hematology, Immunoassay, etc.)
- Country/Source, Manufacturer Company
- Brand Name, Model Number, Serial Number
- Number of Machines*, Asset Tag
- Location Within Institution
- Installation Date, Ownership Type (Owned/Leased/Rental)
- Is BCOC Supplied? (Yes/No)
- Warranty Expiry Date
- Service Contract Status, Provider

**Visual Features:**
- Dynamic equipment entry addition
- Department dropdown with 9 options
- BCOC flag for tracking
- Grid layout for compact data entry

---

### Form 5: Test Count & Laboratory Capacity 📊
**Purpose:** Capture testing volume and capacity metrics  
**Database Mapping:** `SurveyResponses` table  
**Stored Procedure:** Multiple survey response entries

**Key Sections:**
- Monthly Test Volume by Department (8 categories)
- Laboratory Capacity & Utilization
- Staffing & Operations
- Capacity Constraints

**Sample Fields:**
- Biochemistry Tests (monthly count)
- Hematology Tests (monthly count)
- Immunoassay Tests (monthly count)
- ESR Tests (monthly count)
- Microbiology Tests (monthly count)
- Histopathology Tests (monthly count)
- Radiology & Imaging Tests (monthly count)
- Other Tests (monthly count + specify types)
- Total Monthly Capacity (maximum tests)
- Current Utilization Percentage
- Lab Technicians Count
- Medical Technologists Count
- Operating Hours per Day
- Operating Days per Week

**Visual Features:**
- Auto-calculating total tests display
- Annual projection (monthly × 12)
- Color-coded test categories
- Large summary box with gradient background
- Real-time calculation on input

---

### Form 6: Future Prospectus & Equipment Requirements 🎯
**Purpose:** Capture future purchase plans and requirements  
**Database Mapping:** `Visits` + `SurveyResponses` tables  
**Stored Procedure:** `sp_Visits_Create` + survey response entries

**Key Sections:**
- General Purchase Plans
- Specific Equipment Requirements (dynamic entries)
- Current Equipment Issues
- Future Plans & Expansion

**Sample Fields:**
- Planning to Purchase New Equipment?* (Yes/No/Maybe)
- Expected Purchase Timeline (3 months, 6 months, 1 year+)
- Estimated Annual Budget (BDT)
- Departments Needing Upgrade (checkboxes)
- Equipment Type Needed*, Preferred Brand/Model
- Quantity Required, Priority Level*
- Budget Allocated (BDT), Expected Purchase Date
- Reason for Purchase* (New/Replacement/Expansion/Upgrade)
- Current Equipment Issues/Concerns
- New Department Plans
- Capacity Expansion Plans
- Technology Upgrade Plans

**Visual Features:**
- Dynamic equipment requirement entries
- Priority level dropdown (High/Medium/Low)
- Reason for purchase categorization
- Department needs checkboxes
- Comprehensive future planning sections

---

### Form 7: Satisfaction & Service Feedback ⭐
**Purpose:** Gather customer satisfaction ratings and feedback  
**Database Mapping:** `SurveyResponses` table  
**Stored Procedure:** Survey response entries with ratings

**Key Sections:**
- Feedback Provider Information
- Rating Scales (1-10) for 6 aspects
- Qualitative Feedback
- Net Promoter Score
- Priority Areas

**Sample Fields:**
- Provider Type* (Key Person/Doctor/Equipment User/Other)
- Provider Name*, Designation, Department
- Overall Satisfaction with Equipment (1-10 slider)
- Service Response Time Satisfaction (1-10 slider)
- Technical Support Quality (1-10 slider)
- Product Quality Satisfaction (1-10 slider)
- Pricing Satisfaction (1-10 slider)
- Training & Documentation Quality (1-10 slider)
- What Do We Do Well? (Strengths)
- What Can We Improve? (Areas for Improvement)
- Positive Incidents/Experiences
- Negative Incidents/Issues
- Would You Recommend Us?* (5 options)
- Priority Ranking (Top 3)

**Visual Features:**
- Interactive rating sliders (1-10)
- Color-coded slider background (red → yellow → green)
- Large rating value display
- Real-time slider value updates
- Visual scale indicators (Poor → Average → Excellent)

---

### Form 8: Market Intelligence 🏢
**Purpose:** Gather competitive intelligence and market data  
**Database Mapping:** `SurveyResponses` table  
**Stored Procedure:** Survey response entries

**Key Sections:**
- Feedback Provider Information
- Competitor Analysis - General
- Specific Competitor Equipment Details (dynamic)
- Competitive Positioning
- Pricing & Value Perception
- Market Dynamics

**Sample Fields:**
- Using Equipment from Other Suppliers?* (Yes/No)
- Which Companies/Brands? (competitor list)
- Number of Other Suppliers
- Competitor Company Name*, Equipment Type*
- Brand & Model, Department Using
- Why Competitor Chosen Over Us?
- Competitor Advantages/Disadvantages
- Pricing Comparison (6 options)
- Service Quality Comparison (6 options)
- How Our Prices Compare?
- Why Choose Us Over Competitors?
- What Competitors Offer That We Don't?
- Open to Switching Suppliers?
- Market Trends & Observations

**Visual Features:**
- Dynamic competitor equipment entries
- Comparison dropdowns (pricing, service quality)
- Relationship duration tracking
- Market positioning analysis sections
- Comprehensive competitor tracking

---

### Form 9: Survey Information (Final Form) ✅
**Purpose:** Document visit details and action items  
**Database Mapping:** `Visits` table  
**Stored Procedure:** `sp_Visits_Create` + follow-up tracking

**Key Sections:**
- Visit Details
- People Met During Visit
- Findings & Outcomes
- Action Items & Follow-up (3 items)
- Additional Observations
- Business Potential Assessment

**Sample Fields:**
- Visit Date*, Visit Time
- Visit Duration (minutes)
- Number of Forms Completed
- Visit Type* (Initial Survey, Follow-up, Installation, etc.)
- Visit Purpose/Objective*
- Key Person Met, Doctors/Consultants Met
- Key Findings/Observations*
- Agreements Reached, Issues Identified
- Opportunities Discovered
- Customer Mood/Sentiment
- Action Required (3 items with assignee, due date, priority)
- Next Follow-up Date*
- Equipment Status Observed
- Staff Competency Level
- Estimated Annual Revenue Potential (BDT)
- Customer Classification (Key Account, Major, Standard, etc.)
- Relationship Quality
- Probability of Next Purchase

**Visual Features:**
- Green completion banner ("Final Form")
- 3 pre-configured action item sections
- Business potential assessment
- Customer classification dropdown
- Relationship quality indicators
- Purchase probability assessment

---

## 🎨 Design Features

### Consistent UI Elements Across All Forms

1. **Header Section**
   - Purple gradient background (#667eea → #764ba2)
   - White text with hospital emoji
   - Form number indicator (e.g., "Form 2 of 9")

2. **Form Header Bar**
   - Light gray background (#f8f9fa)
   - Institution Name*, Institution ID, Date*, Employee ID*, Employee Name
   - Grid layout (5 columns, responsive)
   - Auto-fills today's date

3. **Form Content Area**
   - White background
   - Purple section titles (#667eea)
   - Gray subsections (#f8f9fa)
   - Rounded corners (border-radius: 10px-15px)
   - Box shadows for depth

4. **Input Fields**
   - Border color: #dee2e6
   - Focus color: #667eea with glow effect
   - 12px padding, 14px font size
   - Smooth transitions (0.3s)

5. **Buttons**
   - Submit: Purple gradient background
   - Add: Green (#28a745)
   - Remove: Red (#dc3545)
   - Hover effects with elevation
   - Font weight: 600

6. **Footer Section**
   - Light gray background
   - Declaration checkbox (required)
   - Submit button with hover animation
   - Required field indicator (red asterisk)

7. **Responsive Design**
   - Grid layouts collapse to single column on mobile
   - Touch-friendly input sizes
   - Optimized for tablets and phones

### Form-Specific Visual Elements

- **Form 5:** Auto-calculating total display with gradient background
- **Form 7:** Interactive sliders with color gradient (red → yellow → green)
- **Form 9:** Green completion banner indicating final form

---

## 🚀 Installation & Setup

### Prerequisites
- SQL Server 2016 or higher
- Web server (IIS, Apache, or Node.js)
- Modern web browser (Chrome, Firefox, Edge, Safari)

### Database Setup

1. **Create Database:**
```sql
-- Run the complete MedicalKYC_DB.sql script
-- This will:
-- 1. Drop existing database (if any)
-- 2. Create fresh database
-- 3. Create all 16 tables
-- 4. Create 2 views
-- 5. Create 31 stored procedures
-- 6. Insert 15 sample records per table
-- 7. Execute test CRUD operations
```

2. **Verify Installation:**
```sql
-- Check table counts
SELECT 
    'Suppliers' AS TableName, COUNT(*) AS RecordCount FROM dbo.SupplierInstitutions
UNION ALL SELECT 'Institutions', COUNT(*) FROM dbo.Institutions
UNION ALL SELECT 'Employees', COUNT(*) FROM dbo.Employees
-- ... (see script for full verification query)

-- Expected output: 15 records per table
```

3. **Test CRUD Operations:**
```sql
-- Test procedures are included in the script
-- They automatically execute and display results
-- Check console output for success messages
```

### Web Forms Setup

1. **Deploy HTML Files:**
```bash
# Place all form files in web server directory
forms/
  ├── form1_institution.html
  ├── form2_contacts.html
  ├── form3_doctors.html
  ├── form4_equipment.html
  ├── form5_testcount.html
  ├── form6_future.html
  ├── form7_satisfaction.html
  ├── form8_market_intelligence.html
  └── form9_survey_info.html
```

2. **Configure Backend API (Required for Production):**
```javascript
// Example API endpoints needed:
POST /api/institutions          // Form 1
POST /api/contact-persons       // Forms 2, 3
POST /api/equipment             // Form 4
POST /api/institution-instruments // Form 4 (linking)
POST /api/visits                // Forms 5, 6, 7, 8, 9
POST /api/survey-responses      // Forms 5, 6, 7, 8
POST /api/complaints            // As needed
POST /api/maintenance           // As needed
```

3. **Update Form JavaScript:**
```javascript
// Uncomment production fetch calls in each form
// Example from form1_institution.html:
fetch('/api/institutions', {
    method: 'POST',
    headers: { 'Content-Type': 'application/json' },
    body: JSON.stringify(completeData)
})
.then(response => response.json())
.then(result => {
    alert('Institution created with ID: ' + result.InstitutionID);
    // Proceed to Form 2
});
```

---

## 📊 Data Flow Diagram

```
User Input (Forms 1-9)
        ↓
JavaScript Data Collection
        ↓
API Endpoint (Backend)
        ↓
Stored Procedures (SQL Server)
        ↓
Database Tables (MedicalKYC_DB)
        ↓
Views & Reports
```

### Form-to-Table Mapping

| Form | Primary Table(s) | Stored Procedure |
|------|------------------|------------------|
| Form 1 | Institutions | sp_Institutions_Create |
| Form 2 | ContactPersons | sp_ContactPersons_Create |
| Form 3 | ContactPersons | sp_ContactPersons_Create |
| Form 4 | InstrumentEquipment, InstitutionInstruments | sp_Equipment_Create + linking |
| Form 5 | SurveyResponses | sp_Visits_Create + responses |
| Form 6 | Visits, SurveyResponses | sp_Visits_Create + responses |
| Form 7 | SurveyResponses | Survey response entries |
| Form 8 | SurveyResponses | Survey response entries |
| Form 9 | Visits | sp_Visits_Create |

---

## 🔍 Sample Database Queries

### Get Institution Summary
```sql
SELECT * FROM vwInstitutionSummary 
WHERE IsActive = 1 
ORDER BY TotalMachines DESC;
```

### Get Equipment Inventory
```sql
SELECT * FROM vwInstrumentInventory
ORDER BY TotalUnitsInstalled DESC;
```

### Search Institutions by Location
```sql
EXEC spSearch_Institutions_ByLocationOrType 
    @Location = 'Dhaka',
    @InstitutionType = NULL;
```

### Get Employee Visit History
```sql
EXEC spVisits_GetByEmployee 
    @EmployeeID = 1,
    @StartDate = '2025-01-01',
    @EndDate = '2025-12-31';
```

### Complaints Report by Status
```sql
EXEC spComplaints_Report_ByStatus 
    @StartDate = '2025-01-01',
    @EndDate = '2025-12-31';
```

### Maintenance History Report
```sql
EXEC spMaintenance_Report_History 
    @InstitutionID = 1000,
    @EquipmentID = NULL,
    @StartDate = '2024-01-01',
    @EndDate = '2025-12-31';
```

### Equipment Utilization Summary
```sql
EXEC spEquipment_Utilization_Summary 
    @EquipmentID = NULL;
```

---

## 📈 Reporting & Analytics

### Available Reports

1. **Institution Analytics**
   - Total institutions by type and classification
   - Geographic distribution
   - Equipment installation patterns
   - Visit frequency and trends

2. **Equipment Reports**
   - Total installations by equipment type
   - Manufacturer market share
   - BCOC supplied equipment tracking
   - Service contract status

3. **Sales Activity Reports**
   - Employee visit statistics
   - Territory coverage
   - Conversion rates
   - Follow-up compliance

4. **Service Reports**
   - Complaint resolution times
   - Maintenance schedule adherence
   - Parts usage patterns
   - Service cost analysis

5. **Customer Satisfaction**
   - Average ratings by aspect
   - Net Promoter Score (NPS)
   - Feedback trends
   - Issue categories

6. **Market Intelligence**
   - Competitor presence by institution
   - Pricing comparisons
   - Market share analysis
   - Win/loss tracking

---

## 🔐 Security Considerations

### Database Security
- Use SQL Server authentication with strong passwords
- Grant minimum required permissions to application users
- Enable SQL Server audit logging
- Regular backup schedule (daily recommended)

### Web Application Security
- Implement user authentication (not included in forms)
- Use HTTPS for all form submissions
- Sanitize all user inputs before database insertion
- Implement rate limiting on API endpoints
- Store sensitive data encrypted

### Data Privacy
- Comply with local data protection regulations
- Implement data retention policies
- Provide data export functionality for users
- Maintain audit trail for data access and modifications

---

## 🛠️ Maintenance & Support

### Regular Maintenance Tasks

1. **Weekly:**
   - Review incomplete surveys
   - Check follow-up dates
   - Monitor complaint resolution times

2. **Monthly:**
   - Generate sales activity reports
   - Review equipment maintenance schedules
   - Analyze customer satisfaction trends
   - Update supplier information

3. **Quarterly:**
   - Database performance optimization
   - Archive old records
   - Review and update question bank
   - Conduct user training refreshers

4. **Annually:**
   - Database backup verification
   - Security audit
   - System performance review
   - Feature enhancement planning

### Troubleshooting

**Common Issues:**

1. **Form submission fails:**
   - Check browser console for JavaScript errors
   - Verify API endpoint connectivity
   - Ensure all required fields are filled

2. **Data not saving to database:**
   - Verify stored procedure execution
   - Check database connection string
   - Review SQL Server error logs

3. **Duplicate entries:**
   - Implement unique constraints on key fields
   - Add validation before insert operations
   - Use MERGE statements instead of INSERT

---

## 📞 Support & Contact

For technical support or feature requests, please contact:
- **Database Administrator:** [Your Contact]
- **Application Developer:** [Your Contact]
- **Project Manager:** [Your Contact]

---

## 📄 License

This project is proprietary software. All rights reserved.

---

## 🙏 Acknowledgments

- SQL Server database design best practices
- Bootstrap-inspired CSS framework
- Modern web form UX patterns
- Medical equipment industry standards

---

## 📚 Additional Resources

- SQL Server Documentation: https://docs.microsoft.com/en-us/sql/
- Web Forms Best Practices: https://www.w3.org/WAI/tutorials/forms/
- Medical Device Regulations: [Operating country's regulatory body]

---

**Version:** 2.0  
**Last Updated:** November 2025  
**Status:** Production Ready

---

## 🎯 Quick Start Guide

1. ✅ Run `MedicalKYC_DB.sql` to create database
2. ✅ Verify 15 sample records in each table
3. ✅ Deploy HTML forms to web server
4. ✅ Configure backend API endpoints
5. ✅ Test Form 1 submission end-to-end
6. ✅ Train users on form completion process
7. ✅ Begin data collection!

---

**Ready to revolutionize your customer data collection! 🚀**
