# Customer Segmentation & Purchase Prediction Analysis
 
**CustomHub Tiktokshop Customer Segmentation Analysis**  

**Tools Used:**  
**Excel** &nbsp; | &nbsp; **Python pandas** &nbsp; | &nbsp; **K-means Clustering**

### Project Type  
 
- **Data Cleaning**                                   &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  * **Machine Learning**  
- **Exploratory Data Analysis (EDA)**                &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  * **Data Visualization**  
- **Data Preprocessing**  


   


### 👥 Type  
**Stakeholder**  

 


**Project background**

Founded in 2022, CustomHub52 is a California-based TikTok Shop specializing in personalized gifts and seasonal products. The store has experienced rapid growth, with seasonal gift items driving the majority of sales.

In its first year, CustomHub52 leveraged influencer marketing and TikTok ads as key revenue drivers, quickly expanding its customer base. With a data-driven approach, including advanced analytics and targeted campaign strategies, the store surpassed **20,000** customers, establishing itself as a leading brand in the personalized gifting space.

This project focuses on customer segmentation using K-Means clustering to group customers based on demographic attributes such as gender, age, and income to be able to cluster customers by segments. This clustering allows easier targeting and easier to predict of purchasing behaviour. After clustering, Logistic Regression is applied to predict the probability of customer purchases on a new dataset.


****Executive Summary****

I segmented my customers into four distinct clusters. Career-Focused Segment (43% of Customers), Standard Segment (36% of Customers), Fewer-Opportunities Segment (12% of Customers), Well-Off Segment (9% of Customers)  
In terms of revenue contribution:
Career-Focused Segment drives 48% of total revenue, Standard Segment accounts for 25% of total revenue, Fewer-Opportunities Segment contributes 13% of revenue, Well-Off Segment makes up 14% of revenue.

The **juicy part** every segemnt has a favorited product. Career-Focused Segment contribute 36% revenue of product 4  ,  Standard Segment contribute 49% revenue of product 5 ,  Fewer-Opportunities Segment contribute 56% revenue of product 2 , Well-Off Segment contribute 40% revenue of product 5 

 Using my Logistic Regression model, I analyzed the coefficients for each price point and their corresponding products, allowing me to understand what drives purchases and to what extent. I leveraged this information to calculate the Price Elasticity of Demand (PED). The results were particularly insightful—Products 2, 3, and 4 showed a PED of less than -1, indicating they are elastic. This suggests that increasing the price of these products would likely lead to a higher overall revenue, as demand would not drop significantly enough to offset the price increase.
 

**Recommendations**
I recommende trying to change product prices as follows;
Product_1: -20% , Product_2: 5% , Product_3: 20% , Product_4: 10%, Product_5: -10%

