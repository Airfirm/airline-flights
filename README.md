# airline-flights

## Data Analytics Capstone: Step-by-Step Project Setup, Data Collection, and Exploratory Data Analysis

**Project:** Predictive Analytics for Airline Flight Delays
**Data Source:** U.S. Department of Transportation — Bureau of Transportation Statistics (BTS)
**Development Environment:** Visual Studio Code (VS Code)
**Programming Language:** Python
**Analysis Environment:** Jupyter Notebook
**Version Control:** Git and GitHub
**Repository:** `airline-flights`

For your capstone, I recommend building an end-to-end Python analytics project that begins with collecting historical airline flight data, progresses through exploratory data analysis (EDA), and eventually develops machine learning models to predict flight delays.

We will organize the process into eight stages.

## Stage 1: Determine How Much Historical Data to Collect

Before cloning your repository, let's establish the dataset period.

### My recommendation: Start with 12 months of data from 2025

The Bureau of Transportation Statistics provides historical domestic flight performance data, including scheduled flights, actual arrival and departure times, cancellations, and delays. The records are available by month. ([Transtats][1])

I recommend the following:

| Option                | Data Period                | Purpose                                                 | Recommendation  |
| --------------------- | -------------------------- | ------------------------------------------------------- | --------------- |
| Initial testing       | January 2025               | Verify data collection and Python processing            | Start here      |
| Initial EDA           | January–March 2025         | Examine data quality and early trends                   | Second step     |
| Full capstone dataset | January–December 2025      | Capture seasonal patterns and develop models            | **Recommended** |
| Expanded analysis     | January 2024–December 2025 | Compare annual patterns and improve temporal validation | Optional        |

### Why use a full year?

A complete year allows you to investigate:

1. **Seasonality:** Do airline delays increase during particular months?
2. **Airline performance:** Which airlines experience higher delay rates?
3. **Airport performance:** Which airports experience frequent delays?
4. **Scheduling patterns:** Are morning or evening flights more likely to be delayed?
5. **Predictive modeling:** Can historical flight characteristics predict arrival delays?

A full calendar year is a manageable starting point for a graduate capstone, although the records may still occupy substantial disk space and memory.

**My recommendation:** Begin with January 2025, confirm that your data collection and notebook work, and then extend to all 12 months of 2025.

For predictive modeling, we can use a chronological split, such as January–September for training, October–November for validation, and December for final testing.

If your computer handles the data comfortably, adding 2024 later would provide a stronger basis for evaluating predictions across different years.

---

## Stage 2: Clone Your GitHub Repository into VS Code

You already have a remote GitHub repository named:

`airline-flights`

We want to create a local copy on your Windows 11 computer.

## Step 1: Get the repository URL

1. Open GitHub in your browser.
2. Sign in to your account.
3. Navigate to your repository named `airline-flights`.
4. Select the green **Code** button.
5. Under HTTPS, copy the repository URL.

It should resemble:

```text
https://github.com/YOUR-USERNAME/airline-flights.git
```

Replace `YOUR-USERNAME` with your actual GitHub username.

## Step 2: Clone using VS Code

Open Visual Studio Code.

1. Press `Ctrl + Shift + P`.
2. Type `Git: Clone`.
3. Select **Git: Clone**.
4. Paste the repository URL.
5. Press Enter.
6. Choose the local folder where you want the repository stored.
7. Select **Open** when VS Code asks whether to open the cloned repository.

For example, you might clone into your Documents folder:

```text
Documents/
    airline-flights/
```

VS Code supports cloning repositories through its Command Palette and automatically configures the remote repository as `origin`. ([Visual Studio Code][2])

### Alternative: Clone using the terminal

Open the VS Code terminal:
**Terminal → New Terminal**

Run:

```powershell
cd "$HOME\Documents"
git clone https://github.com/YOUR-USERNAME/airline-flights.git
cd airline-flights
code .
```

Use your actual repository URL.

If your repository contains existing files, cloning preserves those files and the repository's Git history.

### Step 3: Verify the connection

In the VS Code terminal, run:

```powershell
git remote -v
```

You should see something resembling:

```text
origin  https://github.com/YOUR-USERNAME/airline-flights.git (fetch)
origin  https://github.com/YOUR-USERNAME/airline-flights.git (push)
```

This confirms that your local project is connected to your remote GitHub repository.

---

## Stage 3: Set Up Python and Jupyter Notebook

Next, let's configure the Python environment.

