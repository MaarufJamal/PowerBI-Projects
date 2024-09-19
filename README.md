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
  ![Card](Assets\Card.PNG)

- Step 3 : After that I calculated the total number of churned customer by using a measure Churned with the DAX:

        Churned = IF('Databel - Data'[Churn Label]="Yes",1,0)

  The new measure shown as a column:

  ![Churned](Assets\Churned.jpg)

- Step 4 : Next step was to calculate the churn rate across different categories. So I added a new Measure, Churn Rate. The DAX for this measure follows:

        Churn Rate = [Number of Churned Customers]/[Number of Customers]

  I also used a card to show that data.

- Step 5 : I showcased these in the 'Churn Demographic' page. Which looks like:
  ![Demographics](Assets\Demographics.PNG)
- Step 6 : I calculated percentage of churned customers across different churn categories. So in a clustered bar chart we added %GT of Number of Customers on the X axis and Churn reasons in Y axis.Very important note here is that we had to add a filtre on the Churn Label and select that as Yes, so that the customers who are not churned are not counted.
- Step 7 : I also created an Age Bin with an interval of 10 years. A snapshot of the new bin column is displayed below
  ![Bins](Assets\Bins.PNG)

- Step 8 : I added a Line and Clustered Column chart showcasing number of customers the age for different age groups where the line represented the churnt rate for those age groups.
- Step 9 : Next I added a new page where I different vizualized different Group and categories. I added a donut chart where the Legend is Contract Type and Values are Count of Customer ID as shown in the following snapshot
  ![3rd](Assets\3rd.PNG)

- Step 10 : I added a clustered column chart showcasing Churnt Rate by Contract Category and Gender where X axis is Contract Category, Y axis is Churn Rate and Legend is Gender.
- Step 11 : I added a pie chart where we showcased churn rate by category, where Legend is Churn Category and Values are Count of Customer ID.
- Step 12 : To filter these values across Monthly and Yearly Churn Rates, I adeed a Multi Row card where the fields are Churn Rate and Contract Category.
- Step 13 : Next I added a clustered bar chart showcasing churn rate for different group consumptions and different plans. Also a table with churn rate and different data plan was also added for extra details. For this I had to create a new Column Grouped consumptions where the following DAX was added

  ```txt
  Grouped Consumption = IF('Databel - Data'[Avg Monthly GB Download]<5,"Less than 5 GB", IF('Databel - Data'[Avg Monthly GB Download]<10,"Between 5 and 10 GB","10 or more GB"))
  ```

  ![Grouped Consumption]("https://github.com/MaarufJamal/PowerBI-Projects/blob/bf39dfe2b377ddcf89d4fe5e359dacb004838c94/Assets/GroupedConsumption.PNG")

  The table filtering out more information was also added as shown below:
  ![4th](Assets\4th.PNG)

- Step 14 : Next I have a pie chart displaying Number of Customers with respect to different payment methods where the legend is payment method and values are Count of Customer ID.
  ![5th](Assets\5th.PNG)
- Step 15 : Additionally in the page titled "Contract Type" I added a line chart showing Churn Rate by Account Length and Contract Type.
- Step 16 : Finally I added a Map Visual to display churn rqate by state where I filtered the bubbles to mark it by Red circle for the largest value.
  ![6th](Assets\6th.PNG)
