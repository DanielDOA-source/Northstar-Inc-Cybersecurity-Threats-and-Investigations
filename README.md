# Northstar-Inc-Cybersecurity-Threats-and-Investigations
# 🔐 Cybersecurity Log Analysis & Threat Investigation
### SQL Data Analytics Portfolio Project | MySQL

---

## 1. Executive Summary

This project involved a SQL-based cybersecurity investigation of login activities, employee accounts, devices, IP address reputation, and security alerts for **Northstar Services**, a fictional organization experiencing concerns about failed logins, suspicious IP activity, and unresolved security alerts.

The objective was to use SQL to investigate security-related data, identify unusual activity patterns, evaluate potential risks, and develop analytical insights to support management's decision-making.

The analysis leveraged relational data, aggregation, conditional logic, Common Table Expressions (CTEs), window functions, ranking, date/time analysis, and reusable SQL views to examine security activity from multiple perspectives.

The project demonstrates the practical application of SQL for data exploration, analytical problem-solving, risk investigation, and business reporting.

---

## 2. Project Objectives

The investigation was designed to:

- Understand overall login activity, including successful and failed authentication attempts.
- Identify patterns in failed login activity by time, employee, device, department, and IP address.
- Investigate IP address reputation and potentially risky login activity.
- Analyze employee account access patterns and device usage.
- Evaluate security alerts, severity, resolution status, and response times.
- Compare departmental security metrics with overall company performance.
- Identify unusual activity that may warrant further investigation.
- Develop reusable SQL summaries to support recurring security monitoring.

---

## 3. Business Problem

Northstar Services' IT department had concerns about an increase in failed login attempts, unfamiliar IP addresses, and unresolved security alerts.

Management required a data-driven investigation to better understand:

- Where authentication failures were concentrated.
- Whether certain accounts, devices, departments, or IP addresses exhibited unusual activity.
- Whether successful logins were associated with potentially high-risk IP addresses.
- Whether security alerts were being resolved effectively.
- Which areas should receive priority for further investigation.

The project approached these concerns through structured SQL analysis, with an emphasis on identifying evidence-based risk indicators rather than assuming a cyberattack had occurred.

---

## 4. Dataset & Database Structure

The analysis used five relational tables containing employee, device, login, security alert, and IP reputation information.

| Table | Description | Key Analytical Use |
|---|---|---|
| `employees` | Employee account, department, job role, and employment information | Account-level and departmental analysis |
| `devices` | Device identifiers, device types, and operating systems | Device usage and login failure investigation |
| `login_logs` | Login timestamps, employee IDs, device IDs, IP addresses, login status, and failure information | Authentication activity analysis |
| `security_alerts` | Alert types, severity, timestamps, resolution status, and related security information | Alert monitoring and response analysis |
| `ip_reputation` | IP addresses, countries, risk classifications, and reputation information | IP risk investigation |

### Data Relationships

The project combines these datasets through employee, device, login, and IP address identifiers to enable cross-table investigation.

---

## 5. Key Business Questions

| Investigation Area | Key Questions |
|---|---|
| Login Activity | How many login attempts occurred? What percentage succeeded or failed? When were failures most frequent? |
| Employee Accounts | Which accounts had the highest failed-login counts? Were repeated failures followed by successful logins? |
| IP Investigation | Which IP addresses generated the most login attempts and failures? Were successful logins associated with high-risk IPs? |
| Employee & Device Analysis | Which employees used multiple devices? Which devices or departments had higher failure rates? Was activity occurring outside typical working hours? |
| Security Alerts | Which alert types and severity levels were most common? Which alerts remained unresolved? How long did resolution take? |
| Trend Analysis | How did failed-login activity change daily? Were there periods of noticeable increases? |
| Advanced Analytics | How did departmental failure rates compare with the company-wide rate? Which accounts and alerts should be prioritized? |

---

## 6. SQL Techniques & Concepts Applied

