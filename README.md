# Health-care-analytics-Dashboard
Healthcare Analytic Dashboard
Dashboard link: https://app.powerbi.com/links/DALi1Crgfw?ctid=7e2137dd-6ef9-46eb-974e-5086fd7cdd20&pbi_source=linkShare
Project Objective
The objective of this project is to design and develop a comprehensive healthcare dashboard that enables healthcare providers, administrators, and decision-makers to effectively monitor, analyze, and manage key health metrics and operational data. This dashboard aims to enhance patient care, streamline operations, and support data-driven decision-making through the following specific goals
Import data to Power BI
1. Prepare csv file
2. Import CSV file to Power BI
3. Data cleaning
4. Data Processing
DAX Queries Total patient Total_patient = count('Patients Dataset'[patient_id])
Administrative Staff % Administrative_staff = divide( countrows( FILTER('Patients Dataset','Patients Dataset'[patient_admin_flag]=True())) ,[Total_patient]) Non Administrative staff % Non-Administrative_staff = divide( countrows( FILTER('Patients Dataset','Patients Dataset'[patient_admin_flag]=False())) ,[Total_patient]) Referred Patient % of referred patient = ( var _refer= CALCULATE([Total_patient],'Patients Dataset'[department_referral]<>"None") return
divide(_refer,[Total_patient])) Walk in patient % of unreferred patient = ( var _unrefer= CALCULATE([Total_patient],'Patients Dataset'[department_referral]="None") return divide(_unrefer,[Total_patient])) Percent of satisfaction score % of_satisfaction score = var _sat_score=CALCULATE( [Total_patient],'Patients Dataset'[patient_sat_score]<>BLANK()) return divide(_sat_score,[Total_patient]) Percent of No Satisfaction Score % of no_satisfaction_score = divide( COUNTROWS( FILTER('Patients Dataset','Patients Dataset'[patient_sat_score]=BLANK())), [Total_patient]) Average Satisfaction Score Average_satisfaction_score = calculate( average('Patients Dataset'[patient_sat_score]), 'Patients Dataset'[patient_sat_score]<>BLANK()) Average Wait time Average_Wait_time = average('Patients Dataset'[patient_waittime]) Parameter table Parameter = { ("Avg. satisfaction_score", NAMEOF('Measure_table'[Average_satisfaction_score]), 0), ("Avg. Wait_time", NAMEOF('Measure_table'[Average_Wait_time]), 1) }
Project Insight
Overview
 Total Patients: 9216
 50.04% of patients are attended by administrative staff.
 58.59% are walk-in patients, while 41.41% are referred.
 77.86% of clinic patients are adults.
 Average satisfaction score: 5.47
 Approximately 75% of patients did not provide a satisfaction score.
 Patient flow is higher on weekdays than weekends.
 Average satisfaction score and average wait time are not correlated with patient race.
Healthcare Dashboard Using Power BI
1. Average Wait Time: Analyze the typical wait time for patients before their appointments, identifying patterns and trends to evaluate the efficiency of the healthcare system.
2. Patient Satisfaction: Assess the average satisfaction scores provided by patients, understanding the factors that contribute to a positive patient experience and ways to improve it.
3. Total Patient Visits Monthly: Review the monthly patient visit trends to comprehend the dynamics of healthcare demand over time.
4. Administrative vs. Non-Administrative Appointments: Differentiate between appointments involving administrative processes and those that do not, exploring their impact on wait times and patient satisfaction.
5. Referrals and Walk-In Patients: Investigate the balance between referred patients and walk-in patients, and its effect on the overall patient experience.
6. Patient Visits by Age Group and Race: Analyze the distribution of patient visits across various age groups and races, gaining insights into the diverse healthcare needs and preferences.
.
