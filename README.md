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

<img src="https://github.com/meghananekkanti25/LA-Checkbook-Insights/assets/74411935/586eb164-127c-4d82-af22-a329bf220209" alt="Image description" width="150" />

We will eventually build a dimensional schema like this:

<img src="https://github.com/meghananekkanti25/LA-Checkbook-Insights/assets/74411935/e680611f-121a-4cd5-b4f3-298cad47b24d" width="450" />

We then create the database by define the tables and their relationships using sql functions. 

❗️Make sure that the number of records of the final fact (checkbook in this case) match the number of records in the original data after data cleaning.


## 🌠 Data Analysis and Visualization
Using Pandas and Matplotlib, we created visualizations to better understand the data to explain and effectively answer the questions.

### 1️⃣. Which vendors have the highest total order dollar amoun? What are the order counts for the top three vendors, and what percentage of the dataset's total orders does each vendor represent?

#### Top 5 vendors based on total order dollar amount 
These are vendors with highest expenditure.

<img src="https://github.com/meghananekkanti25/LA-Checkbook-Insights/assets/74411935/4942c621-e8ed-41ef-8983-8f1ed775b8c2" width="700" />
  
1. Voya Holdings, Inc.: $ 344,757,329 VOYA is a financial services company that provides retirement, investment, and insurance products. In a government context, this expenditure could be related to pension fund management, employee retirement plans, or other financial services.
2. Southern California Public Power Authority: $ 342,719,045 SCPPA is a joint powers authority consisting of municipal utilities and an irrigation district. The Office of the Treasurer likely handles financial transactions for a city or state. Expenditures here may relate to utility services or financial management services for public funds.
3. Turner PCL: $ 329,937,822 These are large construction companies that often form joint ventures for large-scale construction projects. Expenditures with this vendor would likely be for construction or major infrastructure projects.
4. Delta Airlines Inc.: $ 226,029,349 Delta is a major airline. Government expenditures with Delta could be for employee travel, transportation of officials, or other travel-related services.
5. Southern California Permanente Medical Group: $ 214,302,046 This is a medical organization that provides healthcare services. Expenditures with this group would likely be related to healthcare services for government employees or public health initiatives.


#### Top 3 Vendors based on order counts
These are vendors with the highest number of transactions.

<img src="https://github.com/meghananekkanti25/LA-Checkbook-Insights/assets/74411935/9e331720-966a-4fe1-a27c-1add041589d7" width="700" />

1. Konica Minolta Business Solutions - 0.05%: 54,975 transactions Konica Minolta is a multinational technology company that specializes in business solutions, including office printing systems, digital presses, multifunctional products (MFPs), and IT services. They typically provide copiers, laser printers, and related services.
2. Office Depot Business SVCS Div - 0.05%: 43,104 transactions Office Depot provides a broad range of office supplies and services. This division would cater to business customers with products like stationery, furniture, technology equipment, and business services (such as printing and document services).
3. Falcon Fuels INC. - 0.05%: 20,578 transactions This company likely specializes in the provision of fuel products. They could be supplying gasoline, diesel, or other types of fuel for vehicles, equipment, and heating purposes.