| SQL Technique | Application in Project | Analytical Value |
|---|---|---|
| `SELECT`, `WHERE`, `ORDER BY` | Data retrieval, filtering, and sorting | Isolating relevant security records |
| `GROUP BY` | Summarizing login activity by employee, IP, device, department, date, severity, and alert type | Identifying concentrations and patterns |
| Aggregate Functions | `COUNT()`, `SUM()` | Quantifying authentication activity and alerts |
| Conditional Aggregation | `CASE WHEN`, conditional `SUM()` and `COUNT()` | Calculating successful logins, failed logins, and failure rates |
| Joins | `INNER JOIN`, `LEFT JOIN` | Connecting employee, login, device, IP, and alert data |
| Common Table Expressions | `WITH` clauses | Organizing multi-step analysis and intermediate calculations |
| Window Functions | `LAG()` | Comparing current activity with preceding events or periods |
| Ranking Functions | `DENSE_RANK()` | Ranking employees by failed login attempts |
| Date & Time Functions | `DATE()`, `DAYNAME()`, `DAYOFWEEK()`, `HOUR()`, `TIME()` | Analyzing activity by date, weekday, hour, and working-time patterns |
| Percentage Calculations | Failure rates and success/failure proportions | Enabling fair comparisons across departments and groups |
| `HAVING` | Filtering grouped results | Identifying accounts and devices meeting investigation thresholds |
| `TIMESTAMPDIFF()` | Calculating alert resolution duration | Evaluating security response time |
| SQL Views | `CREATE OR REPLACE VIEW` | Creating reusable reporting datasets |
| Subqueries | Filtering and comparing against aggregate values | Supporting analytical logic and investigation rules |

---

## 7. Investigation Summary & Aggregated Analytical Tables

The following tables summarize the scope of the SQL analysis and the types of outputs generated by the queries.

*Note: The SQL file contains query logic, but verified query result exports were not included. Therefore, actual counts, percentages, rankings, and measured findings are not reported here.*

### 7.1 Login Activity Summary

| Metric | SQL Analysis Performed | Business Purpose |
|---|---|---|
| Total Login Events | Counted login records | Measure overall authentication activity |
| Dataset Time Range | Identified earliest and latest login timestamps | Establish the period covered |
| Successful Logins | Counted successful authentication events | Understand legitimate access activity |
| Failed Logins | Counted failed authentication events | Measure authentication issues or potential risk |
| Success Rate | Calculated successful attempts as a percentage of total | Assess login outcomes |
| Failure Rate | Calculated failed attempts as a percentage of total | Monitor unsuccessful authentication activity |
| Failed Logins by Weekday | Grouped failures by day of the week | Identify temporal patterns |
| Failed Logins by Hour | Grouped failures by hour | Detect periods of elevated activity |

### 7.2 Employee Account Risk Summary

| Metric | Analytical Approach | Purpose |
|---|---|---|
| Failed Attempts by Employee | Grouped failed logins by employee | Identify accounts with concentrated failures |
| Employee Failure Ranking | Applied `DENSE_RANK()` | Prioritize accounts for review |
| Repeated Failures Followed by Success | Used `LAG()` to examine login sequences | Identify authentication patterns requiring investigation |
| Employee Failure Rate | Compared failed attempts with total login attempts | Assess account-level login performance |
| After-Hours Activity | Filtered weekend and out-of-hours login records | Identify activity outside assumed normal working hours |
| Multiple Device Access | Counted distinct devices per employee | Understand device usage patterns |

### 7.3 IP Address Risk Summary

| Metric | Analytical Approach | Purpose |
|---|---|---|
| Total Attempts by IP | Grouped login records by IP address | Identify high-volume IP addresses |
| Failed Attempts by IP | Filtered and counted failed logins by IP | Identify IPs generating repeated authentication failures |
| IP Reputation Analysis | Joined login records to IP reputation data | Evaluate login activity in relation to IP risk |
| Successful Logins from High-Risk IPs | Filtered successful logins associated with high-risk IP classifications | Highlight potentially risky successful authentication |
| Country-Level IP Summary | Aggregated IP reputation records by country | Examine geographical distribution |
| IP Risk Classification Summary | Grouped IP records by risk level | Understand the distribution of classified IP risks |
| Suspicious Activity Flagging | Flagged high-risk IPs or IPs with at least five failed attempts | Establish a preliminary investigation rule |

### 7.4 Employee & Device Summary

| Metric | Analytical Approach | Purpose |
|---|---|---|
| Multiple Devices per Employee | Counted distinct device IDs | Identify employees accessing through multiple devices |
| Device Failed Login Counts | Aggregated failures by device | Identify devices with repeated authentication failures |
| Device Failure Rate | Calculated failed attempts relative to total device attempts | Compare devices fairly |
| Department Failed Login Counts | Grouped failures by department | Identify departments with higher failure volumes |
| Department Failure Rates | Calculated department-level failure percentages | Account for differences in login volumes |
| Employee Failure Rates | Calculated account-level failure percentages for accounts with at least five attempts | Identify accounts with comparatively high failure proportions |

### 7.5 Security Alert Summary

