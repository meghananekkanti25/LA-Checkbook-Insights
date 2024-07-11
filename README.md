# 📋 LA-Checkbook-Insights

## ⚙️ Background
For our class project, we are using a dataset from the Los Angeles City Controller's office to gain insights into urban development and financial trends. We had to act as consultants for the Controller's office, put ourselves in their shoes, and create three analytical questions to gain a better understanding of data analysis and management. Our goal is to leverage this project to enhance our skills in statistical analysis and make meaningful contributions to the field of urban planning.


## 📊 Data
This dataset contains 700,145 records and 62 variables, providing a comprehensive foundation for analysis. This organization allows researchers to efficiently explore and interpret data, gaining granular insights into resource allocation within the City of Los Angeles. By examining expenditures, vendors, departments, and fund types, users can uncover valuable patterns and trends in financial resource distribution, facilitating informed decision-making processes.

Data source:

You can find the data here: https://controllerdata.lacity.org/api/views/mkec-7zmd/rows.csv?accessType=DOWNLOAD&api_foundry=true.

You can find the data dictionary and more information about each field here: https://controllerdata.lacity.org/Purchasing/2020-Checkbook-Data/mkec-7zmd.


## 🏁 Getting Started
Start by setting up the appropriate environment to run a Jupyter Notebook file to ensure you have the proper versions of the required libraries. Once that is done, ensure you have PostgreSQL installed and running. You can then download the data and .ipynb file and hit "Run All" on the notebook.


## 🧩 Dimensional Modelling
We want to create a schema to get a logical understanding and structure for the database by defining tables, columns, and their relationships.

First we start from this schema:

<p align="center">
    <img src="https://github.com/meghananekkanti25/LA-Checkbook-Insights/assets/74411935/4ea86035-7682-4fd8-bd81-d618a4de2865" alt="Image description" width="150" />
</p>

We will eventually build a dimensional schema like this:

<p align="center">
    <img src="https://github.com/meghananekkanti25/LA-Checkbook-Insights/assets/74411935/e12e24c1-4e02-476a-b9d2-0a75922979f0" width="450" />
</p>

We then create the database by define the tables and their relationships using sql functions. 

❗️Make sure that the number of records of the final fact (checkbook in this case) match the number of records in the original data after data cleaning.


## 🌠 Data Analysis and Visualization
Using Pandas and Matplotlib, we created visualizations to better understand the data to explain and effectively answer the questions.

### 1️⃣. Which vendors have the highest total order dollar amoun? What are the order counts for the top three vendors, and what percentage of the dataset's total orders does each vendor represent?

#### Top 5 vendors based on total order dollar amount 
These are vendors with highest expenditure.
<br>
<p align="center">
    <img src="https://github.com/meghananekkanti25/LA-Checkbook-Insights/assets/74411935/aab9cae2-a662-42b8-bd26-ef3411756a62" width="700" />
</p>
<br>

1. **Voya Holdings, Inc.**: $ 344,757,329 VOYA is a financial services company that provides retirement, investment, and insurance products. In a government context, this expenditure could be related to pension fund management, employee retirement plans, or other financial services.
2. **Southern California Public Power Authority**: $ 342,719,045 SCPPA is a joint powers authority consisting of municipal utilities and an irrigation district. The Office of the Treasurer likely handles financial transactions for a city or state. Expenditures here may relate to utility services or financial management services for public funds.
3. **Turner PCL**: $ 329,937,822 These are large construction companies that often form joint ventures for large-scale construction projects. Expenditures with this vendor would likely be for construction or major infrastructure projects.
4. Delta Airlines Inc.: $ 226,029,349 Delta is a major airline. Government expenditures with Delta could be for employee travel, transportation of officials, or other travel-related services.
5. Southern California Permanente Medical Group: $ 214,302,046 This is a medical organization that provides healthcare services. Expenditures with this group would likely be related to healthcare services for government employees or public health initiatives.


#### Top 3 Vendors based on order counts
These are vendors with the highest number of transactions.
<br>
<p align="center">
    <img src="https://github.com/meghananekkanti25/LA-Checkbook-Insights/assets/74411935/9e331720-966a-4fe1-a27c-1add041589d7" width="700" />
</p>
<br>

1. **Konica Minolta Business Solutions** - 0.05%: 54,975 transactions Konica Minolta is a multinational technology company that specializes in business solutions, including office printing systems, digital presses, multifunctional products (MFPs), and IT services. They typically provide copiers, laser printers, and related services.
2. **Office Depot Business SVCS Div** - 0.05%: 43,104 transactions Office Depot provides a broad range of office supplies and services. This division would cater to business customers with products like stationery, furniture, technology equipment, and business services (such as printing and document services).
3. **Falcon Fuels INC.** - 0.05%: 20,578 transactions This company likely specializes in the provision of fuel products. They could be supplying gasoline, diesel, or other types of fuel for vehicles, equipment, and heating purposes.

<br>

### 2️⃣. What departments exhibit higher spending, and how is the government budget allocated among various activities within these departments?
We used Pareto analysis on the top 10 departments badsed on their spending in the data to identify and prioritize those contributing to 80% of the financial impact. This approach helps to focus on resources in key departments, aiming to optimize financial management by improving resource allocation and decision-making efficiency.

<br>
<p align="center">
    <img src="https://github.com/meghananekkanti25/LA-Checkbook-Insights/assets/74411935/944effeb-df02-407a-aa66-8533876bd0a9" width="700" />
</p>
<br>

