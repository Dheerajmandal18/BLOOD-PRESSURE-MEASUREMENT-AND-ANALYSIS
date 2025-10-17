# 🩺 Blood Pressure Measurement and Analysis

## 📘 Project Overview
This project is a Python-based GUI application that analyzes blood pressure readings (Systolic and Diastolic) and provides insights such as:
- Blood pressure category (Normal, Elevated, Hypertension, etc.)
- Possible causes
- Precautions
- Cure recommendations

The application uses **Tkinter** for the graphical interface, allowing users to easily input values and view results instantly.

---

## ⚙️ Tools & Libraries
- Python 3.x  
- Tkinter (built-in GUI library)

---

## 💻 Code Implementation

```python
import tkinter as tk
from tkinter import messagebox

class BloodPressureAnalyzer:
    def __init__(self, systolic, diastolic):
        self.systolic = systolic
        self.diastolic = diastolic

    def analyze(self):
        if self.systolic < 120 and self.diastolic < 80:
            return "Normal Blood Pressure"
        elif self.systolic < 130 and self.diastolic < 80:
            return "Elevated Blood Pressure"
        elif self.systolic < 140 and self.diastolic < 90:
            return "Stage 1 Hypertension"
        elif (140 <= self.systolic <= 180) or (90 <= self.diastolic <= 120):
            return "Stage 2 Hypertension"
        elif self.systolic > 180 or self.diastolic > 120:
            return "Hypertensive Crisis"
        else:
            return "Invalid Blood Pressure Reading"

    def get_cause(self):
        return [
            "Genetics",
            "Lack of physical activity",
            "Poor diet",
            "Stress",
            "Sleep apnea",
            "Kidney disease",
            "Adrenal gland disease"
        ]

    def get_precautions(self):
        return [
            "Maintain a healthy weight",
            "Exercise regularly",
            "Eat a balanced diet",
            "Reduce sodium intake",
            "Limit alcohol consumption",
            "Quit smoking",
            "Manage stress"
        ]

    def get_cure(self):
        return [
            "Medications",
            "Lifestyle changes",
            "Dietary changes",
            "Stress management"
        ]

def show_result():
    try:
        systolic = int(systolic_entry.get())
        diastolic = int(diastolic_entry.get())
        analyzer = BloodPressureAnalyzer(systolic, diastolic)
        request = request_var.get()

        if request == "analysis":
            result = analyzer.analyze()
        elif request == "causes":
            result = ", ".join(analyzer.get_cause())
        elif request == "precautions":
            result = ", ".join(analyzer.get_precautions())
        elif request == "cures":
            result = ", ".join(analyzer.get_cure())
        else:
            result = "Invalid choice."

        messagebox.showinfo("Result", result)
    except ValueError:
        messagebox.showerror("Input Error", "Please enter valid numerical values for blood pressure.")

# GUI Setup
root = tk.Tk()
root.title("Blood Pressure Analyzer")

# Labels and Input Fields
tk.Label(root, text="Enter Systolic Blood Pressure:").pack()
systolic_entry = tk.Entry(root)
systolic_entry.pack()

tk.Label(root, text="Enter Diastolic Blood Pressure:").pack()
diastolic_entry = tk.Entry(root)
diastolic_entry.pack()

# Radio Buttons for Options
request_var = tk.StringVar(value="analysis")
tk.Radiobutton(root, text="Analysis", variable=request_var, value="analysis").pack(anchor=tk.W)
tk.Radiobutton(root, text="Causes", variable=request_var, value="causes").pack(anchor=tk.W)
tk.Radiobutton(root, text="Precautions", variable=request_var, value="precautions").pack(anchor=tk.W)
tk.Radiobutton(root, text="Cures", variable=request_var, value="cures").pack(anchor=tk.W)

# Submit Button
submit_button = tk.Button(root, text="Submit", command=show_result)
submit_button.pack()

# Run the App
root.mainloop()


## 📸 Screenshots

### 🩺 Main Interface
![Main Interface](screenshot1.png)

### 📊 Analysis Result
![Analysis Result](screenshot2.png)



