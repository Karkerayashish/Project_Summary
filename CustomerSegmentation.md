# Customer Segmentation

---
# **1. Introduction**
---

Segmenting customers is the **process** of **dividing** up mass **consumers** into **groups** with **similar** **needs** and **wants**. It can **help** **companies** to **focus** on **marketing** efforts, so that **customer** **satisfaction** and **overall** **profit** could be achieved at higher rates. **Segmentation** **exists** to **mitigate** the **inevitable** **problems** that evolve from a **"One size fits all"** approach. Best in class **suppliers** **develops** **different** types of **segmentation** to **understand** how to **create**, **position**, and **communicate** the value of their offering to **address** the different **needs** required in different customer segments.

<center><img src = "https://github.com/Karkerayashish/Customer_Segmentation/blob/master/Customer%20Segmentation%201.jpg"></center>

Many **companies** **adopts** **different** **segmentation** **schemes**, that is often **develop** **best** **but** **static** (snapshot of consumer's preferences at the moment). Market **trends** **evolve** over time. **It** may **grow**, **decline** or **disappear** **within** certain **time** period due to number of **reasons** like **demographics trend**, **technological** **advancement**, **economic** **cycles** etc.

<a id = Section2></a>

---
# **2. Problem Statement**
---
At some point, it becomes **impossible** to **focus** on an **individual customer** and **sometimes** the **communication** between customers **become** **complex**. We **need** **a way** out to **understand** our **customers** in **structured** and **shared manner**.

<center><img src="https://github.com/Karkerayashish/Customer_Segmentation/blob/master/Customer%20Segmentation%202.png"></center>

**<h3>Scenario:</h3>**

**Knack Grant** is a UK based non-store **online retail company** started in 2009. The company mainly **sells** unique **all-occasion gift-ware**. Many customers of the company are wholesalers. The **company** is **growing** at **rapid speed**. At the **same time** they are **unable** to **catch up** the **customer expectation** and **maintain healthy relationship** i.e failing in Customer Relationship Management(CRM).

In order **to tackle this problem**, they **hired a team of data scientists**. They **need** an **automated solution** to **identify** the **customers expectations** and the **future trends** so that they can **engage** with customers in **more structured and shared manner** leading their company to future endavours.

**Note:** 
- This **problem** is a type of **unsupervised learning**, i.e. there is no target present in our data. 

- We will **clusters customers based on their behavior**.

- It will **give** us an **approximation** about the **customer purchasing behavior** **leading** to **better marketing**.

---
# **3. Data Acquisition & Wrangling**
---

- This data set is based on online transactions occurring between 01/12/2017 and 09/12/2019 and is accessible [here!](https://storage.googleapis.com/retail-analytics-data/OnlineRetailV3.csv) 

| Records | Features |
| :-- | :-- | 
| 1067371 | 8 |

|Id|Features|Description|
| :-- | :-- | :-- |
|01|**Invoice**|Invoice number. A 6-digit integral number uniquely assigned to each transaction. If this code starts with the letter 'c', it indicates a cancellation.|
|02|**StockCode**|Product item code. A 5-digit integral number along with letters uniquely assigned to each distinct product.|
|03|**Description**|Product item name.|
|04|**Quantity**|The quantities of each product item per transaction. Some values are negative due error while tracking data under process.|
|05|**InvoiceDate**|Invice date and time. The day and time when a transaction was generated.|
|06|**Price**|Product price per unit in sterling (&pound;).|
|07|**Customer ID**|Customer number. A 5-digit integral number uniquely assigned to each customer.|
|08|**Country**|Country name. The name of the country where a customer resides.|

---
# **4. Data Pre-Processing**
---
- In this section, we will perform the below steps to ensure we have clean data.

  - Identification & Handling of Missing Data

  - Null Data Identification & Handling

  - Zero Data Identification & Handling

  - Identification & Handling of Redundant Data

  - Identification & Handling of Inconsistent Data Types

---
# **5. Exploratory Data Analysis**

 <h4>We will try to answer the below questions using EDA.</h4>

*Question 1: What is the ordered quantity of product items per day by the customer?*

*Question 2: What is the total sales of product items per day by the customer?*

*Question 3: Which are the top 10 product that were sold at high quantity to the customer?*

*Question 4: Which are the top 10 product items that were sold at low quantity to the customer?*

*Question 5: What is the total amount that was spend by per country?*

This **concludes** our Exploratory Data Analysis.

---
# **6. Customer Segmentation Techniques**

- In this section we will explore two techniques of clustering customer i.e. using K-Means and RFM(Recency Frequency Monetary).
---

 **Segmentation using K-Means**

- We will be **segmenting** **customers** **based** **on** their **behaviour** i.e the **quantity ordered** and **total amount** on that product.

- **Firstly**, we will **run** **K-means** at **default setting**. Then we will **tune** it over **multiple** **K values**, **finding optimal K**.

- But **before** that we will **normalize two features** that are important for clustering i.e. **Quantity and TotalSpend**.

**Hyperparameter Tuning: Finding Optimal K**

- We **will** **iterate** our model **over** **some** **iterations**, finding optimal K value for clustering.

- We **check** **inertia**, defined as the mean squared distance between each instance and its closest centroid. Logically, as per the definition **lower** the **inertia** **better** the **model**.

- We will **use** **Elbow** **rule** in order to **find** the **optimal** **number** of **clusters**.

- With **Elbow** **rule**, we can see when **K = 5**, there is **significant** **drop** in **inertia**.

- So **K = 5 is optimal** for our **solution**.

**Final Model**

- Having identified the charactersitics of each cluster, we can roll out targeted advertising, promotion offers, etc.**

## **7. Segmentation using RFM**

- RFM stands for **Recency**, **Frequency** and **Monetary**.
  - **RECENCY (R):** Days since last purchase. If score value is high it signifies that customer recently visited the shop.

  - **FREQUENCY (F):** Total number of purchases. If score value is high it signifies that customer buying frequency is high.

  - **MONETARY (M):** Total money customer spent. If score value is high it signifies that customer spending habit is high.

- It is a very **old technique** to **segment** the **customers** and it **works** **very** **well**.

- But it **work** **with** very **recent** **date**, so we **choose** **date** which is **one** **day** **more** than the **data of last day**.

**<h3>Working:</h3>**
- Firstly, we will calculate the RFM metrics for each customer.

|#|Customer|Recency|Frequency|Monetary|
| :-- | :-- | :-- | :-- | :-- |
|01|A|53 days|3 transactions|&pound;230|
|02|B|120 days|10 transactions|&pound;900|
|03|C|10 days|8 transactions|&pound;200|

- Secondly, we will add segment numbers to RFM table.

|#|Customer|Recency|Frequency|Monetary|R|F|M|
| :-- | :-- | :-- | :-- | :-- | :-- | :-- | :--|
|01|A|53 days|3 transactions|&pound;230|2|2|2
|02|B|120 days|10 transactions|&pound;900|1|1|2|
|03|C|10 days|8 transactions|&pound;200|3|3|3|

- Finally, Sort according to the RFM scores from the best customers (score 444).

|#|Segment|RFM|Description|Marketing|
| :-- | :-- | :-- | :-- | :-- |
|01|Best Customers|444|Bought most recently and most often, and spend the most|No price incentives, new products and loyalty programs.|
|02|Loyal Customers|X4X|Buys most frequently|Use R and F to further segment.|
|03|Big Spenders|XX4|Spends the most|Market your most expensive products.|
|04|Almost Lost|244|Haven't purchased for sometime, but purchased frequently and spend the most|Aggresive price incentives.|
|05|Lost Customers|144|Haven't puchased for some time, but purchased frequently and spend the most|Aggressive price incentives.|
|06|Lost Cheap Customers|111|Last purchase long ago, purchased few, and spent little.|Don't spend too much trying to re-acquire.|

**We can match respective customers with above table to identify important customers.**

|#|Customer ID|Recency|Frequency|Monetary|R Value|F Value|M Value|RFM Score
| :-- | :-- | :-- | :-- | :-- | :-- | :-- | :-- | :-- |
|01|12346|326|47|155164.66|2|2|4|224|
|02|12347|3|222|4921.53|4|4|4|444|
|03|12348|76|51|2019.40|3|2|3|323|
|04|12349|19|180|4452.84|4|4|4|444|
|05|12350|311|17|334.40|2|1|1|211|

---
# **8. Conclusion**
---

- We **studied in depth about the data**, its **characteristics** and its **distribution**.

- We **explored various questions** related to the **customer behaviour** and their **residency** and **buying habits**.

- We **adopted two techniques** to **solve** this **business problem**:
  - Using K-Means
  - Using RFM (Recency Frequency Monetary)
  
- **Both** are **used widely**, but **RFM is much better** than automating the whole solution **because** we are **more precise** in **identifying** the **customer** frequent **buying habits** and their **spend**.

