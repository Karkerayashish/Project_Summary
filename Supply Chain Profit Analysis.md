# Supply Chain Profit Analysis

---
# **Introduction**
---
According to <a href = "https://6fefcbb86e61af1b2fc4-c70d8ead6ced550b4d987d7c03fcdd1d.ssl.cf3.rackcdn.com/cms/reports/documents/000/004/072/original/CDP_Supply_Chain_Report_2019.pdf?1550490556">**CDP's Supply Chain Report 2019**</a>, the CDP(Carbon Disclosure Project) **Supply Chain program**
has **continuously grown** its impact **over** the **past
decade**. Since its **launch in 2008 with 14 members**,
the program has **now expanded to** bring together
**115 major** purchasing **organizations around** the
**world**, collectively **representing** **US$3.3 trillion** in
**procurement** **spend**. 

The **lesson** from a decade of the CDP Supply Chain
program **is** that large **public and private sector**
organizations really **can lead effective change**
**through** using **their** substantial **procurement spend** as
a powerful lever for action. **If others** can **follow** their
example, and **suppliers continue to cascade good
practices** and commitments further **down the supply
chain**, **this** can **play** a **huge role in the rapid transition**
**to** a **sustainable, low carbon economy**.

<center><img src = "https://raw.githubusercontent.com/Karkerayashish/Supply_Chain_Profit_Analysis/master/Supply%20Chain%20Management%201.png"></center>

So in **summary**, there is **there is direct impact on environment** in supply chain program. Most **companies** begin with the best **intentions** to **achieve successful** and **sustainable supply chain cost** management, but **somehow** seem to **lose** **momentum**, only to **see costs increase** against in **short order**. The **supply chain process** should be **handled** in such a way that there is **minimum impact** on **environment** while **covering maximum profit**. 

**<h4>Note:</h4>** In this case study we will be **ignoring** the **study of environmental factors** because **most** of the **companies don't disclose** their **reports** on environmental impacts and only **focusing** on the **profit accquirement**.

---
# **Problem Statement**
---

Supply Chain **initiates** from gathering **raw materials**, **supplying** raw materials by supplier to the **manufacturing**, **delivering** to **retailers** by the **distributer**. Finally these products are **consumed** by the **consumer**. With the **increase** in **demand** this **process** **repeats** over again.

<center><img src = "https://raw.githubusercontent.com/Karkerayashish/Supply_Chain_Profit_Analysis/master/Supply-Chain-Example.png"></center>

**<h3>Scenario:</h3>**

**DataCo** an **IT** service management **company**, **used** this **data** to **analyse** the **supply chain** in **areas** of **important** registered **activities** which includes **Provisioning** , **Production** , **Sales** and **Commercial Distribution**. But due to their **traditional processing** methodolgy, they are **unable** to **capture** the **true picture** of their data. They **want** to **identify growth opportunities** related to a given industry within a region. 

They **hired** a **team** of **data scientists** to **analyse and build an automated solution** which can **help** in **identifying key patterns** out of their data **leading growth** of their **company**.

**Note:** Here we will be involved only between Retailer, Consumer & Supplier.


| Target Feature | Potential Values |
| :-- | :-- |
|**Benefit per order**|Range: [ -4274.97, 911.7 ]|

---
# **Data Acquisition & Description**
---

This data set is based on supply chain management provided by DataCo Global and is accessible <a href="https://storage.googleapis.com/retail-analytics-data/DataCoSupplyChainDataset.csv">**here**</a>.


| Records | Features |
| :-- | :-- |
| 180519 | 53 |