**The concentration of Spending**: The top three departments by spending are "WATER AND POWER," "AIRPORTS," and "NON_DEPARTMENTAL." Together, they account for a significant portion (70.40%) of the total spending. The expenditure distribution among the departments may reflect the priorities and policy decisions of the governing body. Considerable expenditure in "WATER AND POWER" and "AIRPORTS" may reflect extensive infrastructure, maintenance, or operational costs associated with these sectors.

**The threshold for Majority of Spending**: It takes only five departments ("WATER AND POWER," "AIRPORTS," "NON_DEPARTMENTAL," "GENERAL SERVICES," and "TRANSPORTATION") to exceed 77% of total spending, and the "HOUSING AND COMMUNITY INVESTMENT DEPARTMENT" pushes the cumulative spending just past the 80% threshold. Approximately 80% of the expenditure is concentrated only within the top 6 departments. This aligns with the Pareto principle, which suggests that a small number of departments are responsible for a large proportion of the effects (spending).

While smaller departments like "POLICE" have a lower individual percentage, their essential services mean that budget adjustments must carefully consider avoiding compromising critical public services. This spending distribution suggests that strategic financial management efforts should focus on the top spending departments. However, it is also crucial to ensure that smaller departments operate efficiently and that we do not overlook them simply because they have a smaller share of the spending.

--- 

We analyzed activities within specific departments—'WATER AND POWER', 'AIRPORTS', 'NON DEPARTMENTAL', 'GENERAL SERVICES', 'TRANSPORTATION', and 'HOUSING AND COMMUNITY INVESTMENT DEPARTMENT' — using Pareto analysis to focus on those contributing most significantly. Extracting financial data from the checkbook table, joined with department and activity tables, reveals total spending on each activity. Results show spending by activity as a percentage of departmental totals, guiding spending priorities and insights into departmental financial management.

<br>
<p align="center">
    <img src="https://github.com/meghananekkanti25/LA-Checkbook-Insights/assets/74411935/dc313a0d-4226-4565-8545-beee0447529c" width="700" />
</p>
<br>

The government classifies activities under each department into main activities and financial services. Financial Services activities focus on supporting operations through financial management and planning. Main activities account for over 97% of each department's budget allocation.

1. **Airports** categorize their activities into 'TRANSPORTATION, COMMERCE AND/OR ENTERPRISE' and 'FINANCIAL SERVICES,' with 99.94% of total spending directed towards 'TRANSPORTATION, COMMERCE AND/OR ENTERPRISE.'
2. **General Services** categorizes activities into 'GENERAL GOVERNMENT,' 'FINANCIAL SERVICES,' and 'PROTECTION OF PERSONS AND PROPERTY,' allocating 96.65% of the budget to 'GENERAL GOVERNMENT' and 3.35% to 'FINANCIAL SERVICES.'
3. The **Housing and Community Investment Department** primarily focuses its expenditure on community development.
4. Both **Transportation** and **Water** departments allocate their entire budgets to 'TRANSPORTATION, COMMERCE, and ENTERPRISE.'

<br>

### 3️⃣. Which departments use most of the Special Revenue funds and the Capital Projects funds?

#### Special Revenue funds
A special revenue fund is a designated account created by a government to gather funds earmarked for a specific project. These funds offer an additional layer of accountability and transparency, assuring taxpayers that their contributions will be allocated for the intended purpose.

<br>
<p align="center">
    <img src="https://github.com/meghananekkanti25/LA-Checkbook-Insights/assets/74411935/efc18cbf-ae5c-4f68-92f4-c003f267d64b" width="700" />
</p>
<br>

1. **Top Departments by Special Revenue**: The "NON_DEPARTMENTAL," "TRANSPORTATION," and "HOUSING AND COMMUNITY INVESTMENT DEPARTMENT" are the top three entities in terms of the total dollar amount from special revenue funds.
2. **Cumulative Impact**: Spending from these funds will have a noticeable cumulative impact as we move down the list. The "TRANSPORTATION" department alone accounts for nearly 45% of the special revenue fund spending, and along with "NON_DEPARTMENTAL," they comprise over 70% of the total special revenue fund expenditure.
3. **Efficiency and Efficacy**: The efficient use of special revenue funds should be regularly reviewed. This is not just a formality, but a crucial step to ensure that these targeted funds are making the intended impact. Departments with lower allocations may need to be audited for efficiency or to argue a case for increased funding, highlighting the importance of your role in oversight.


#### Capital Projects funds
Capital Projects Funds are used to account for financial resources allocated to the acquisition or construction of capital facilities, including land, improvements to land, buildings, building improvements, and infrastructure. Examples include infrastructure projects such as railways, roads, and dams.

<br>
<p align="center">
    <img src="https://github.com/meghananekkanti25/LA-Checkbook-Insights/assets/74411935/6a238952-ff50-4dd8-bf71-b1ec47574e61" width="700" />
</p>
<br>

1. **High-Value Projects**: The "HOUSING AND COMMUNITY INVESTMENT DEPARTMENT" has incurred the highest expenditure on a single project, indicating a significant investment in housing-related initiatives.
2. **Diverse Capital Projects**: Projects span various sectors, from administrative actions (as seen in the "CITY ADMINISTRATIVE OFFICER" department) to housing, public works, park acquisition, and transportation. This diverse range reflects a variety of capital project types, including housing investments, park acquisitions, and transportation infrastructure.
3. **Investment in Public Services**: There is a clear emphasis on investing in community services and infrastructure, such as parks and transportation, aimed at enhancing residents' quality of life. The substantial expenditure in the "HOUSING AND COMMUNITY INVESTMENT DEPARTMENT" underscores a dedicated effort toward housing development, potentially addressing housing affordability or homelessness. The investment in "BIKE SHARE PHASE III" within the "TRANSPORTATION" department highlights a commitment to sustainable and alternative transportation options.








