# finance-tracker
from datetime import datetime

class FinanceTracker:
    def __init__(self):
        self.records = []

    def add_transaction(self, amount, category, trans_type):
        if trans_type not in ["income", "expense"]:
            raise ValueError("Transaction type must be 'income' or 'expense'")
        self.records.append({
            "amount": amount,
            "category": category,
            "type": trans_type,
            "date": datetime.now()
        })

    def get_monthly_summary(self):
        summary = {"income": 0, "expense": 0}
        for r in self.records:
            if r["date"].month == datetime.now().month and r["date"].year == datetime.now().year:
                summary[r["type"]] += r["amount"]
        return summary

    def list_transactions(self):
        return self.records