|Id|Features|Description|
| :-- | :-- | :-- |
|01|**Type**|Type of tranasaction made.|
|02|**Days for shipping (real)**|Actual shipping days of the purchased product.|
|03|**Days for shipment (scheduled)**|Days of scheduled delivery of the purchased product.|
|04|**Benefit per order**|Earnings per order placed.|
|05|**Sales per customer**|Total sales made per customer. Generally gives you an idea about how much a customer is spening.|
|06|**Delivery Status**|Delivery status of orders: [Advance shipping , Late delivery , Shipping canceled , Shipping on time].|
|07|**Late_delivery_risk**|Categorical variable that indicates if sending is late (1), it is not late (0).|
|08|**Category Id**|Product category code.|
|09|**Category Name**|Description of the product category.|
|10|**Customer City**|City where the customer made the purchase.|
|11|**Customer Country**|Country where the customer made the purchase.
|12|**Customer Email**|Customer's email.|
|13|**Customer Fname**|Customer's first name.|
|14|**Customer Id**|Customer unique ID.|
|15|**Customer Lname**|Customer's last name.|
|16|**Customer Password**|Masked customer key.|
|17|**Customer Segment**|Types of Customers: [Consumer , Corporate , Home Office.]|
|18|**Customer State**|State to which the store where the purchase is registered belongs.|
|19|**Customer Street**|Street to which the store where the purchase is registered belongs.|
|20|**Customer Zipcode**|Customer zipcode.|
|21|**Department Id**|Department code of store.|
|22|**Department Name**|Department name of store.|
|23|**Latitude**|Latitude corresponding to location of store.|
|24|**Longitude**|Longitude corresponding to location of store.|
|25|**Market**|Market to where the order is delivered : Africa , Europe , LATAM , Pacific Asia , USCA.|
|26|**Order City**|Destination city of the order.|
|27|**Order Country**|Destination country of the order.|
|28|**Order Customer Id**|Customer order code.|
|29|**order date (DateOrders)**|Date on which the order is made.|
|30|**Order Id**|Order code.|
|31|**Order Item Cardprod Id**|Product code generated through the RFID reader.|
|32|**Order Item Discount**|Order item discount value.|
|33|**Order Item Discount Rate**|Order item discount percentage.|
|34|**Order Item Id**|Order item code.|
|35|**Order Item Product Price**|Price of products without discount.|
|36|**Order Item Profit Ratio**|Order Item Profit Ratio.|
|37|**Order Item Quantity**|Order Item Quantity.|
|38|**Sales**|Value in sales(selling price).|
|39|**Order Item Total**|Total amount per order.|
|40|**Order Profit Per Order**|Order Profit Per Order.|
|41|**Order Region**|Region of the world where the order is delivered :  [Southeast Asia ,South Asia ,Oceania ,Eastern Asia, West Asia , West of USA , US Center , West Africa, |
|||Central Africa ,North Africa ,Western Europe ,Northern , Caribbean , South America ,East Africa ,Southern Europe , East of USA ,Canada ,Southern Africa ,|
||| Central Asia ,  Europe , Central America, Eastern Europe , South of  USA.]|
|42|**Order State**|State of the region where the order is delivered.|
|43|**Order Status**|Order Status : [COMPLETE , PENDING , CLOSED , PENDING_PAYMENT ,CANCELED , PROCESSING ,SUSPECTED_FRAUD ,ON_HOLD ,PAYMENT_REVIEW.]|
|44|**Order Zipcode**|Zipcode of the region where the order is delivered.|
|45|**Product Card Id**|Product code.|
|46|**Product Category Id**|Product category code.|
|47|**Product Description**|Product Description.|
|48|**Product Image**|Link of visit and purchase of the product (Masked).|
|49|**Product Name**|Product Name.|
|50|**Product Price**|Product Price.|
|51|**Product Status**|Status of the product stock :[If it is 1 not available , 0 the product is available.]|
|52|**Shipping date (DateOrders)**|Exact date and time of shipment.|
|53|**Shipping Mode**|The following shipping modes are presented : [Standard Class , First Class , Second Class , Same Day].|


---
# **Data Pre-Processing**
---

- Identification & Handling of Missing Data
- Zero Data Identification & Handling
- Identification & Handling of Redundant Data
- Identfication & Handling of Redundant Features
- Identification & Handling of Inconsistent Data Types

---
# **Exploratory Data Analysis**
---

- *Question 1: What is the frequency and proportion of scheduled shipment days of order?*
- *Question 2: What is the frequency and proportion of real shipment days of order?*
- *Question 3: Where is the majority of markets located from where product is set to sail?*
- *Question 4: What is the relationship between Customer Segement and Delivery Status?*
- *Question 5: What was the total sales per day with respect to the order date?*
- *Question 6: Which state has placed highest number of orders?*
- *Question 7: What amount of benifit was obtained per state?*
- *Question 8: What was the total amount of products under each category that was ordered and at what value it was sold?*

---
# **Post Data Processing & Feature Selection**
---

- In this part we will **perform encoding over categorical features** and **feed it** to the **Random Forest** because machines can't understand human language.
- But before that we **need** to **drop certain features** like,
  - Customer Fname, Customer Lname, Customer Street, Order City, Order State, Product Image, order date (DateOrders), shipping date (DateOrders).
- We **dropped** these features **because** these **have labels with high cardinality**.
- **Random Forest** will then **identify important features** for our model **using threshold** over the information gain over reduction in impurity.
- And **finally** we will **split** our **data** for the **model development**.


### **Encoding Categorical Features**

- In this part we will **analyze** the **number of labels per feature** and **use Target Encoding**.
- **Reason to use Target encoding:** There are **some features** which are **highly cardinal** in nature.

