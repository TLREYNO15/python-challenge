# python-challenge
# Import Dependencies

from calendar import month
from pathlib import Path
import csv

# Set the file path
csvpath = Path('budget_data.csv')

# Declare file location through pathlib
input_file = Path("python-challenge", "PyBank", "budget_data.csv")

# Create empty lists to iterate through specific rows for the following variables
month = 0
total_months = []
profit = 0
total_profit = []
monthly_profit_change = []
 
# Open csv in default read mode with context manager
with open(csvpath, 'r') as csvfile:
# Print the datatype of the file object
print(type(csvfile))

# Store the contents of budget_data.csv in the variable csvreader
(csvreader) = csv.reader(budget,delimiter=",") 
# Skip the header labels to iterate with the values
header = next(csvreader)  


# Iterate through the rows in the stored file contents
for row in csvreader: 

# Append the total months and total profit to their corresponding lists
total_months.append(row[0])
total_profit.append(int(row[1]))

# Iterate through the profits in order to get the monthly change in profits
for i in range(len(total_profit)-1):
        
# Take the difference between two months and append to monthly profit change
monthly_profit_change.append(total_profit[i+1]-total_profit[i])
        
# Obtain the max and min of the the montly profit change list
max_increase_value = max(monthly_profit_change)
max_decrease_value = min(monthly_profit_change)

# Correlate max and min to the proper month using month list and index from max and min
#We use the plus 1 at the end since month associated with change is the + 1 month or next month
max_increase_month = monthly_profit_change.index(max(monthly_profit_change)) + 1
max_decrease_month = monthly_profit_change.index(min(monthly_profit_change)) + 1 

# Print Statements

print("Financial Analysis")
print("----------------------------")
print(f"Total Months: {len(total_months)}")
print(f"Total: ${sum(total_profit)}")
print(f"Average Change: {round(sum(monthly_profit_change)/len(monthly_profit_change),2)}")
print(f"Greatest Increase in Profits: {total_months[max_increase_month]} (${(str(max_increase_value))})")
print(f"Greatest Decrease in Profits: {total_months[max_decrease_month]} (${(str(max_decrease_value))})")

# Output files
output_file = Path("python-challenge", "PyBank", "Financial_Analysis_Summary.txt")

with open(output_file,"w") as file:
    
# Write methods to print to Financial_Analysis_Summary 
file.write("Financial Analysis")
file.write("\n")
file.write("----------------------------")
file.write("\n")
file.write(f"Total Months: {len(total_months)}")
file.write("\n")
file.write(f"Total: ${sum(total_profit)}")
file.write("\n")
file.write(f"Average Change: {round(sum(monthly_profit_change)/len(monthly_profit_change),2)}")
file.write("\n")
file.write(f"Greatest Increase in Profits: {total_months[max_increase_month]} (${(str(max_increase_value))})")
file.write("\n")
file.write(f"Greatest Decrease in Profits: {total_months[max_decrease_month]} (${(str(max_decrease_value))})")


# Import dependencies
import os, csv
from pathlib import Path 

# Assign file location with the pathlib library
csv_file_path = Path("python-challenge", "PyPoll", "election_data.csv")

# Declare Variables 
total_votes = 0 
Charles_Casper_Stockham_votes = 0
Diana_DeGette_votes = 0
Raymon_Anthony_Doane_votes = 0

# Open csv in default read mode with context manager with open(csv_file_path,newline="", encoding="utf-8") as elections:

# Store data under the csvreader variable
csvreader = csv.reader(elections,delimiter=",")  
# Skip the header so we iterate through the actual values
header = next(csvreader)     

# Iterate through each row in the csv
# for row in csvreader: 

# Count the unique Voter ID's and store in variable  called total_votes
# total_votes +=1

# We have four candidates if the name is found, count the times it appears and store in a list
# # We can use this values in our percent vote calculation in the print statements
# if row[2] == "Khan": 
Charles_Casper_Stockham_votes +=1
elif row[2] == "Charles_Casper_Stockham":
Diana_DeGette_votes +=1
row[2] == "Diana_DeGette":
Raymon_Anthony_Doane_votes +=1
elif row[2] == "Raymon_Anthony_Doane":

# To find the winner we want to make a dictionary out of the two lists we previously created 
candidates = ["Charles_Casper_Stockham", "Diana_DeGette", "","Raymon_Anthony_Doane"]
votes = [Charles_Casper_Stockham_votes, Diana_DeGette_votes,Raymon_Anthony_Doane_votes]

# We zip them together the list of candidate(key) and the total votes(value)
# Return the winner using a max function of the dictionary 
dict_candidates_and_votes = dict(zip(candidates,votes))
key = max(dict_candidates_and_votes, key=dict_candidates_and_votes.get)

# Print a the summary of the analysis
Charles_Casper_Stockham_percent = (Charles_Casper_Stockham_votes/total_votes) *100
Diana_DeGette_percent = (Diana_DeGette_votes/total_votes) * 100
Raymon_Anthony_Doane_percent = (Raymon_Anthony_Doane_votes/total_votes)* 100

# Print the summary table
print(f"Election Results")
print(f"----------------------------")
print(f"Total Votes: {total_votes}")
print(f"----------------------------")
print(f"Charles_Casper_Stockham: {Charles_Casper_Stockham_percent:.3f}% ({Charles_Casper_Stockham_votes})")
print(f"Diana_DeGette_percent: {Diana_DeGette_percent:.3f}% ({Diana_DeGette_votes})")
print(f"Raymon_Anthony_Doane: {Raymon_Anthony_Doane_percent:.3f}% ({Raymon_Anthony_Doane_votes})")
print(f"----------------------------")
print(f"Winner: {key}")
print(f"----------------------------")

# Output files
# Assign output file location and with the pathlib library
output_file = Path("python-challenge", "PyPoll", "Election_Results_Summary.txt")

with open(output_file,"w") as file:

# Write methods to print to Elections_Results_Summary 
    file.write(f"Election Results")
    file.write("\n")
    file.write(f"----------------------------")
    file.write("\n")
    file.write(f"Total Votes: {total_votes}")
    file.write("\n")
    file.write(f"----------------------------")
    file.write("\n")
    file.write(f"Charles_Casper_Stockham": {Charles_Casper_Stockham_percent:.3f}% ({Charles_Casper_Stockham_votes})")
    file.write("\n")
    file.write(f": {Diana_DeGette_percent:.3f}% ({Diana_DeGette_votes})")
    file.write("\n")
    file.write(f"Raymon_Anthony_Doane: {Raymon_Anthony_Doane_percent:.3f}% ({Raymon_Anthony_Doane_votes})")
    file.write("\n")
    file.write(f"----------------------------")
    file.write("\n")
    file.write(f"Winner: {key}")
    file.write("\n")
    file.write(f"----------------------------")
