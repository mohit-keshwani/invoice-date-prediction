# Invoice Date Prediction

## About
 - I received an invoice dataset of a company that contains the past payment information and behaviour of various buyers. Based on the previous payment patterns, the ML model needs to predict what will be the date a payment is to be made by the customer for an invoice. The model also needs to predict which aging bucket the invoice falls into based on the predicted payment date. 
 - Basially, the Machine Learning part is divided into two subparts:
     - To build a Machine Learning Model to predict the payment date of an invoice when it gets created in the system. 
     - Categorize the invoice into different buckets based on predicted payment date.<br>
            1) 0-15 days <br>
            2) 16-30 days <br>
            3) 31-45 days <br>
            4) 46-60 days <br>
            5) Greater than 60 days <br>
            
 ## Technology And Libraries Used:
  - Machine Learning
  - Scikit-Learn
  - Python
  - Numpy
  - Pandas
  - Matplotlib
  - Seaborn
  - Plotly
  - Pickle
  - Jupyter Notebook
            
## Dataset
  - I received a dataset which contains 50000 rows and 19 features listed below.
 
**Original Features in Dataset:**
   - business_code - company code of the account
   - cust_number - customer number given to all the customers of the Account
   - name_customer - name of the customer.
   - clear_date - The date on which the customer clears an invoice, or in simple terms, they make the full payment.
   - buisness_year - the year in which invoice was created
   - doc_id - It is also an unique identifier of an invoice is a primary key for acct_doc_header table
   - posting_date - 
   - document_create_date - The date on which the document was created
   - document_create_date.1 - The date on which the invoice document was created 
   - due_in_date - The date on which the customer is expected to clear an invoice
   - invoice_currency - The currency of the invoice amount in the document for the invoice
   - document type - It represents the type of document. eg D1 represents Invoice
   - posting_id - key indicator to identify whether an AR item is invoice, deduction, credit memo based on its value. Apllicable for SAP ERP
   - area_business - Business area in sap is defined as an organisationalarea within the financial accounting module.
   - total_open_amount - The amount that is yet to be paid for that invoice
   - baseline_create_date - The date on which the Invoice was created.
   - cust_payment_terms - Business terms and agreements between customers and accounts on discounts and days of payment
   - invoice_id - Unique number assigned when a seller creates an Invoice. 	
   - isOpen - indicator of whether an invoice is open or closed. isopen = 1, means the invoice is open.
   
   
**Engineered Features:**
 - *__Invoice Level Features__*
     - **paid_invoices** - Number of paid invoices prior to the creation date of a new invoice of a customer. 
     - **late_paid_invoices** - Number of invoices which were paid late prior to the creation date of a new invoice of a customer 
     - **ratio_late_paid_invoices** - late_paid_invoices / paid_invoices
     - **total_amount_paid_invoices** - The sum of the base amount from all the paid invoices prior to the creation of new invoice for a customer.
     - **total_amount_late_paid_invoices** - The sum of the base amount from all the paid invoices which were late prior to the creation of new invoice for a customer. 
     - **ratio_amount_late_paid_invoices** - total_amount_late_paid_invoices / total_amount_paid_invoices
     - **average_days_late** - Average days late of all paid invoices that were late prior to the creation date of a new invoice for a customer.
     - **total_outstanding_invoices** - Number of the outstanding invoices prior to the creation date of a new invoice of a customer. 
     - **total_late_outstanding_invoices** - Number of the outstanding invoices which were late prior to the creation date of a new invoice of a customer.
     - **ratio_late_outstanding_invoices** - total_late_outstanding_invoices / total_outstanding_invoices
     - **total_amount_outstanding_invoices** - The sum of the base amount from all the outstanding invoices prior to the creation of new invoice for a customer.
     - **total_amount_late_outstanding_invoices** - The sum of the base amount from all the outstanding invoices which were late prior to the creation of new invoice for a customer. 
     - **ratio_amount_late_outstanding_invoices** - total_amount_late_outstanding_invoices / total_amount_outstanding_invoices
     - **average_days_late_outstanding_invoices** - Average days late of all outstanding invoices that were late prior to the creation of new invoice for a customer.

[Dataset](https://github.com/mohit-keshwani/invoice-date-prediction/tree/main/Data)

## Model Performance
Model | R2 Score | RMSE | MAE
--- | --- | --- | ---
KNN Regressor | 0.371 | 6.827 | 2.394
Random Forest Regressor | 0.397 | 6.688 | 2.390
Gradient Boosting Regressor | 0.390 | 6.723 | 2.342
XG Boost Regressor | 0.367 | 6.850 | 2.356
