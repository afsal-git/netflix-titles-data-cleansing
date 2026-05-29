# Data Analyst Internship - Task 1: Data Cleaning and Preprocessing

## Project Objective
[cite_start]The objective of this task is to clean and prepare a highly corrupted, raw dataset of Netflix titles[cite: 5, 17]. [cite_start]This workflow identifies and resolves typical real-world data anomalies—such as missing values, duplicate entries, structural format inconsistencies, and incorrect data types [cite: 5, 20][cite_start]—ensuring the dataset is fully structured and prepared for analytical processing or modeling[cite: 24].

---

## Technical Toolset Used
* **Environment:** Visual Studio Code (VS Code)
* **Language:** Python
* **Libraries:** Pandas, NumPy

---

## Comprehensive Summary of Changes

The raw dataset (`messy_netflix_titles.csv`) was systematically cleaned using Python Pandas through the following operations:

### 1. Column Header Standardization
* [cite_start]Removed all leading and trailing whitespaces from the raw headers[cite: 11].
* [cite_start]Standardized all column labels to uniform lowercase syntax[cite: 11].
* [cite_start]Replaced internal whitespace blocks with clean underscores (e.g., `SHOW ID` and `DATE_ADDED ` were converted to `show_id` and `date_added`)[cite: 11].

### 2. Record Deduplication
* Handled structural data mutations where duplicated rows had minor text variances.
* [cite_start]Utilized subset structural filtering (`subset=['show_id']`) to evaluate unique identifiers[cite: 9].
* [cite_start]Removed all duplicate records, maintaining only the first valid iteration and successfully reducing rows[cite: 9].

### 3. Text and Categorical Normalization
* **Type Column:** Applied `.str.strip().str.title()` mechanics to eliminate conflicting categorizations like `movie`, `MOVIE`, and ` Movie `, grouping them seamlessly into `Movie` or `TV Show`.
* **Country Column:** Built an architectural standardization mapping structure to capture regional input anomalies (e.g., converting `US`, `USA`, `united states`, and trailing whitespace records all back to a unified `United States`).

### 4. Mixed-Format Parsing (Date Fields)
* [cite_start]Resolved highly chaotic structural date variances (e.g., mixing `dd-mm-yyyy`, `yyyy/mm/dd`, `mm/dd/yyyy`, and text strings like `September 24, 2021`)[cite: 10, 31].
* [cite_start]Leveraged `pd.to_datetime()` utilizing `errors='coerce'` and `format='mixed'` flags to parse variations accurately[cite: 8].

### 5. Type Casting and Numerical Extraction
* [cite_start]Cleared the `release_year` string variables of literal noise text (e.g., removing `Year:` prefixes)[cite: 12].
* [cite_start]Extracted and cast numeric elements from corrupted strings directly into explicit integer types (`.astype(int)`)[cite: 12].

### 6. Missing Value (Null) Imputation Strategy
* [cite_start]Imputed text placeholders (`'Unknown Director'`, `'Unknown Cast'`, `'Unknown Country'`) into sparse categorical blocks to maintain dataset structure without dropping rows[cite: 8].
* Imputed numerical entries in the release year field using the calculated sample **Median Year (2017)**.
* Standardized unparseable or empty date records cleanly as `'Not Available'`.
* **Result:** Achieved a perfect **0% Missing Values** metric across the entire dataset.

---

## Project Repository Files
* **`messy_netflix_titles.csv`**: The initial, corrupted raw source data containing formatting issues, duplicates, and missing indices.
* **`cleaned_netflix_titles.csv`**: The final, processed structural dataset with pristine layout schemas and zero validation errors.
* **`data_cleaning.ipynb`**: Interactive Jupyter Notebook outlining the precise line-by-line programmatic execution steps.

---

### Verification and Quality Metrics
* **Initial Dataset Size:** 8957 Rows, 12 Columns
* **Final Verified Clean Dataset Size:** 8807 Rows, 12 Columns
* **Final Missing Value Count:** 0