| Metric | Analytical Approach | Purpose |
|---|---|---|
| Alerts by Severity | Grouped alerts by severity | Support risk prioritization |
| Alerts by Type | Counted alerts by alert type | Identify recurring alert categories |
| Resolved vs. Unresolved Alerts | Grouped by alert status | Monitor alert backlog and resolution |
| High/Critical Unresolved Alerts | Filtered higher-severity open or investigating alerts | Prioritize urgent review |
| Alert Resolution Duration | Calculated minutes and hours using `TIMESTAMPDIFF()` | Evaluate response and resolution time |
| Alerts by Department | Joined alerts with login and employee data | Explore department-level alert distribution |
| Alerts Associated with Risk Indicators | Combined alert, employee, and IP reputation information | Support risk-based investigation |

### 7.6 Trend & Comparative Analysis

| Metric | SQL Method | Purpose |
|---|---|---|
| Daily Failed Login Activity | Grouped failures by date | Monitor daily authentication patterns |
| Daily Change in Failed Attempts | Used `LAG()` to calculate previous-day differences | Identify increases or decreases |
| Percentage Change | Compared daily failure counts with preceding periods | Measure relative changes |
| Department vs. Company Failure Rate | CTEs and percentage calculations | Benchmark department performance |
| Top Failed Login Days | Reusable view with descending sort and `LIMIT` | Highlight dates with elevated failures |
| Employee Failure Ranking | Window ranking | Prioritize accounts based on failure volume |

---

## 8. Major Findings & Insights

### Evidence Status

The SQL script contains investigative queries for the areas below. However, query outputs were not supplied, so numerical findings cannot be confirmed from the project files alone.

| Finding Category | Insight the Analysis Is Designed to Reveal | Evidence Required to Confirm |
|---|---|---|
| Authentication Trends | Whether failed login activity is concentrated on particular days or hours | Failed-login counts by weekday and hour |
| High-Failure Accounts | Which employee accounts experience the greatest number of failed attempts | Employee ranking table |
| Login Sequence Patterns | Whether repeated failed attempts are followed by a successful login | Chronological login sequence output |
| IP Address Risk | Whether high-risk IP addresses are associated with successful authentication | IP reputation and successful login records |
| Departmental Risk | Which departments have the highest failure rates relative to login volume | Department failure-rate comparison |
| Device Risk | Which devices experience disproportionately high failure activity | Device failure-rate results |
| Security Alert Prioritization | Whether high-severity alerts remain unresolved | Alert severity and status summary |
| Security Response | How long alerts take to resolve | Resolution duration results |
| Activity Spikes | Whether failed login activity rises noticeably between consecutive days | Daily comparison and percentage-change output |

### Interpretation

These analytical outputs can support identification of authentication anomalies, unusual access behavior, possible risk exposure, and operational weaknesses in security alert management.

Any unusual pattern should be treated as an indicator for further investigation—not as proof of a confirmed security breach.

---

## 9. Reusable Security Reporting

The project created a SQL view named:

`daily_security_summary`

The view aggregates login activity by date and provides:

| Summary Column | Description |
|---|---|
| `activity_date` | Date of login activity |
| `total_login_attempts` | Total login events recorded for the date |
| `failed_login_attempts` | Number of failed login events |
| `successfull_login_attempts` | Number of successful login events |

This reusable summary supports:

- Daily login monitoring.
- Tracking successful and failed authentication trends.
- Identifying dates with the highest failed-login volumes.
- Producing a recurring security activity report.
- Supporting management-level monitoring without repeatedly rebuilding the same aggregation.

Example use cases included querying the view by activity date or retrieving the dates with the highest failed login counts.

---

## 10. Investigation Rule for Potentially Suspicious Activity

The project implemented a preliminary IP-based flagging approach using the following conditions:

| Flagging Condition | Reason |
|---|---|
| IP address classified as `High Risk` | Reputation data indicates elevated risk |
| IP address associated with five or more failed login attempts | Repeated authentication failures may warrant review |

IP addresses meeting either condition were selected for further investigation.

This rule is intended as an initial screening mechanism. It does not independently confirm malicious activity, and its thresholds should be validated against business context, legitimate usage patterns, and the available data.

---

## 11. Business Recommendations

The following recommendations are proposed based on the analytical areas investigated. They should be prioritized and validated against actual query findings before being presented as evidence-driven operational actions.

