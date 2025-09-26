Phase 1: Problem Understanding & Industry Analysis

Industry Problem: Traditional recruitment systems lack transparency and coordination between recruiters, HR, and candidates. Processes like job posting, candidate screening, interview scheduling, and onboarding are often siloed.

Solution: TalentBridge addresses this by providing a unified Salesforce-based HR Portal with the following goals:

Streamline job and candidate management.

Automate application and interview processes.

Provide dashboards for performance tracking.

Enhance collaboration between HR and recruiters.

Industry Relevance: Recruitment technology (HRTech) is trending toward automation and AI. Our project positions Salesforce as a customizable recruitment solution.

Phase 2: Org Setup & Configuration

Org Setup: Salesforce Developer Org created and configured for HR Portal.

User Roles & Profiles:

Recruiter – job posting, candidate sourcing.

HR – candidate selection, onboarding, final decisions.

System Administrator – full access, configuration.

Permission Sets: Defined for recruiters and HR users to access custom objects like Jobs_c__c, Candidate__c, Application__c, OnboardingTask__c.

App & Tabs: Created a custom app TalentBridge with tabs for Jobs, Candidates, Applications, and Dashboard.

Phase 3: Data Modeling & Relationships

Custom objects created to represent recruitment lifecycle:

Jobs_c__c – Stores job openings.

Fields: Title__c, Location__c, Status__c, CreatedDate.

Status values: Open, Closed.

Candidate__c – Represents applicants.

Fields: Name, Email__c, Experience__c.

Application__c – Links candidates to jobs.

Fields: Candidate__c (Lookup), Job__c (Lookup), Stage__c.

Stage values: Applied, In Review, Selected, Rejected.

OnboardingTask__c – Tracks onboarding tasks.

Fields: TaskName__c, AssignedTo__c, TaskType__c (Picklist), Status__c.

Relationships:

Job → Application → Candidate (Master-Detail/Lookup).

One job can have many applications, one candidate can apply for many jobs.

Phase 4: Process Automation (Admin)

Record-Triggered Flows:

When Application stage = Selected, send an email to candidate.

When Job status = Closed, prevent new applications.

Approval Process:

Optional HR approval for final job closure.

Validation Rules:

Candidate email format check.

Job cannot be closed unless all applications are processed.

Phase 5: Apex Programming (Developer)

Apex Classes Developed:

HRPortalController.cls – Core CRUD and logic for jobs, applications, candidates, interviews, and onboarding tasks.

Methods: createJob, updateApplicationStatus, scheduleInterview, sendOfferLetter, getAllCandidates, getHRUsers.

TalentBridgeDashboardController.cls – Provides summarized data for dashboards.

Returns: Job stats, Application stats, Candidate stats, Jobs by Day, Applications by Day.

Best Practices Applied:

@AuraEnabled methods for LWC integration.

SOQL queries optimized with selective fields.

Exception handling with proper error messages.

Phase 6: User Interface Development

Lightning Web Components (LWCs):

talentBridgeLWC – Central dashboard displaying KPIs (Jobs, Applications, Candidates), trends, and statistics.

applicationManagement – Manage candidate applications.

onboardingManagement – Handle onboarding tasks with picklists.

interviewScheduling – Schedule and manage interviews.

offerManagement – Generate and send offer letters.

UI Enhancements:

Styled KPI cards with color highlights.

Responsive grid layout using SLDS.

DataTables for tabular job/application trends.

Phase 7: Integration & External Access

Email Integration: Offer letters and application status notifications sent via Salesforce email templates.

Future Scope:

Candidate portal via Salesforce Experience Cloud.

Integration with LinkedIn or external job boards using REST APIs.

Phase 8: Data Management & Deployment

Data Migration: Sample job, candidate, and application records loaded using Data Loader.

Change Sets / SFDX:

Deployed Apex classes and LWCs from sandbox/dev org to production-ready org.

Handled field-level security assignments.

Error Fixes: Adjusted object API names (Jobs_c__c) to ensure alignment.

Phase 9: Reporting, Dashboards & Security Review

Reports:

Applications by Stage.

Jobs by Status.

Candidates per Job.

Dashboards:

TalentBridge Dashboard (custom LWC using Apex data).

Visualization of job openings, application trends, and candidate counts.

Security Review:

Applied with sharing in Apex controllers.

Checked CRUD/FLS compliance before DML/queries.

Profiles and permission sets aligned with user roles.

Phase 10: Final Presentation & Demo Day

Business Impact:

Reduced manual coordination between HR and recruiters.

Real-time tracking of hiring funnel.

Improved candidate experience with timely communication.

Conclusion

TalentBridge is a comprehensive Salesforce-based recruitment management system. It leverages Salesforce declarative and programmatic features to solve real-world HR challenges. With further expansion (Experience Cloud for candidates, API integrations with LinkedIn), it can evolve into a full-scale HRTech product.