## Step 1: Install VS Code extensions

In VS Code, select the **Extensions** icon or press:

`Ctrl + Shift + X`

Search for and install these Microsoft extensions:

| Extension | Purpose                           |
| --------- | --------------------------------- |
| Python    | Python development and debugging  |
| Jupyter   | Run interactive Jupyter notebooks |
| Pylance   | Python language support           |

Ensure Python itself is installed on your computer.

Open your VS Code terminal and run:

```powershell
python --version
```

You should see a Python version number.

If Python isn't recognized, it needs to be installed or configured before continuing.

## Step 2: Create a virtual environment

Inside your cloned `airline-flights` repository, open the terminal and execute:

```powershell
python -m venv .venv
```

This creates a project-specific Python environment.

Activate it using:

```powershell
.\.venv\Scripts\Activate.ps1
```

Your terminal should now begin with:

```text
(.venv)
```

If PowerShell blocks activation, you can avoid changing its execution policy by using the environment's Python executable directly:

```powershell
.\.venv\Scripts\python.exe --version
```

## Step 3: Install the necessary Python libraries

With your virtual environment activated, execute:

```powershell
python -m pip install --upgrade pip
```

Then:

```powershell
python -m pip install pandas numpy matplotlib seaborn scikit-learn jupyter ipykernel pyarrow
```

These packages will support:

| Library      | Purpose                              |
| ------------ | ------------------------------------ |
| pandas       | Data loading, cleaning, and analysis |
| numpy        | Numerical calculations               |
| matplotlib   | Data visualizations                  |
| seaborn      | Statistical visualizations           |
| scikit-learn | Machine learning                     |
| jupyter      | Interactive notebooks                |
| ipykernel    | Jupyter Python kernel                |
| pyarrow      | Efficient Parquet file storage       |

Finally, create a dependency file:

```powershell
python -m pip freeze > requirements.txt
```

This allows you or your instructor to reproduce the Python environment later.

---

## Stage 4: Organize Your Project Repository

A well-organized repository is particularly important for your capstone because it demonstrates professional development practices.

I recommend the following structure:

```text
airline-flights/
│
├── data/
│   ├── raw/
│   ├── processed/
│   └── external/
│
├── notebooks/
│   ├── 01_data_collection.ipynb
│   ├── 02_data_cleaning.ipynb
│   ├── 03_exploratory_analysis.ipynb
│   └── 04_predictive_modeling.ipynb
│
├── src/
│   ├── data_preparation.py
│   └── modeling.py
│
├── reports/
│   ├── figures/
│   └── final_report/
│
├── README.md
├── requirements.txt
└── .gitignore
```

### What each folder does

**data/raw:** Original downloaded BTS datasets.

**data/processed:** Cleaned datasets ready for analysis.

**data/external:** Supplementary datasets, if needed.

**notebooks:** Jupyter notebooks documenting each phase.

**src:** Reusable Python scripts.

**reports/figures:** Charts generated during your analysis.

**reports/final_report:** Your completed project report and supporting documentation.

### Step 1: Create your folders

In the VS Code terminal, execute:

```powershell
New-Item -ItemType Directory -Force -Path `
data/raw, `
data/processed, `
data/external, `
notebooks, `
src, `
reports/figures, `
reports/final_report
```

### Step 2: Create a `.gitignore` file

Large datasets should generally not be committed directly to GitHub.

Create a file named:

`.gitignore`

Add:

```gitignore
# Python environment
.venv/
__pycache__/
*.pyc

# Jupyter checkpoints
.ipynb_checkpoints/