| Recommendation | Business Rationale | Supporting Analysis |
|---|---|---|
| Review accounts with repeated failed login attempts | Repeated authentication failures may indicate account misuse, forgotten credentials, or attempted unauthorized access | Employee failed-login ranking and login sequence analysis |
| Investigate successful logins from high-risk IP addresses | A successful authentication from a risky source may require verification | IP reputation investigation |
| Prioritize unresolved high-severity alerts | High-severity unresolved alerts may represent risks requiring timely attention | Alert severity and resolution status analysis |
| Review departments with elevated failure rates | Higher failure rates may indicate concentrated issues or different operational patterns | Departmental failure-rate comparison |
| Investigate devices with unusual failure patterns | Device-specific anomalies may help identify access problems or potential misuse | Device failure counts and rates |
| Monitor failed login activity regularly | Ongoing trend analysis can help detect changes in authentication patterns | Daily security summary and trend analysis |
| Improve security alert response monitoring | Resolution-time analysis can help evaluate operational response performance | Alert resolution duration |

---

## 12. Data Quality & Technical Considerations

During review of the SQL scripts, the following issues should be addressed before final execution and publication of the results:

| Issue Identified | Potential Impact | Recommended Correction |
|---|---|---|
| `login_hour` is updated before the column is added | The script may fail at execution | Add the column before updating it, or calculate the hour directly in the query |
| Multiple database names are used (`internship`, `northstar_services`, `cybersecur_investigation`) | Queries may run against inconsistent schemas or databases | Standardize the database name and execution workflow |
| Inconsistent login column naming (`login_id` and `log_id`) | Queries may fail if the actual schema uses only one identifier | Confirm the schema and standardize the column references |
| Inconsistent alert status naming (`alert_status` and `resolution_status`) | Alert queries may fail or produce inconsistent outputs | Confirm and standardize the actual column name |
| Company failure-rate calculation uses `' Failed'` with a leading space | Failed attempts may not be counted correctly | Remove the leading space and validate status values |
| Department alert join appears incomplete | Department-level alert counts may be inaccurate or produce unintended joins | Complete the join condition using the appropriate employee identifier |
| Alert severity case logic uses inconsistent capitalization | Priority ordering may not work consistently | Standardize severity values and case handling |
| Different scripts reference different employee and alert field structures | SQL execution may fail across database versions | Validate actual schemas and use consistent field names |
| No result exports are included | Numerical findings cannot be independently verified from the submitted script | Export key result tables or include screenshots/data summaries |

These issues are important because accurate analysis depends on consistent schemas, correct joins, and validated calculations.

---

## 13. Project Limitations

- The dataset represents a fictional business scenario.
- The SQL scripts provide analytical queries but not complete verified output tables.
- IP reputation information may not be sufficient to independently establish malicious intent.
- Unusual login behavior does not necessarily indicate a compromised account.
- After-hours access depends on the assumed working-hours definition.
- Multiple-device access may be normal employee behavior.
- Alert resolution analysis depends on valid alert and resolution timestamps.
- The suspicious activity threshold of five failed attempts is a preliminary analytical rule, not a validated security policy.
- Data quality and schema inconsistencies may affect some query results until corrected.

---

## 14. Conclusion

This project demonstrates how SQL can be used to investigate a practical cybersecurity-related business problem by transforming raw relational data into structured analytical outputs.

Through login activity analysis, IP reputation investigation, employee and device comparisons, security alert monitoring, ranking, trend analysis, and reusable reporting views, the project establishes a framework for identifying patterns that may warrant further attention.

The key contribution is the application of SQL to connect multiple datasets, measure security activity, compare risk indicators, and support informed investigation and management decision-making.

**Skills demonstrated:** SQL querying, data aggregation, relational joins, CTEs, window functions, ranking, conditional calculations, date/time analysis, data quality validation, trend analysis, reusable views, and business-focused reporting.

---

## 15. Project Skills & Technologies

| Category | Skills |
|---|---|
| Database | MySQL |
| Querying | SQL |
| Data Analysis | Aggregation, filtering, grouping, ranking |
| Data Transformation | Conditional logic, CTEs, calculated metrics |
| Advanced SQL | Window functions, `LAG()`, `DENSE_RANK()` |
| Relational Analysis | Multi-table joins |
| Time-Series Analysis | Daily comparisons, percentage changes, temporal patterns |
| Reporting | Summary tables, reusable views, business recommendations |
| Analytical Domain | Cybersecurity log analysis and risk investigation |

---

**Project Type:** SQL Data Analytics & Cybersecurity Investigation  
**Organization:** Northstar Services (Fictional Case Study)  
**Database:** MySQL  
**Duration:** 3 Weeks  
**Project Group:** Group A – Tech Studio Academy

