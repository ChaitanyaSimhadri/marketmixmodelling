# Market mix model
Capstone project submitted for IIIT Bangalore and Upgrad for Evaluation


Problem Statement
ElecKart is a leading e-commerce chain based in Ontario, Canada, specialising in electronic products. The brand has shown commendable growth in just a few years of its operation. However, over the last one year, ElecKart has faced a revenue dip even after spending a significant amount of money on marketing and promotions. There was a high customer churn ratio because the company was failing to understand customer demographics and cater to the needs of their customers.

Essentially, the company wants —

What are the KPIs that Drive the Top Line Performance?
What is the quantitative impact of each commercial lever on revenue?
How eleckart allocate budgets on different marketing campaigns


Summary
Dataset 'ConsumerElectronics' have 1648824 rows and 20 cols

Understanding Data : The target variable, in this case is decided as 'gmv' Which is Gross merchandise value

Data Preparation: After data cleaning, Removing NUlls and Outliers total rows retained from Datset are 1465066 which is 88%

Imputed null values in few col with 0 and dropped rest of the rows which has NAN vals
Converted few Features from Categorical cols to Flot vars
Treated Outliers of few cols and replaced with 0,99 percentile
Feature Engineering: Derived New KPIs whic are needed for MMM

 - Derived New col week from Date col
- A - KPIs replated to Advertisement
     * Generated Adstock values from the Adverisement spends
- P - KPI's related to price
    * listing_price =  gmv/total_units
    * replaced MRP with listing price where listing price more than MRP
- D - KPI's related to discount
    * Discount%  =  mrp-listprice/mrp
- Q -  KPI's Related to Product assortment and Quality
      * Order_payment_type
      * Generating new coulumn weather product is premium or not
       * NPS score from the customers
- T - KPI's related to industry trend, Seasonality Etc
     * SpeciAl Sale Calender
     * Holiday list
     * payday
After feature selection, Aggregated the Complete Dataset to weekly level and Seggregated the Data to three Categories

Camera accessoried
Home audio
Gaming Accessory
Used Linear Regression Additive Model and Multiplicative Model on all three Datasets

Below are few observations based on the Modellng
 Additive Model Scores:
 Camera Accessary  -  R2 Score on Test Data - 0.8014843753292288, on Train data - 0.9751149715897107
 Home Audio -  R2 Score on Test Data - 0.14963637297420018, on Train data - 0.14963637297420018
 Gaming Accessary-  R2 Score on Test Data - -1.5303001348794707, on Train data - 0.9773583045274947
 Multiplicative Model: 
 Camera Accessary  -  R2 Score on Test Data -- 0.9868555048474846, on Train data - 0.990254012909584
 Home Audio -  R2 Score on Test Data -- 0.990254012909584, on Train data - 0.990254012909584
 Gaming Accessary -  R2 Score on Test Data -- 0.9887077514241147, on Train data - 0.9966545388956052
Overall Multiplicative Model has the best fit on the dataset

Best Fit line of All three Multiplicative Models are as below

revenue(Camera Accessary) =  Const + 0.46 * Other_SMA3 + 0,27 * cameratripod + 0.75 * lens + 0.05 * Tv_Adstock – 0.06 * Content_Marketing_adstock
Revenue(Home Audio) = Const + 0.38 * homeaudiospeaker + homeaudiospeaker * homeaudiospeaker - 0.23*Online_marketing_adstock + 0.16 * Online_marketing_adstock - 0.04 * Other_SMA3

Revenue(Gaming Accessory): Const + 0.51 * gamepad + 0.43* gamingaccessorykit + 0.42 * gamingkeyboard + gamingkeyboard + gamingkeyboard + ContentMarketing_SMA3 * ContentMarketing_SMA3 + 0.22* listing_price_SMA3

Recommendations: Camera Accessary:

Concentrate More on products like camerabattery, lens and Cameratripod
These Items yeild more revenue
TV is the best advertising Media of all. Invest in the TV advertising and Content marketing can be skipped
Home Audio: Concentrate on

Concentrate more on products game pad, gaming accessory kit, keyboard and mouse
Content marketing is the best marketing statergy fpr Home Audio products
Gaming Accessary:

Concentrate more on products game pad, gaming accessory kit, keyboard and mouse
Content marketing is the best marketing statergy fpr Home Audio products
