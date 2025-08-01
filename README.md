# Cloudwalk-DataAnalyst-
Project Cloudwalk


FRAUD DETECTION SYSTEM

This project identifies potential fraud in financial transactions in a simple and effective way.  
It combines clear rule-based analysis with AI (KMeans++) and generates automatic reports.

------------------------------------------------------------
WHAT IT DOES

1. Analyzes user behavior (average transaction amount, devices used, transaction frequency, etc.).
2. Applies real-time fraud detection rules:
   - Very high or very low transaction amounts.
   - Many different devices used by the same user.
   - Transactions occurring too close together.
   - Daily and per-transaction limits exceeded.
   - Detects "card testing" attempts.

3. Groups users with similar behaviors using AI (KMeans++).
4. Generates automatic reports:
   - Excel file with a detailed transaction log and decisions.
   - Word document with summary statistics.
   - Confusion Matrix image (shows decision quality).

------------------------------------------------------------
OUTPUT

Each run creates a folder with the date and time, for example:

output/
  20250731_1530/
    log_transactions.xlsx
    final_analysis.docx
    confusion_matrix.png

This keeps a history of previous analyses.

------------------------------------------------------------
WHAT YOU NEED

Install these Python libraries:

pip install pandas numpy matplotlib seaborn scikit-learn openpyxl python-docx

------------------------------------------------------------
HOW TO RUN

1. Update the CSV file path and output folder at the top of the code:
   csv_file = r"C:\...\transactional-sample.csv"
   base_output_dir = r"C:\...\output"

2. Run the script:
   python antifraud.py

3. The system will:
   - Read the transaction CSV file.
   - Build user profiles.
   - Apply fraud detection rules.
   - Generate all reports automatically.

------------------------------------------------------------
METRICS

The system shows accuracy and errors using a Confusion Matrix:
- TP: Fraudulent transactions correctly blocked.
- FP: Legitimate transactions blocked by mistake.
- FN: Fraudulent transactions that were missed.
- TN: Legitimate transactions correctly approved.

It also calculates the false positive and false negative rates.

------------------------------------------------------------
ADJUSTING THE RULES

You can change the fraud detection thresholds inside the AntiFraudSystem class:

self.rules = {
    'max_transactions_per_hour': 5,
    'max_amount_per_day': 5000,
    'max_amount_single': 3000,
    'card_testing_amount': 5.00,
    'suspicious_intervals': {'critical': 2, 'high': 10}
}

------------------------------------------------------------
