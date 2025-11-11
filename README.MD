# 🧠 CodeBook – Social Network Data Analysis 

## 📋 Overview
Welcome to **CodeBook**, a social media platform for coders — built as part of the **Coders of Delhi Data Science Internship**.  
Your goal in this project is to act as a Data Scientist Intern and use **pure Python (no pandas or NumPy)** to analyze user data, clean it, and build basic recommendation features.

You will:
1. Load and explore a JSON dataset of CodeBook users.  
2. Clean and structure the messy data.  
3. Build a **“People You May Know”** recommendation system.  
4. Build a **“Pages You Might Like”** recommendation engine.

---

## 🗂️ Project Structure
```
📁 CodeBook_Project/
│
├── data.json / codebook_data.json        # Original user + page dataset
├── cleaned_codebook_data.json            # Cleaned dataset after preprocessing
├── 01_Introduction.ipynb                 # Step 1: Load and display data
├── people_you_may_know.py                # Step 2: Friend recommendation logic
├── pages_you_might_like.py               # Step 3: Page recommendation logic
├── README.md                             # Project documentation
└── requirements.txt (optional)
```

---

## ⚙️ Technologies Used
- **Python 3.10+**
- **Jupyter Notebook** or **VS Code**
- JSON module (built-in Python)

---

## 🧩 1. Load and Display the Data

### Task:
Read the dataset and display:
- Each user’s ID, name, friends, and liked pages.
- Available pages on the platform.

### Example JSON:
```json
{
  "users": [
    {"id": 1, "name": "Amit", "friends": [2, 3], "liked_pages": [101]},
    {"id": 2, "name": "Priya", "friends": [1, 4], "liked_pages": [102]},
    {"id": 3, "name": "Rahul", "friends": [1], "liked_pages": [101, 103]},
    {"id": 4, "name": "Sara", "friends": [2], "liked_pages": [104]}
  ],
  "pages": [
    {"id": 101, "name": "Python Developers"},
    {"id": 102, "name": "Data Science Enthusiasts"},
    {"id": 103, "name": "AI & ML Community"},
    {"id": 104, "name": "Web Dev Hub"}
  ]
}
```

### Example Output:
```
Users and their connections:
ID:1 - Amit is friends with: [2, 3] and liked pages are [101]
ID:2 - Priya is friends with: [1, 4] and liked pages are [102]
ID:3 - Rahul is friends with: [1] and liked pages are [101, 103]
ID:4 - Sara is friends with: [2] and liked pages are [104]

Pages Information:
101: Python Developers
102: Data Science Enthusiasts
103: AI & ML Community
104: Web Dev Hub
```

---

## 🧹 2. Clean and Structure the Data

### Goal:
- Remove users with missing names.
- Remove duplicate friend entries.
- Remove inactive users (no friends or liked pages).
- Deduplicate page entries.

### Output:
A clean and consistent JSON file saved as `cleaned_codebook_data.json`.

---

## 👥 3. People You May Know

### Logic:
Suggest users who are **not direct friends** but **share mutual friends**.

Example:
- Amit (1) → Friends: Priya (2), Rahul (3)
- Priya (2) → Friends: Amit (1), Sara (4)

Amit and Sara share Priya as a mutual friend → Suggest **Sara to Amit**.

### Code:
```python
recommendations = find_people_you_may_know(user_id=1, data)
print("People You May Know:", recommendations)
```

### Example Output:
```
People You May Know for User 1: [4]
```

---

## 📄 4. Pages You Might Like

### Logic:
Suggest pages that other users with **similar interests** have liked.  
This is a simple **collaborative filtering** approach.

Example:
- Amit (ID: 1) likes `AI World (102)`
- Priya (ID: 2) also likes `AI World (102)` and `Data Science Daily (103)`  
➡ Recommend **Data Science Daily (103)** to Amit.

### Code:
```python
page_recommendations = find_pages_you_might_like(user_id=1, data)
print(f"Pages You Might Like for User {user_id}: {page_recommendations}")
```

### Example Output:
```
Pages You Might Like for User 1: [103]
```

---

## 🚀 How to Run the Project

### Step 1: Clone or download the project folder
```bash
cd Desktop/CodeBook_Project
```

### Step 2: Activate your environment
```bash
conda activate pydata
```

### Step 3: Run in Jupyter or VS Code
Open `01_Introduction.ipynb` or run the Python files individually.

---

## 🏁 Summary

✅ Load and explore social network data  
✅ Clean and preprocess JSON data  
✅ Build a friend recommendation system  
✅ Implement a page recommendation engine  
✅ Use pure Python for data analysis  

This project demonstrates **core data science thinking** using only **native Python logic** — no libraries, no frameworks — just algorithms and problem-solving!

---

## 💡 Future Improvements
- Implement recommendation weighting (mutual friend count / shared interest score).  
- Add data persistence with a database.  
- Create a Streamlit dashboard for visual exploration.
