# 📋 LA-Checkbook-Insights


## ⚙️ Background
For this project, we used the Los Angeles City Controller's office dataset to analyze urban development and financial trends. Our role was to act as consultants for the Controller's office, putting ourselves in their position to create three key analytical questions that would improve data analysis and management. This project aimed to strengthen our statistical analysis skills and contribute valuable insights to urban planning.

## 📊 Data
This dataset contains 700,145 records and 62 variables, providing a solid foundation for analysis. Its structured format allows for efficient exploration and interpretation, offering detailed insights into how financial resources are allocated within Los Angeles. By examining expenditures, vendors, departments, and fund types, we identified patterns and trends in financial distribution, supporting informed decision-making.
Data source: [Los Angeles City Controller Data](https://controllerdata.lacity.org/api/views/mkec-7zmd/rows.csv?accessType=DOWNLOAD&api_foundry=true)  
You can find the data dictionary and more information about each field [here](https://controllerdata.lacity.org/Purchasing/2020-Checkbook-Data/mkec-7zmd).

## 🏁 Getting Started
To begin, set up the necessary environment to run a Jupyter Notebook, ensuring compatibility with required libraries. Additionally, ensure that PostgreSQL is installed and running. After downloading the data and notebook file, simply execute "Run All" in the Jupyter Notebook to start analysis.

## 🧩 Dimensional Modelling
We designed a schema to logically structure the database, defining tables, columns, and their relationships.
Initially, we used the following schema:

<p align="center">
    <img src="https://github.com/meghananekkanti25/LA-Checkbook-Insights/assets/74411935/4ea86035-7682-4fd8-bd81-d618a4de2865" alt="Image description" width="150" />
</p>

Over time, we developed a dimensional schema like this:
<p align="center">
    <img src="https://github.com/meghananekkanti25/LA-Checkbook-Insights/assets/74411935/e12e24c1-4e02-476a-b9d2-0a75922979f0" width="450" />
</p>

We created the database by defining tables and relationships using SQL functions.
❗️ Ensure that the final fact table (checkbook) retains the same number of records as the original dataset after data cleaning.

## 🌠 Data Analysis and Visualization
Using Pandas and Matplotlib, we created visualizations to help interpret the data and answer our analytical questions effectively.

### 1️⃣. Which vendors have the highest total order amounts? What are the order counts for the top three vendors, and what percentage of total orders does each represent?

#### Top 5 Vendors by Total Order Amount 
These vendors have the highest expenditures:
<br>
<p align="center">
    <img src="https://github.com/meghananekkanti25/LA-Checkbook-Insights/assets/74411935/aab9cae2-a662-42b8-bd26-ef3411756a62" width="700" />
</p>
<br>

1. **Voya Holdings, Inc.**: $344,757,329  
   Voya is a financial services provider offering retirement, investment, and insurance solutions. This spending likely covers pension fund management, employee retirement plans, or other financial services related to government operations.
2. **Southern California Public Power Authority**: $342,719,045  
   SCPPA is a consortium of municipal utilities and an irrigation district. This expenditure likely supports utility services or financial management for public funds, with the Office of the Treasurer overseeing these transactions.
3. **Turner PCL**: $329,937,822  
   Turner PCL is a prominent construction company involved in large-scale infrastructure projects. This spending is likely tied to the development or construction of public works and other major government projects.
4. **Delta Airlines, Inc.**: $226,029,349  
   Delta is a leading airline, and government spending with them likely covers employee travel, transportation for government officials, and other related air travel services.
5. **Southern California Permanente Medical Group**: $214,302,046  
   This medical organization provides healthcare services to government employees or supports public health initiatives, making up a significant portion of the spending in healthcare-related areas.

#### Top 3 Vendors by Order Count
These vendors have the most transactions:
<br>
<p align="center">
    <img src="https://github.com/meghananekkanti25/LA-Checkbook-Insights/assets/74411935/9e331720-966a-4fe1-a27c-1add041589d7" width="700" />
</p>
<br>

1. **Konica Minolta Business Solutions** — 0.05%: 54,975 transactions  
   Konica Minolta is a multinational technology company specializing in business solutions like office printing systems, digital presses, multifunctional products (MFPs), and IT services. They typically provide copiers, laser printers, and related services.
2. **Office Depot Business SVCS Div** — 0.05%: 43,104 transactions  
   Office Depot offers a wide range of office supplies and services. This division serves customers with products such as stationery, furniture, technology equipment, and business services like printing and document services.
3. **Falcon Fuels Inc.** — 0.05%: 20,578 transactions  
   Falcon Fuels specializes in providing fuel products, including gasoline, diesel, and other types of fuel for vehicles, equipment, and heating purposes.

<br>

### 2️⃣. Which departments have the highest spending, and how is the budget distributed among their activities?
We performed a Pareto analysis on the top 10 spending departments to identify which contributed the most to total expenditure.

<br>
<p align="center">
    <img src="https://github.com/meghananekkanti25/LA-Checkbook-Insights/assets/74411935/944effeb-df02-407a-aa66-8533876bd0a9" width="700" />
</p>
<br>

**The concentration of spending**  
The top three departments by spending are "WATER AND POWER," "AIRPORTS," and "NON_DEPARTMENTAL." Together, they account for a significant portion (70.40%) of the total spending. The expenditure distribution among these departments likely reflects the priorities and policy decisions of the governing body. Considerable spending in "WATER AND POWER" and "AIRPORTS" may indicate extensive infrastructure, maintenance, or operational costs associated with these sectors.

**The threshold for Majority of spending**  
It takes only five departments ("WATER AND POWER," "AIRPORTS," "NON_DEPARTMENTAL," "GENERAL SERVICES," and "TRANSPORTATION") to exceed 77% of total spending. The "HOUSING AND COMMUNITY INVESTMENT DEPARTMENT" pushes the cumulative spending just past the 80% threshold. Approximately 80% of the expenditure is concentrated within the top 6 departments. This follows the Pareto principle, which suggests that a few departments are responsible for a large proportion of the effects (spending).

While smaller departments like "POLICE" have a lower individual percentage, their essential services mean that budget adjustments must carefully consider avoiding compromising critical public services. This spending distribution indicates that strategic financial management efforts should focus on the top spending departments, but it is also important to ensure that smaller departments operate efficiently and are not overlooked simply due to their smaller share of the spending.

--- 

**Departmental Activity Analysis Using Pareto Analysis**  
We analyzed activities within specific departments—'WATER AND POWER,' 'AIRPORTS,' 'NON DEPARTMENTAL,' 'GENERAL SERVICES,' 'TRANSPORTATION,' and 'HOUSING AND COMMUNITY INVESTMENT DEPARTMENT'—using Pareto analysis to focus on those contributing most significantly. By extracting financial data from the checkbook table, and joining it with department and activity tables, we were able to calculate the total spending on each activity. The results show spending by activity as a percentage of departmental totals, which guides spending priorities and provides valuable insights into departmental financial management.

<br>
<p align="center">
    <img src="https://github.com/meghananekkanti25/LA-Checkbook-Insights/assets/74411935/dc313a0d-4226-4565-8545-beee0447529c" width="700" />
</p>
<br>

The government classifies activities within each department into main activities and financial services. Financial Services activities are centered on supporting operations through financial management and planning. Main activities account for over 97% of each department's budget allocation.

1. **Airports** categorize their activities into 'TRANSPORTATION, COMMERCE AND/OR ENTERPRISE' and 'FINANCIAL SERVICES,' with 99.94% of the total spending directed towards 'TRANSPORTATION, COMMERCE AND/OR ENTERPRISE.'
2. **General Services** categorizes activities into 'GENERAL GOVERNMENT,' 'FINANCIAL SERVICES,' and 'PROTECTION OF PERSONS AND PROPERTY,' allocating 96.65% of the budget to 'GENERAL GOVERNMENT' and 3.35% to 'FINANCIAL SERVICES.'
3. The **Housing and Community Investment Department** predominantly focuses its expenditure on community development.
4. Both the **Transportation** and **Water** departments allocate their entire budgets to 'TRANSPORTATION, COMMERCE, and ENTERPRISE.'

<br>

### 3️⃣. Which departments use most of the Special Revenue and Capital Projects funds?

#### Special Revenue funds
These funds are allocated for specific projects and ensure transparency in spending.
<br>
<p align="center">
    <img src="https://github.com/meghananekkanti25/LA-Checkbook-Insights/assets/74411935/efc18cbf-ae5c-4f68-92f4-c003f267d64b" width="700" />
</p>
<br>

1. **Top Departments by Special Revenue**: The "NON_DEPARTMENTAL," "TRANSPORTATION," and "HOUSING AND COMMUNITY INVESTMENT DEPARTMENT" are the top three entities in terms of the total dollar amount from special revenue funds.
2. **Cumulative Impact**: Spending from these funds will have a noticeable cumulative impact as we move down the list. The "TRANSPORTATION" department alone accounts for nearly 45% of the special revenue fund spending, and along with "NON_DEPARTMENTAL," they comprise over 70% of the total special revenue fund expenditure.
3. **Efficiency and Efficacy**: The efficient use of special revenue funds should be regularly reviewed. This is not just a formality, but a crucial step to ensure that these targeted funds are making the intended impact. Departments with lower allocations may need to be audited for efficiency or to argue a case for increased funding, highlighting the importance of your role in oversight.

#### Capital Projects funds
These funds finance infrastructure and construction projects.
<br>
<p align="center">
    <img src="https://github.com/meghananekkanti25/LA-Checkbook-Insights/assets/74411935/6a238952-ff50-4dd8-bf71-b1ec47574e61" width="700" />
</p>
<br>

1. **High-Value Projects**: The "HOUSING AND COMMUNITY INVESTMENT DEPARTMENT" has incurred the highest expenditure on a single project, indicating a significant investment in housing-related initiatives.
2. **Diverse Capital Projects**: Projects span various sectors, from administrative actions (as seen in the "CITY ADMINISTRATIVE OFFICER" department) to housing, public works, park acquisition, and transportation. This diverse range reflects a variety of capital project types, including housing investments, park acquisitions, and transportation infrastructure.
3. **Investment in Public Services**: There is a clear emphasis on investing in community services and infrastructure, such as parks and transportation, aimed at enhancing residents' quality of life. The substantial expenditure in the "HOUSING AND COMMUNITY INVESTMENT DEPARTMENT" underscores a dedicated effort toward housing development, potentially addressing housing affordability or homelessness. The investment in "BIKE SHARE PHASE III" within the "TRANSPORTATION" department highlights a commitment to sustainable and alternative transportation options.


## 🔖 Takeaways and Next Steps
- **Top Vendors and Expenditures**: Large expenditures are driven by major vendors such as Voya Holdings and Turner PCL, who primarily serve the financial services, utilities, and infrastructure sectors.
  
- **Operational Suppliers**: Vendors like Konica Minolta and Office Depot, with the highest transaction volumes, provide essential operational supplies.
  
- **High-Spending Departments**: Departments like 'WATER AND POWER' and 'AIRPORTS' account for significant portions of the budget, necessitating targeted financial oversight.
  
- **Budget Prioritization**: Departmental budget allocations focus on key operational areas, ensuring that resources are allocated efficiently to support essential functions.
  
- **Special Revenue and Capital Projects**: Significant funds from Special Revenue and Capital Projects are directed towards 'TRANSPORTATION' and 'HOUSING AND COMMUNITY INVESTMENT,' reflecting a strong focus on infrastructure development and community services.

Next Steps:
1. Conduct a detailed analysis of spending subcategories to identify areas for potential cost savings.
2. Review historical data to identify trends and better inform future budgeting decisions.
3. Perform variance analysis by comparing budgeted vs. actual spending to assess financial performance.
4. Execute cost-benefit analyses to optimize fund utilization and ensure maximum value for each dollar spent.