Based on the price elasticity of products:
![Screenshot 2025-02-14 101358](https://github.com/user-attachments/assets/1226e91d-ccf3-4422-8ff2-e17f78b1966b)
**Marketing Strategy recommendation:**
Carreer-Focused 

*Increase bidding strategy by 20-40% to maximize ad reach, especially for high-ticket items.

*Adjust pricing by increasing product 3 price by 20% to maximize revenue potential.

*Horizontal scaling efforts on social media by duplicating successful ad sets that target the Product 4.

*Vertical scaling efforts on social media target the Product 3.

*Offer early access or VIP discounts to incentivize high-value purchases.

Standard  

*Horizontal scaling efforts on social media by duplicating ad sets that targets the Standard Segment and Product 5.

*Focus on influencer and affiliate marketing to generate new revenue streams for Product 5.

*Targeted premium email campaigns with product recommendations to insentive higher purchases.

*Increase retargeting efforts for customers who abandoned carts in the Standard Segment, offering them a time-sensitive discount.

Fewer-Opportunities 

*Target Product 2 specifically in new campaigns and ad sets to maximize reach and increase revenue.

*Leverage exclusive email marketing tailored to their ambition and success-driven mindset, promoting high-value items.

*Vertical and horizontal scaling: Run A/B tests to determine which method drives the best ROAS for this group.

*Explore premium products with personalized features such as custom name gifts or luxury options to appeal to their refined tastes.

*Launch E-mail Campaign for limited-edition products to create urgency for purchase.

Well-Off 

*Target Product 5 in new campaigns and ad sets to improve reach and maximize revenue.

*Increase special offer and event E-mail Marketing to boost sales of Products 2, 4, and 5.

*Vertical and horizontal scaling: Run A/B tests on both strategies to determine the most effective method.

*Explore affordable product bundles to increase purchase probability for budget-conscious customers.

*Consider offering loyalty rewards for repeat purchases to build brand affinity and increase LTV.



**Project Deep-Dive**

I began this project with Exploratory Data Analysis (EDA) by examining the data types, columns, and values to identify patterns and correlations. I used key methods such as .info(), .describe(), .corr(), and .head() to gain an initial understanding of the dataset. Next, I proceeded with data preprocessing. Since the dataset contained both categorical and ordinal values, I started by encoding categorical variables such as gender and marital status. I applied Label Encoding, assigning 1 and 0 to categories

My first challenge came across when encoding ordinal data—unlike categorical data, it needed to be enumerated based on its levels rather than arbitrary values. I initially attempted to use OrdinalEncoder, but I quickly realized it automatically assigns values in alphabetical order, which did not align with the logical ranking of my data. To solve this, I conducted further research using Google and AI tools and found a workaround. I created list variable for ordinal features, ensuring they were encoded correctly. Using .unique(), I extracted the distinct values for Education, Occupation, and Settlement Size, manually arranging them in ascending order before applying the encoding.

The next step was standardizing the data to ensure that all features contributed equally to the model. Since the dataset included variables with different scales—age (ranging from 18 to ~76) and income (ranging from hundreds to tens of thousands)—without standardization, the model would weigh income as the most significant factor. To address this, I applied MinMaxScaler, which scales values to a range between 0 and 1, preventing larger values from dominating the clustering process. I also tested StandardScaler, but after comparing both, I found that MinMaxScaler produced similar clustering results while being more interpretable for this dataset.

PCA and Modelling  
I have faced biggest challenge so far for this project as you will see at the diagrams cluster number isn't clear I cannot decide whether I should choose 2,4,5 or 7 because it can be all of them when you use elbow method. To address this challenge first I reduce the dimension from 7 to 4 this allows me to save on computing time and energy and also allows me to see clearly for choosing which of the cluster I should choose. 
K-means Clustering without PCA
![image](https://github.com/user-attachments/assets/10cf0018-f40a-4456-a980-f2e5b7250aef)



K-means Clustering with PCA
![image](https://github.com/user-attachments/assets/3d753b45-0d9c-4e9c-9403-640fd0be43a1)


The visualizations above indicate that there is no clear optimal number of clusters. However, by reducing the dimensions, I was able to gain better insights into the clustering structure, making it easier to determine the appropriate number of clusters.


![image](https://github.com/user-attachments/assets/83f27b08-a268-48e0-9d40-d615af0bfcd8)

However, The cluster decision isn't clear yet. To address this, I used the Silhouette Score, which measures how well-defined clusters are. A lower Silhouette Score indicates more intertwined clusters, while a higher score suggests well-separated groups.

After analyzing the scores, I found that 4 clusters provided the best balance, ensuring distinct and meaningful segmentation for this project


**Segments insight**
 **Career-Focused Segment (43% of Customers)** This segment consists mainly of individuals in high-level executive roles, contributing to 26% of revenue by segment and 36% of revenue from Product 4, indicating strong ambition and financial stability. **Standard Segment (36% of Customers)** This segment works in skilled employee, official, or management roles, representing 36% of the customer base and 48% of revenue from Product 5, making them a significant segment with high purchase power. They account for 43% of total sales, with Product 5 being the top-seller. **Fewer Opportunities (12% of Customers)** This segment is typically found in self-employed, highly qualified, or officer roles, representing the higher end of skilled occupations. They account for 12% of the customer base and hold the biggest proportion of revenue with 56% from Product 2, making them a smaller but influential group. **Well-Off Segment (10% of Customers)** This segment consists mostly of single women with average education levels and lower income within the range. Their occupations are generally on the lower end of the spectrum. They represent 9% of the dataset, contributing to 40% of revenue from Product 5, 26% from Product 4, and 24% from Product 2.

**Price Elasticity of Demand** 
I aimed to analyze demand elasticity, which measures how sensitive product demand (quantity sold) is to price changes. The key goal was to determine how much a small change in price would impact the quantity sold and, ultimately, revenue.

To achieve this, I wrote a Python function that calculates the price elasticity of demand for each product. The function follows the fundamental elasticity formula: 
 E=β 
p
​
 ×( 
Mean Quantity
Mean Price
​
 )

E: Elasticity of a product

𝛽𝑝: Coefficient of price impact on demand

I wrote the calculate_elasticity function to loop through all products, extract their respective price coefficients, and apply the elasticity formula. Here's a step-by-step breakdown:

Mapped Products to Their Price Variables

In my dataset, each product (e.g., Product_1) had a corresponding price row (e.g., Price_1).
I created a dictionary price_map to link products to their corresponding price variables.
Iterated Through Each Product

I extracted the price coefficient (price_coef), which was already calculated in my previous model.
Retrieved the mean price and mean quantity of the product from precomputed statistics.
Applied the Elasticity Formula

**The Challenges I faced along the way** 
Indexing Issues with temp.loc

Initially, I faced an error because I was trying to directly index the price coefficients without properly mapping product names to price rows.
I resolved this by ensuring each product column correctly mapped to its corresponding price row using the price_map dictionary.

The function multiplied the price coefficient by the ratio of mean price / mean quantity to compute the final elasticity value for each product.
Returned the results as a DataFrame

To keep results organized, I converted the dictionary into a Pandas DataFrame for better readability and further analysis.

Interpreting Elasticity Values

After computing elasticity, I had to ensure the values made sense. Products with high elasticity (>1) indicated that a small price change significantly impacted demand. Products with low elasticity (<1) suggested that demand was relatively stable despite price changes.

**Key Insights from the Elasticity Analysis**

Some products had very high elasticity, meaning a small price increase could lead to a large drop in sales. Others had low elasticity, suggesting that customers were less sensitive to price changes. Using this data, I was able to identify optimal price adjustments per product to maximize revenue.

