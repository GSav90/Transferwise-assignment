### Goal
Reduce Friction

### How
- automated ID document checks 
    - Manual checks
        Time consuming by customer care
        Labor cost
        Human error
- smarter about assessing customer risk and ask the information accordingly
- influence the regulators to change the regulations of course

### Questions
- Which customers are risky?
    - Identify Strange behavior/outliers(not normal)
        Outlier Analysis
            Define what is normal behavior
            Whatever doesn't fit normal behavior criteria is your output.
    - Set limits/restrictions based on above results(Request additional documents, Verification call, Contact customer care, threshold limit)
        Show customer impact
        Hypothesize likely behavior(In other words, predict what customer would do if you take xyz action)

- What kind of info would you like to acquire from/about these customers in order to trust our service to them or deny it? How would you go about getting this info?
    - when do we stop our customer to check up on their identity
    - how do we stop our customer to check up on their identity()


### Columns




user_id	request_id	target_recipient_id	date_user_created	addr_country_code	addr_city	recipient_country_code	flag_personal_business	payment_type	date_request_submitted	date_request_received	date_request_transferred	date_request_cancelled	invoice_value	invoice_value_cancel	flag_transferred	payment_status	ccy_send	ccy_target	transfer_to_self	sending_bank_name	sending_bank_country	payment_reference_classification	device	transfer_sequence	days_since_previous_req	first_attempt_date	first_success_date

### Tools
- Visualization tool:
    Tableau
    PowerBI
- Python
    Data Manipulation
        Matplotlib
        Plotly
        Seaborn
    Statistical Analysis
        Mean
        Variance
        Percentile analysis
    Machine Learning
        Outlier analysis
            OneclassSVM: Define normal
            IsolationForest: Define normal, then given a new data point predict outliers

### Designing Solution: Summary
- Slicing of data
    By country
    By bank
    by payment_type
    by flag_personal_business
    by payment_reference_classification
    by device
    by transfer_sequence and customer lifetime

- Derived columns
    Normal vs unusual
    confidence based on customer reliability

- Risky Customers
    New Customers who trying to tranfer big amounts
    Old customer suddenly tranferring unusual amount
    Too frequent tranfers to multiple recipients
    Read current regulations and find restrictions(Generic vs countrywise)
    transfer_to_self

    
### Detailed Analysis
- New Customers who trying to tranfer big amounts
    - Average amount overall, by country, and by ccy send to ccy received
        >3 std dev times the average is unusual amount
    

def normal_amount_by_country(ccy_send, ccy_rcvd,thd=1.5):
    # plot distribution and 
    # return: 1(unusual) or 0(normal)
    # Numpy uses ntile= 99th percentile






### Resources
https://towardsdatascience.com/practical-implementation-of-outlier-detection-in-python-90680453b3ce
https://towardsdatascience.com/detecting-and-treating-outliers-in-python-part-1-4ece5098b755 
ML based: https://machinelearningmastery.com/model-based-outlier-detection-and-removal-in-python/

### Plotly 101
https://www.kaggle.com/kanncaa1/plotly-tutorial-for-beginners
https://kanoki.org/2019/12/31/how-to-create-interactive-data-visualization-using-plotly/
https://www.geeksforgeeks.org/python-plotly-tutorial/
https://towardsdatascience.com/choropleth-maps-101-using-plotly-5daf85e7275d