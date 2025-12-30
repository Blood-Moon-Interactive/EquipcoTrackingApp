Equipco Tracking App

PROJECT OVERVIEW

The Equipco Tracking App is a professional-grade Power Apps solution designed to centralize and streamline the management of company-owned equipment. Developed to replace manual, fragmented tracking methods, the application provides 
a transparent audit trail for assets ranging from IT hardware like laptops and monitors to specialized specialty tools. The goal is to improve accountability, reduce equipment loss, and provide management with real-time insights 
into the lifecycle and condition of all assets.

BUSINESS OBJECTIVES

Accountability: Establish a consistent method for tracking item possession and condition.

Visibility: Provide clear insights into equipment usage and current condition to reduce misplacement.

Automation: Replace manual workflows for checkout confirmation and damage reporting.

Accessibility: Enable employees to reserve and check out items quickly from any device.

KEY FEATURES

1. Equipment Inventory Management
Maintains a master list of equipment including item names, categories, and current status.
Tracks asset conditions such as "Good," "Needs Repair," or "Broken".
Allows administrators to add, edit, or retire inventory.

2. User Reservations & Checkouts
Searchable and filterable interface for employees to view available inventory.
Simplified reservation and checkout confirmation process.

3. Damage & Repair Workflow
Integrated damage reporting for employees upon returning equipment.
Automatic status updates to "Needs Repair" or "Under Repair" to trigger maintenance workflows.

4. Dynamic Reporting Dashboards
Visual breakdown of total inventory by category.
Real-time tracking of currently checked-out items and items flagged for repair.

🛠 Technical Stack

Platform: Microsoft Power Apps (Canvas App).
Data Source: SharePoint Lists.
UI/UX: Designed for ease of use with clear visual indicators (colors/icons) for status.

LESSONS LEARNED

Handling Data Delegation
One of the primary challenges was calculating the "Grand Total" of equipment value from SharePoint. Using the standard Sum() function triggered delegation warnings, meaning the app would only calculate totals for the first 500–2,000 items.

Solution: I implemented a Collection strategy, using ClearCollect on screen load to bring the data into the app's local memory. This allowed for accurate, real-time math without delegation limitations.

Complex Multi-Conditional Filtering
The BRD required a clear distinction between items needing repair and items that should no longer be in the active repair loop.

Challenge: Filtering for "Needs Repair" while simultaneously excluding "Retired" items based on user-controlled toggles.

Solution: Developed a nested If logic within the Filter function: Filter(Equipment, Condition.Value = "Needs Repair", If(Toggle1.Value, !Retired, true)) This allowed the UI to dynamically shift between "Active Maintenance" and "Historical Damage" views.

UI Versatility with State Variables
To keep the app lightweight and maintainable, I utilized a single Template Screen for multiple reports.

Solution: By passing Context Variables (e.g., varReportMode) through the Maps function, I enabled the app to dynamically change titles, chart types, and table columns based on the user's selection, significantly reducing the app's complexity and loading time.
