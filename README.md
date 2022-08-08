# # Loan Qualifier Application


Project was built to help determine if user applies for a loan and where. Applicants insert finacial data and personal data to apply for a loan. Output will resulit in asking user if they would like to save loan qualifiers as csv file.


## Technologies

Python is used to help filter user data to find if the user qualifies for a loan. User inserts data and python will search from a csv file to meet certain criteria. Finacial data is used in formulas to determine if user qualify for loans and which banks offer the loans.If user qualifies for loans it will ask if they would like to save as a csv file.


## Installation Guide
User will want to make sure that fire and questionary are installed. 
operator will have to import libary to use loan query.

```pip install fire```

```pip install questionary```



![image](https://user-images.githubusercontent.com/107014664/183303599-ead531aa-c4cd-408a-ab24-298e67c44640.png)


## Usage
This app queries the customer on various financial data to match qualifying loans. 

Loan qualification criteria is based on:
        - Credit Score
        - Loan Size
        - Debit to Income ratio (calculated)
        - Loan to Value ratio (calculated)
        
 ![image](https://user-images.githubusercontent.com/107014664/183316094-d81ddbd9-36ed-4e13-be2e-c17e9fff0c3c.png)
  
        
  This application will ask the user its financial data to match them to banks that they qualify for or it won't show any if they don't qualify. 
  
  
    bank_data_filtered = filter_max_loan_size(loan, bank_data)
    bank_data_filtered = filter_credit_score(credit_score, bank_data_filtered)
    bank_data_filtered = filter_debt_to_income(monthly_debt_ratio, bank_data_filtered)
    bank_data_filtered = filter_loan_to_value(loan_to_value_ratio, bank_data_filtered)

    print(f"Found {len(bank_data_filtered)} qualifying loans")

    return bank_data_filtered
  
  The application will use the code below to see if user qualifies for a loan. It will look at the Information within the csv file to pull the data.
  
     qualifying_loans=questionary.confirm("Do you want to save your qualifying loans").ask()
     csvpath = Path('qualifying_loans.csv')
     save_csv(csvpath, qualifying_loans)

def save_csv(csvpath):
    with open(csvpath, "r") as csvfile:
        data = [filter_credit_score,filter_debt_to_income,filter_loan_to_value,filter_max_loan_size]
        csvreader = csv.reader(csvfile, delimiter=",")
        next(csvreader)

        for row in csvreader:
            data.append(row)
        return data
        
        
        
        
        
        
        
        
        
        
        