# Raw and processed datasets
data/raw/*
data/processed/*
data/external/*

# Keep data directories
!data/raw/.gitkeep
!data/processed/.gitkeep
!data/external/.gitkeep

# Local configuration
.env

# Operating system files
.DS_Store
Thumbs.db
```

This keeps your repository focused on code, documentation, notebooks, and analytical results rather than large files.

For reproducibility, your README can document exactly where the BTS files were obtained.

---

## Stage 5: Download Flight Data from TranStats

Now we can begin collecting the actual dataset.

## Step 1: Open the BTS data download page

Use the official TranStats selective download page:

[BTS Reporting Carrier On-Time Performance Dataset](https://transtats.bts.gov/DL_SelectFields.aspx?QO_fu146_anzr=b0-gvzr&gnoyr_VQ=FGJ&utm_source=chatgpt.com)

The page contains dropdown menus for year, period, and geography, along with checkboxes for individual data fields. ([Transtats][3])

## Step 2: Select the data period

For your first download, use:

| Setting          | Selection |
| ---------------- | --------- |
| Filter Geography | All       |
| Filter Year      | 2025      |
| Filter Period    | January   |

This will let you test your entire processing workflow with one month of data.

## Step 3: Select your data attributes

Rather than selecting all available fields, I recommend starting with approximately 24 useful variables.

### A. Flight identification

| Field                           | Description     |
| ------------------------------- | --------------- |
| FlightDate                      | Date of flight  |
| Year                            | Flight year     |
| Month                           | Flight month    |
| DayOfWeek                       | Day of week     |
| Reporting_Airline               | Airline carrier |
| Flight_Number_Reporting_Airline | Flight number   |

### B. Airport information

| Field    | Description         |
| -------- | ------------------- |
| Origin   | Origin airport      |
| Dest     | Destination airport |
| Distance | Flight distance     |

### C. Flight schedule and performance

| Field      | Description                         |
| ---------- | ----------------------------------- |
| CRSDepTime | Scheduled departure time            |
| DepTime    | Actual departure time               |
| DepDelay   | Departure delay in minutes          |
| CRSArrTime | Scheduled arrival time              |
| ArrTime    | Actual arrival time                 |
| ArrDelay   | Arrival delay in minutes            |
| ArrDel15   | Arrival delay of 15 minutes or more |

### D. Cancellation and diversion information

| Field            | Description            |
| ---------------- | ---------------------- |
| Cancelled        | Cancellation indicator |
| CancellationCode | Cancellation reason    |
| Diverted         | Diversion indicator    |

### E. Delay causes

| Field             | Description                              |
| ----------------- | ---------------------------------------- |
| CarrierDelay      | Airline-related delay                    |
| WeatherDelay      | Weather-related delay                    |
| NASDelay          | National Airspace System delay           |
| SecurityDelay     | Security-related delay                   |
| LateAircraftDelay | Delay caused by a late-arriving aircraft |

**Important:** We will download actual delay information for descriptive analysis, but these variables must not automatically become predictive model inputs.

If the goal is to predict delays before departure, the model cannot use outcomes that occur after departure.

## Step 4: Download January 2025

After selecting the fields:

1. Locate the **Download** button.
2. Click Download.
3. Save the resulting file.
4. Extract it if the download is compressed.
5. Move the CSV file into your repository's `data/raw` folder.

TranStats' official instructions confirm that its selective downloads provide comma-delimited files based on selected periods and fields. ([Transtats][4])

For consistency, rename the extracted CSV:

```text
flights_2025_01.csv
```

Your repository should now resemble:

```text
airline-flights/
│
├── data/
│   └── raw/
│       └── flights_2025_01.csv
```

### What about the remaining months?

After confirming that January loads correctly, repeat the download process for February through December.

Use consistent filenames:

```text
flights_2025_01.csv
flights_2025_02.csv
flights_2025_03.csv
flights_2025_04.csv
flights_2025_05.csv
flights_2025_06.csv
flights_2025_07.csv
flights_2025_08.csv
flights_2025_09.csv
flights_2025_10.csv
flights_2025_11.csv
flights_2025_12.csv
```

**Important:** Select the same columns for every download so you can combine the files without unexpected schema differences.

---

## Stage 6: Create Your First Jupyter Notebook

Now we will begin working with the downloaded data in VS Code.

## Step 1: Create a notebook

In VS Code:

1. Open the `notebooks` folder.
2. Right-click and select **New File**.
3. Name the file:
4. Open the notebook.
5. Click **Select Kernel** in the upper-right corner.
6. Select the Python interpreter inside your `.venv` environment.

```text
01_data_collection.ipynb
```

You can now write and execute Python code directly in VS Code.

## Step 2: Import the Python libraries

In the first code cell, enter:

```python
import pandas as pd
import numpy as np
from pathlib import Path

print("Pandas version:", pd.__version__)
```

Run the cell by clicking the play button.

If it executes without errors, your notebook environment is working.

## Step 3: Locate your repository and dataset

Because your notebook is inside the `notebooks` folder, we should locate the project root reliably.

Enter:

```python
from pathlib import Path

cwd = Path.cwd()

if (cwd / "data").exists():
    project_root = cwd
elif (cwd.parent / "data").exists():
    project_root = cwd.parent
else:
    raise FileNotFoundError(
        "Cannot locate the project data folder."
    )

data_path = project_root / "data" / "raw"

print("Project root:", project_root)
print("Dataset folder:", data_path)
```

This accommodates VS Code configurations that run the notebook from either the repository root or the notebook folder.

## Step 4: Load January 2025

Create another code cell:

```python
file_path = data_path / "flights_2025_01.csv"

df = pd.read_csv(
    file_path,
    low_memory=False
)

print("Rows:", df.shape[0])
print("Columns:", df.shape[1])

df.head()
```

If everything works, Jupyter will display the first five flight records.

**Note:** The filename must match the actual file you downloaded.

## Step 5: Inspect your dataset

Run:

```python
df.info()
```

This displays:

* Column names
* Data types
* Non-null values
* Memory usage

Next:

```python
df.columns.tolist()
```

This will show all available data fields.

Finally:

```python
df.describe()
```

This displays descriptive statistics for your numerical variables.

At this point, you have successfully imported the BTS dataset into Python.

---

## Stage 7: Begin Exploratory Data Analysis (EDA)

This is where your capstone starts moving from data collection into meaningful analysis.

I recommend creating a second notebook:

```text
03_exploratory_analysis.ipynb
```

However, initially you can run the following code in your first notebook to inspect the dataset before creating a separate cleaning workflow.

## Step 1: Examine missing values

Run:

```python
missing_values = df.isnull().sum()

missing_percentage = (
    df.isnull().mean() * 100
).round(2)

missing_summary = pd.DataFrame({
    "Missing Values": missing_values,
    "Missing Percentage": missing_percentage
})

missing_summary.sort_values(
    "Missing Percentage",
    ascending=False
).head(20)
```

This identifies the columns with the highest percentages of missing data.

### Why is this important?

Some flights are cancelled or diverted.

These flights may not have a valid arrival delay.

Additionally, delay-cause fields are not necessarily populated for flights that arrived on time.

Consequently, **missing values do not always indicate bad data**.

The BTS reporting instructions distinguish between completed, cancelled, and diverted flights and explain how delay-cause reporting works. ([Bureau of Transportation Statistics][5])

We should investigate missing values before deciding whether to remove records.

---

## Step 2: Examine cancelled and diverted flights

Run:

```python
df["Cancelled"].value_counts(dropna=False)
```

Then:

```python
df["Diverted"].value_counts(dropna=False)
```

This will tell us how many records represent completed, cancelled, and diverted flights.

For the initial predictive modeling dataset, we will focus on completed flights with valid arrival-delay outcomes.

However, we can still analyze cancellation and diversion patterns separately.

---

## Step 3: Prepare an initial EDA dataset

Create a working copy.

```python
eda_df = df.copy()

eda_df["FlightDate"] = pd.to_datetime(
    eda_df["FlightDate"],
    errors="coerce"
)

eda_df = eda_df[
    (eda_df["Cancelled"] == 0) &
    (eda_df["Diverted"] == 0)
].copy()

eda_df = eda_df.dropna(
    subset=["FlightDate", "ArrDel15"]
)

eda_df["ArrDel15"] = (
    eda_df["ArrDel15"].astype(int)
)

print("Records available for analysis:")
print(len(eda_df))
```

We now have an initial dataset containing completed, non-diverted flights with valid target values.

Keep your original `df` unchanged.

---

## Step 4: Calculate the overall arrival delay rate

This is one of the first major performance indicators for your project.

```python
total_flights = len(eda_df)

delayed_flights = (
    eda_df["ArrDel15"] == 1
).sum()

delay_rate = (
    delayed_flights / total_flights * 100
    if total_flights else 0
)

print(f"Total Flights: {total_flights:,}")
print(f"Delayed Flights: {delayed_flights:,}")
print(f"Arrival Delay Rate: {delay_rate:.2f}%")
```

This calculates the percentage of analyzed flights arriving at least 15 minutes late.

**Interpretation:** A higher percentage indicates a greater proportion of delayed flights.

The actual result will depend on your downloaded dataset.

---

## Stage 8: Create Your First Data Visualizations

Now we can produce charts that directly support your project objectives.

I suggest starting with four charts.

## Visualization 1: Arrival Delay Distribution

**Question:** What percentage of flights arrive on time versus delayed?

```python
import matplotlib.pyplot as plt
import seaborn as sns

delay_counts = (
    eda_df["ArrDel15"]
    .value_counts()
    .reindex([0, 1], fill_value=0)
)

plt.figure(figsize=(8, 5))

sns.barplot(
    x=["Not Delayed", "Delayed"],
    y=delay_counts.values
)

plt.title("Flight Arrival Delay Distribution")
plt.xlabel("Arrival Status")
plt.ylabel("Number of Flights")

plt.tight_layout()
plt.show()
```

This chart provides an overview of the frequency of significant arrival delays.

---

## Visualization 2: Delay Rates by Airline

**Question:** Which airlines experience higher percentages of delayed flights?

```python
airline_delays = (
    eda_df.groupby("Reporting_Airline")
    .agg(
        TotalFlights=("ArrDel15", "size"),
        DelayRate=("ArrDel15", "mean")
    )
    .reset_index()
)

airline_delays["DelayRate"] *= 100

airline_delays = airline_delays.sort_values(
    "DelayRate",
    ascending=False
)

plt.figure(figsize=(12, 6))

sns.barplot(
    data=airline_delays,
    x="Reporting_Airline",
    y="DelayRate"
)

plt.title("Arrival Delay Rate by Airline")
plt.xlabel("Airline")
plt.ylabel("Delayed Flights (%)")
plt.xticks(rotation=45)

plt.tight_layout()
plt.show()
```

**Why this matters:** Comparing delay percentages instead of raw delay counts helps account for differences in flight volumes between airlines.

Later, we can add minimum flight-count thresholds to prevent small groups from producing misleading comparisons.

---

## Visualization 3: Delays by Day of the Week

**Question:** Are certain days associated with higher flight delay rates?

```python
weekday_delays = (
    eda_df.groupby("DayOfWeek")["ArrDel15"]
    .mean()
    .mul(100)
    .reindex(range(1, 8))
)

weekday_names = [
    "Mon", "Tue", "Wed", "Thu",
    "Fri", "Sat", "Sun"
]

plt.figure(figsize=(10, 5))

sns.barplot(
    x=weekday_names,
    y=weekday_delays.values
)

plt.title("Arrival Delay Rate by Day of Week")
plt.xlabel("Day of Week")
plt.ylabel("Delayed Flights (%)")

plt.tight_layout()
plt.show()
```

This visualization may reveal scheduling patterns relevant to operational planning.

---

## Visualization 4: Scheduled Departure Time and Delays

**Question:** Does scheduled departure time have a relationship with arrival delays?

For this analysis, we will use `CRSDepTime`.

It represents the scheduled departure time, generally recorded as HHMM in local time.

We will convert that value into a departure-hour category.

```python
eda_df["DepartureHour"] = (
    pd.to_numeric(
        eda_df["CRSDepTime"],
        errors="coerce"
    ) // 100
)

# Represent 2400 (midnight) as hour 0
eda_df["DepartureHour"] = (
    eda_df["DepartureHour"].replace(24, 0)
)

eda_df.loc[
    ~eda_df["DepartureHour"].between(0, 23),
    "DepartureHour"
] = np.nan

hourly_delays = (
    eda_df.groupby("DepartureHour")["ArrDel15"]
    .mean()
    .mul(100)
    .reindex(range(24))
)

plt.figure(figsize=(12, 5))

sns.lineplot(
    x=hourly_delays.index,
    y=hourly_delays.values,
    marker="o"
)

plt.title("Arrival Delay Rate by Scheduled Departure Hour")
plt.xlabel("Scheduled Departure Hour")
plt.ylabel("Delayed Flights (%)")
plt.xticks(range(0, 24, 2))

plt.tight_layout()
plt.show()
```

This can help identify whether flights scheduled later in the day have different delay patterns than earlier flights.

---

## Stage 9: Save Your Initial Results

After completing the first round of analysis, save your initial working dataset.

```python
output_path = (
    project_root /
    "data" /
    "processed" /
    "flights_2025_01_eda.parquet"
)

eda_df.to_parquet(
    output_path,
    index=False
)

print("Dataset saved successfully.")
```

I recommend Parquet for processed datasets because it preserves data types and is generally more efficient than CSV for repeated analytical work.

Your original BTS CSV should remain unchanged in `data/raw`.

You can also save a chart:

```python
plt.figure(figsize=(10, 5))

sns.barplot(
    x=weekday_names,
    y=weekday_delays.values
)

plt.title("Arrival Delay Rate by Day of Week")
plt.xlabel("Day of Week")
plt.ylabel("Delayed Flights (%)")

plt.tight_layout()

plt.savefig(
    project_root /
    "reports" /
    "figures" /
    "weekday_delays.png",
    dpi=300,
    bbox_inches="tight"
)

plt.show()
```

This creates a figure you can eventually include in your capstone report.

---

## Stage 10: Commit and Push Your Work to GitHub

Once your notebook runs successfully, you can save your progress to the remote repository.

Open the VS Code terminal.

First:

```powershell
git status
```

Review the changed files.

Next:

```powershell
git add .
```

Commit:

```powershell
git commit -m "Set up project and complete initial flight data exploration"
```

Push your work:

```powershell
git push origin HEAD
```

This pushes your current branch to its corresponding branch on GitHub when configured appropriately.

If Git reports that the branch has no upstream, use:

```powershell
git push -u origin HEAD
```

Your repository should now contain your project structure, notebook, dependency file, and any committed figures or documentation.

The raw BTS data will remain on your computer because we excluded it through `.gitignore`.

---

## Recommended Capstone Implementation Plan

Here is the workflow I recommend following throughout your project.

| Phase | Activity                                     | Expected Deliverable                              |
| ----- | -------------------------------------------- | ------------------------------------------------- |
| 1     | Clone GitHub repository and configure Python | Working VS Code project                           |
| 2     | Download January 2025                        | Initial BTS CSV                                   |
| 3     | Validate attributes and data types           | Dataset inspection notebook                       |
| 4     | Download remaining 2025 months               | Complete historical dataset                       |
| 5     | Clean and combine the records                | Processed dataset                                 |
| 6     | Conduct exploratory data analysis            | Summary statistics and visualizations             |
| 7     | Develop predictive classification models     | Logistic Regression, Decision Tree, Random Forest |
| 8     | Evaluate model performance                   | Model comparison and evaluation metrics           |
| 9     | Develop a dashboard                          | Tableau or Power BI dashboard                     |
| 10    | Complete project documentation               | Final capstone report                             |

## Important Considerations Before Modeling

There are three technical decisions that will significantly affect your final results.

**First, avoid data leakage.** Because you intend to predict delays before departure, predictor variables must be available before the flight departs. For example, `ArrDelay`, `ArrTime`, and `CarrierDelay` are useful for EDA but should not be used as inputs for a predeparture prediction model.

**Second, validate chronologically.** Randomly distributing records from the same period into training and testing sets can make it harder to evaluate performance on genuinely future flights. A chronological split better represents your intended application.

**Third, evaluate more than accuracy.** If most flights arrive without a significant delay, a model could achieve apparently good accuracy simply by frequently predicting that flights will not be delayed. Precision, recall, F1-score, ROC-AUC, and confusion matrices will provide a more complete picture. Comparing against a simple baseline will also help determine whether machine learning adds value.

---

## What I Recommend You Complete First

For your immediate next session in VS Code, focus on these five tasks:

1. Clone the `airline-flights` repository.
2. Create and activate your Python virtual environment.
3. Install the required Python libraries and create the notebook.
4. Download **January 2025** from BTS with the selected attributes.
5. Import the CSV and run `df.head()`, `df.info()`, and the missing-value analysis.

**Your first milestone is a working Jupyter Notebook that successfully loads real BTS flight records and produces an initial data-quality summary.**

After that, the next major milestone will be combining all 12 months, validating the data, and developing a comprehensive EDA notebook that examines seasonal patterns, airport performance, airline performance, delay causes, and scheduled departure times.

This will give your capstone a reproducible data pipeline and a strong foundation for developing your flight-delay prediction models.

[1]: https://www.transtats.bts.gov/TableInfo.asp?QO_fu146_anzr=b0-gvzr&gnoyr_VQ=FGJ&utm_source=chatgpt.com "OST_R | BTS | Transtats Data Table"
[2]: https://code.visualstudio.com/docs/sourcecontrol/repos-remotes?utm_source=chatgpt.com "Working with repositories and remotes"
[3]: https://transtats.bts.gov/DL_SelectFields.aspx?QO_fu146_anzr=b0-gvzr&gnoyr_VQ=FGJ&utm_source=chatgpt.com "Download page"
[4]: https://transtats.bts.gov/showHelp.asp?utm_source=chatgpt.com "Help"
[5]: https://www.bts.gov/explore-topics-and-geography/modes/aviation/number-39-technical-directive-reporting-time?utm_source=chatgpt.com "Number 39: Technical Directive Reporting On Time Performance 2025 | Bureau of Transportation Statistics"
