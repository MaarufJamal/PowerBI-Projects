# Case Study: Analyzing Customer Churn in PowerBI


## Case Statement

One of the main priorities for subscription-based organizations is lowering client attrition. You will examine and evaluate the churn rates of a dataset from Databel, an example telecom firm, in this Power BI case study.

## Recognize the causes of Customer Churn

Understanding the turnover rate alone is not enough to analyze churn; you also need to understand why customers are leaving at the pace they are and how to keep them from leaving. In order to create measurements and calculated columns and to create visually appealing report pages, you will need to address these questions.


### Steps followed 

- Step 1 : I loaded data into Power BI Desktop, dataset titled 'Databel.csv' is a csv file.
- Step 2 : In the first page I tried to see if the number of total customers is equal to the total number of unique customers by counting the number of distinct customer IDs. For this I used a new measure 'Number of Unique Customers' for which the follwing DAX is applied:
      
        Number of Unique Customers = DISTINCTCOUNT('Databel - Data'[Customer ID]) 
    I used card visuals to showcase this and as the numbers are equal, I can safely say that there are no repeating data
    ![Card](https://github-production-user-asset-6210df.s3.amazonaws.com/182015694/368939718-3fceabb0-8147-4054-9a90-552856bc0502.PNG?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAVCODYLSA53PQK4ZA%2F20240919%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20240919T095809Z&X-Amz-Expires=300&X-Amz-Signature=3287972f7d0797c621e57f2a989d0aa8a354624bc367041587612ee2a862b6ac&X-Amz-SignedHeaders=host&actor_id=182015694&key_id=0&repo_id=859535262)
    

- Step 3 : After that I calculated the total number of churned customer by using a measure Churned with the DAX:
      
        Churned = IF('Databel - Data'[Churn Label]="Yes",1,0) 
    The new measure shown as a column:

    ![Churned](https://github-production-user-asset-6210df.s3.amazonaws.com/182015694/368938941-47ec025f-b436-4a2b-802e-277df0a6dd46.jpg?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAVCODYLSA53PQK4ZA%2F20240919%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20240919T095629Z&X-Amz-Expires=300&X-Amz-Signature=a2fd14c51cb286d2704dd008186b1639918bb594b46a808c09d273cf733a7b33&X-Amz-SignedHeaders=host&actor_id=182015694&key_id=0&repo_id=859535262)
- Step 4 : Next step was to calculate the churn rate across different categories. So I added a new Measure, Churn Rate. The DAX for this measure follows:
      
        Churn Rate = [Number of Churned Customers]/[Number of Customers] 
    I also used a card to show that data.

- Step 5 : I showcased these in the 'Churn Demographic' page. Which looks like:
    ![Demographics](https://github-production-user-asset-6210df.s3.amazonaws.com/182015694/368940845-e094b640-b73b-434b-a6b8-004e2cbeb6b5.PNG?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAVCODYLSA53PQK4ZA%2F20240919%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20240919T100125Z&X-Amz-Expires=300&X-Amz-Signature=fe1cf34ee0d46dbaba5fbcdb0b83ac576df651925f7aa34cf2818776726544a4&X-Amz-SignedHeaders=host&actor_id=182015694&key_id=0&repo_id=859535262)
- Step 6 : I calculated percentage of churned customers across different churn categories. So in a clustered bar chart we added %GT of Number of Customers on the X axis and Churn reasons in Y axis.Very important note here is that we had to add a filtre on the Churn Label and select that as Yes, so that the customers who are not churned are not counted.
- Step 7 : I also created an Age Bin with an interval of 10 years. A snapshot of the new bin column is displayed below
    ![Bins](https://github-production-user-asset-6210df.s3.amazonaws.com/182015694/368925040-1ae5a02d-fd22-464a-aeed-d9af4836a591.PNG?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAVCODYLSA53PQK4ZA%2F20240919%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20240919T094410Z&X-Amz-Expires=300&X-Amz-Signature=69e7df999321a6c6e8fe7426ef5d02d8d58703bef8048cbc40d97599d1091d68&X-Amz-SignedHeaders=host&actor_id=182015694&key_id=0&repo_id=859535262)

- Step 8 : I added a Line and Clustered Column chart showcasing number of customers the age for different age groups where the line represented the churnt rate for those age groups.
- Step 9 : Next I added a new page where I different vizualized different Group and categories. I added a donut chart where the Legend is Contract Type and Values are Count of Customer ID as shown in the following snapshot
![3rd](https://github-production-user-asset-6210df.s3.amazonaws.com/182015694/368952583-c46e13ea-a646-47d7-a8ed-cf99d73879d8.PNG?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAVCODYLSA53PQK4ZA%2F20240919%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20240919T103706Z&X-Amz-Expires=300&X-Amz-Signature=50064c9ab61226a3179f8e61885c2a05b28ff984d42b1061d8af35d1c67778f7&X-Amz-SignedHeaders=host&actor_id=182015694&key_id=0&repo_id=859535262) 

- Step 10 : I added a clustered column chart showcasing Churnt Rate by Contract Category and Gender where X axis is Contract Category, Y axis is Churn Rate and Legend is Gender.
- Step 11 : I added a pie chart where we showcased churn rate by category, where Legend is Churn Category and Values are Count of Customer ID.
- Step 12 : To filter these values across Monthly and Yearly Churn Rates, I adeed a Multi Row card where the fields are Churn Rate and Contract Category.
- Step 13 : Next I added a clustered bar chart showcasing churn rate for different group consumptions and different plans. Also a table with churn rate and different data plan was also added for extra details. For this I had to create a new Column Grouped consumptions where the following DAX was added
      
        Grouped Consumption = IF('Databel - Data'[Avg Monthly GB Download]<5,"Less than 5 GB", IF('Databel - Data'[Avg Monthly GB Download]<10,"Between 5 and 10 GB","10 or more GB")))
    ![Grouped Consumption](https://github-production-user-asset-6210df.s3.amazonaws.com/182015694/368936474-f609a865-a916-40e0-8411-84a005eddb7a.PNG?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAVCODYLSA53PQK4ZA%2F20240919%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20240919T094949Z&X-Amz-Expires=300&X-Amz-Signature=7b94ce11fec5e081973a01f669b1fbcaee522c18d7c3af0a355e4169e41eb50b&X-Amz-SignedHeaders=host&actor_id=182015694&key_id=0&repo_id=859535262)
    The table filtering out more information was also added as shown below:
    ![4th](https://github-production-user-asset-6210df.s3.amazonaws.com/182015694/368953438-9ed8bb6e-8d26-4f57-9257-323ac20866a0.PNG?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAVCODYLSA53PQK4ZA%2F20240919%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20240919T104042Z&X-Amz-Expires=300&X-Amz-Signature=beab6ae2ec2dde4e6a92399fa956035bdd74344ee7706189c7f17920c316250b&X-Amz-SignedHeaders=host&actor_id=182015694&key_id=0&repo_id=859535262)

- Step 14 : Next I have a pie chart displaying Number of Customers with respect to different payment methods where the legend is payment method and values are Count of Customer ID.
    ![5th](https://github-production-user-asset-6210df.s3.amazonaws.com/182015694/368954311-63c10318-3877-46c9-a1c7-b776e63da219.PNG?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAVCODYLSA53PQK4ZA%2F20240919%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20240919T104205Z&X-Amz-Expires=300&X-Amz-Signature=d543391ec22c7fb3034ad3fe387efedf303c6c38772ef9ee44714aa770762cd3&X-Amz-SignedHeaders=host&actor_id=182015694&key_id=0&repo_id=859535262)
- Step 15 : Additionally in the page titled "Contract Type" I added a line chart showing Churn Rate by Account Length and Contract Type.
- Step 16 : Finally I added a Map Visual to display churn rqate by state where I filtered the bubbles to mark it by Red circle for the largest value. 
    ![6th](https://github-production-user-asset-6210df.s3.amazonaws.com/182015694/368954944-ba9c0bda-a82f-4065-9d89-2222209aa74e.PNG?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAVCODYLSA53PQK4ZA%2F20240919%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20240919T104552Z&X-Amz-Expires=300&X-Amz-Signature=d5094c5c85140a6bf97778a5535fb78dc3d5a616b84e80950547ec3b5cd41a8a&X-Amz-SignedHeaders=host&actor_id=182015694&key_id=0&repo_id=859535262)
