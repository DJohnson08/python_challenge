import csv

# File paths
input_file = r"budget_data.csv"
output_file = r"PyBank_analysis.txt"

# Initialize variables
total_months = 0
net_total = 0
changes = []
months = []

# Read the CSV file
with open(input_file) as csvfile:
    csvreader = csv.reader(csvfile)
    header = next(csvreader)  # Skip header
    
    # Initialize variables to store the previous month's value
    previous_value = None
    
    for row in csvreader:
        month = row[0]
        profit_loss = int(row[1])
        total_months += 1
        net_total += profit_loss
        
        # Calculate the monthly change
        if previous_value is not None:
            change = profit_loss - previous_value
            changes.append(change)
            months.append(month)
        
        previous_value = profit_loss

# Calculate average change
average_change = sum(changes) / len(changes)

# Find the greatest increase and decrease
max_increase = max(changes)
max_decrease = min(changes)
max_increase_month = months[changes.index(max_increase)]
max_decrease_month = months[changes.index(max_decrease)]

# Prepare output string
output = (
    "Financial Analysis\n"
    "----------------------------\n"
    f"Total Months: {total_months}\n"
    f"Total: ${net_total}\n"
    f"Average Change: ${average_change:.2f}\n"
    f"Greatest Increase in Profits: {max_increase_month} (${max_increase})\n"
    f"Greatest Decrease in Profits: {max_decrease_month} (${max_decrease})\n"
)

# Print the results
print(output)

# Write the results to a text file
with open(output_file, 'w') as text_file:
    text_file.write(output)