**Target Encoding:** It is useful when you want to transform catgories based on the probability with respect to target. It has a limitation that they are not generated for the test data. We usually save the target encodings obtained from the training data set and use the same encodings to encode features in the test data set. It can be applied in following cases:
- **For the case of categorical target:**
    - Features are replaced with a blend of posterior probability of the target given particular categorical value and the prior probability of the target over all the training data.

- **For the case of continuous target:** 
    - Features are replaced with a blend of the expected value of the target given particular categorical value and the expected value of the target over all the training data. Example:

<center><img src = "https://raw.githubusercontent.com/insaid2018/Domain_Case_Studies/master/Retail/Images/Target%20Encoding.png"></center>

For example, We want to encode Punjab label, we will perform following:
- Estimate all Punjab Labels in data, here it is 3,
- Take mean of target feature with respect to Punjab labels,
- Replace this value with the label in data as shown in figure above.

**Further Reference:** A complete thesis on how target encoders are helpful can be found under provided <a href = "https://dl.acm.org/doi/10.1145/507533.507538">**link**</a>. You can download pdf present there.


### **Feature Selection using Random Forest**

- Now in **real world**, it is very **rare** that **all** the **features** are **important** while developing the model. 
- So **instead** we **analyze** the **impact** of **input over the target**, either done by performing **statistical** **tests**(Pearson, ANOVA, Chi-Square) or by using **Random Forest**.
- **Random forests** are one the most **popular machine learning algorithms** because they **provide**:
 - **a good predictive performance**,
 - **low overfitting and**
 - **easy interpretability.** 
- This **interpretability** is **derived** from the **importance of each feature** on the tree decision **evaluated** on the **reduction** in **impurity**. 
- In other words, it is **easy to compute** how much **each feature is contributing** to the **decision**.
- **Below** we have **implemented** a function namely, **SelectFromModel** **available** in **Sklearn** which **uses** the **base estimator** to **identify** **important features**.
- The **importance** of feature is **determined** on the **basis** of **threshold**(a measure to calculate feature importance).

### **Data Preparation**

- In the **following section** we will **make a cut** over **Target Feature** i.e Benifit per order **by using** a **categorical feature**.
- We will **create a new categorical feature** that will **benifit us** in **splitting** the **data** in **more controlled way** by using **stratified split**.

---
# **Model Development & Evaluation**
---

- In this section we will **develop two type of models**, 
  - one **using all features** and 
  - second **using only importatnt feature** marked important by Random Forest.
- Then we will **compare the results** obtained from them and make our observation.
- **At the end** we will **tune** our **models if required**.

## **Baseline Models**

- **In this section we will develop modes using all the features and analyze the result obtained from it.**

### **Linear Regression**

**Observation:**

- **RMSE obtained** both on **train data** is **56.5** while on **test it is ~61**.
- **R-Square** is good on **train data** i.e. **71%** while on **test data is 66%**.
- It clearly define that **model** is **overfitting**.


### **Decision Tree Regressor**

**Observation:**

- **RMSE** on **training data** is **0** and **testing data is ~9.6** which is **low** as **compared to Linear Regression**.
- **R-Squared** is also **better 100% on training data while 99% on test data**.
- We can see **better results** but **model** is **overfitting**.

### **Random Forest Regressor**

**Observation:**

- We **didn't obtained any better results than Decision Tree**.
- **Infact it performed worse** than Decision Tree Regressor.
- **RMSE obtained** on **training data is 1.61** and **testing data is ~10.5** which is **more than previous model**.
- There is **no change in obtaining R-Squared** from previous model.
- This **model** **overfits** the data.

## **Essential Features Models**

- In this section **we will be using only important features** that were **marked important by Random Forest**.
- The **important features** we obtained from Random Forest **were Sales per customer and Order Item Profit Ratio**.

### **Linear Regression**

**Observation:**

- We can see that **there isn't any major difference after using only important features**.
- **RMSE obtained** on both **training data and testing data have reduce i.e.  56 and ~61**.
- **R-Squared obtained** on **training data is 70%** while on **testing data it is 66%**
- The **model** still **overfits**.


### **Decision Tree Regressor**

**Observation:**

- **RMSE obtained** on both **training and testing data is 0.2 and 9.27** which is **better than previous model** and **its predecessor**.
- **R-Squared is same** as it's predecessor which is 100% on training and 99% on testing data.
- However there could be chance of **overfitting**.

### **Random Forest Regressor**

**Observation:**

- **RMSE obtained** on both **training data** and **testing data is 1.13 and 8.5** which is **lower than previous models**.
- **R-Squared** obtained is **same as the Decision Tree**.
- **But wait, we can still see some overfitting**
- **To ensure** that we **will use** a **cross validation** strategy over this model.




