# 🐶 NYC Dog Licensing Dashboard

## Project Overview

This project uses real dog licensing data from New York City to explore trends in pet ownership across ZIP codes, time, breed, and dog age. The goal is to identify patterns that can help city agencies or animal organizations plan more effective and better-targeted town halls for dog owners.  
The project includes data cleaning and feature engineering in Python, followed by interactive visualizations built in Tableau.

## Stakeholder Description

**Stakeholder:** New York City Director of Animal Services.

The goal is to help the shareholder connect with dog owners by hosting seasonal town halls, sharing resources, and educating the public about dog licensing and pet care.
These insights connect directly to public health by emphasizing the importance of early dog registration—ideally within the year a puppy is born—to promote timely vaccinations and responsible pet ownership.

## Core Business Question: 
> **Are there patterns in current dog licensing rates that help us plan and promote future town halls more effectively?**
The dashboard answers this question by identifying:
- The lowest and highest rates of dog license issuance across NYC boroughs.
- When licenses are issued, most frequently.
- The average age at which dogs are licensed.
- The dog age distribution  

## Exploratory Data Analysis (EDA) in Python
**Tools Used:** `pandas`, `matplotlib`, `seaborn`, and `plotly`

1. **Data Cleaning**
   Our team started its data cleaning process by making sure each column was in the correct format. This included:
   - Renaming the columns for easy data handling

     <img width="428" height="172" alt="Screenshot 2025-07-16 at 11 51 01 PM" src="https://github.com/user-attachments/assets/e3963b55-e645-4151-a992-03aca0304920" />

   - Removing rows with missing values (e.g., gender, breed, ZIP, date).
   -   We dropped 1810 rows in the `name column`, 21 rows in `Gender`, and 82 in `Licence expire date`. We dropped all these rows because they only represent 1% of all the data in our dataset
   - Checking the data type for each column in the dataset, and next changing the one in the wrong format.
     <img width="539" height="116" alt="Screenshot 2025-07-16 at 11 59 03 PM" src="https://github.com/user-attachments/assets/ab94f70f-1bfa-4cf4-a833-24928f1a4704" />

   - We created a get_borough() function that maps zip codes to boroughs using a custom dictionary. For example, zip codes from 10001–10282 are assigned to Manhattan

     <img width="633" height="434" alt="Screenshot 2025-07-17 at 12 01 55 AM" src="https://github.com/user-attachments/assets/c5f3b98c-63fa-4b07-98fb-cc10449ce89a" />

  2. **Feature Engineering**
     We created three new columns to help find more insights with the data.
     - `DogAgeAtLicense`: Calculated age based on birth year and license date.
     - `IssueMonth` and `IssueYear`: Extracted from license issue date.
       <img width="724" height="116" alt="Screenshot 2025-07-17 at 12 10 22 AM" src="https://github.com/user-attachments/assets/18141a48-e667-42bf-8c3e-b7d5b3dd2fb1" />

     - Filtered out unrealistic ages (<0 or >25). In this large dataset, we have bad data, like: Dogs that appear to be 30 years old, which is not realistic (the average dog lifespan is 10–15 years) So we removed rows where: The age is less than 0 → probably a mistake or The age is more than 25 → extremely rare or likely wrong. 
        <img width="586" height="33" alt="Screenshot 2025-07-17 at 12 16 47 AM" src="https://github.com/user-attachments/assets/c8d533cb-d550-4a9b-89c0-6382d1f88dca" />

  3. **Export**

      - The final cleaned dataset is saved as `final_dataset.csv` for use in Tableau.

        <img width="384" height="33" alt="Screenshot 2025-07-17 at 12 23 40 AM" src="https://github.com/user-attachments/assets/295d0eae-6b37-4035-8248-a9e9719cc3be" />



  5. Tableau Workflow / Visualizations
     
     After importing the cleaned dataset in Tableau, our team was tasked with creating data visualizations with easier access to the information when it comes to              neighborhoods with the highest and lowest Dog licenses issued, and the average ages of dogs for which these licenses are issued, which can help create awareness and       contribute to public health safety. 
         <img width="1428" height="814" alt="image" src="https://github.com/user-attachments/assets/04edacfa-5157-4587-a90d-f0ff5fd2b471" />



      Our dashboard allows users to:
     - Filter by borough and license issue year.
     - View boroughs with the highest and lowest dog license rates.
     - Analyze the average age of dogs at license issuance.
     This Dashboard helps stakeholders identify where outreach and town halls are most needed.

      Find the final interactive dashboard built in Tableau here: [Dashboard](https://public.tableau.com/app/profile/kevin.serrano6220/viz/MODproject_17526900544830/Dashboard1?publish=yes)

## Business Recommendations

Based on our findings, we propose the following:
- Increase licensing in underrepresented boroughs
  - Focus outreach efforts in neighborhoods with the lowest registration rates.
- Promote early licensing (<2 years old)
  Tailor content to **new dog owners and puppies**, since most dogs are under 3 years old.
  - This improves vaccination tracking and contributes to rabies prevention.
- Targeted town halls:
  - Host town halls in areas with low licensing rates and Boroughs with high numbers of older, unlicensed dogs (>5 years old). 

  These efforts support:
  - Stronger community relationships
  - Enhanced public safety
  - Improved animal care and control
  - Higher rates of responsible pet ownership citywide
 
## Project Reflection

**Most Important Insight**:
> Most licenses are issued in the spring and early summer, and a large number of them are for very young dogs. This suggests town halls should focus on new dog owner support and be held between **April and July**, in areas with high registration activity.
> Also, the dashboard reveals the average age of dogs at the time of licensing. Late licensing can lead to missed vaccinations, raising public health risks, particularly related to rabies, a disease that poses a danger to both pets and humans.

**Prioritizing Dashboard Features**
> Given time constraints, we prioritized visualizations that directly aligned with our business question, those that highlighted licensing rates across boroughs, and showcased dog age distribution. These visuals most effectively support our case for targeted town halls and public health campaigns.

**Repo Navigation**
```
├── data/
│   ├── raw/
│         └──NYC_Dog_Licensing_Dataset_20250713.csv
│   └── cleaned/
│        └── final_dataset.csv
│──  notebooks/
│        └── data_cleaning.ipynb
└── README.md

```
**People who collaborated in this project**
- Ibrahima Diallo: [LinkedIn](https://www.linkedin.com/in/ibranova/)
- Kevin Serrano Lopez: [LinkedIn](https://www.linkedin.com/in/kevin-serrano-lopez/)
- Itzel Sanchez: [LinkedIn](https://www.linkedin.com/in/itzel-sanchez-8932b6334/)



## Expanded Analysis (Individual Contribution)

### What the Original Group Project Did

Our team of three analyzed over 700,000 active dog licensing records from the NYC Department of Health and Mental Hygiene (DOHMH) Dog Licensing System, sourced through NYC Open Data. The stakeholder is the New York City Director of Animal Services, and the core business question was: *"Are there patterns in current dog licensing rates that help us plan and promote future town halls more effectively?"*

The group's work included:

- **Data Cleaning (Python):** Renamed columns for consistency, removed ~1% of rows with missing values across name, gender, and license expiration fields, verified and corrected data types, and filtered out unrealistic dog ages (below 0 or above 25 years).
- **Feature Engineering (Python):** Created `DogAgeAtLicense` (calculated from birth year and license issue date), `IssueMonth`, and `IssueYear`. Built a `get_borough()` function that maps ZIP codes to boroughs using a custom dictionary.
- **Tableau Dashboard:** Built an interactive dashboard with borough and year filters showing licensing rates by borough, average dog age at licensing, and age distribution. The dashboard allowed basic filtering but presented all charts on a single flat page without a guided narrative.
- **Export:** Saved the cleaned dataset as `final_dataset.csv` for Tableau.

The original project answered the core question at a surface level; it showed *where* and *when* licenses are issued, but did not provide ZIP-level precision, life-stage segmentation, or public health risk flags.

---

### What I Individually Changed or Added

#### 1. Tableau Calculated Fields (3 New Fields)

- **Season:** Groups `IssueMonth` into Spring (Mar–May), Summer (Jun–Aug), Fall (Sep–Nov), and Winter (Dec–Feb). The stakeholder plans town halls by season, not by individual month; this field maps directly to their planning cycle.
- **Dog Age Category:** Groups `DogAgeAtLicense` into life stages — Puppy (<1 year), Young (1–3 years), Adult (4–7 years), Senior (8+ years). This enables the stakeholder to tailor town hall content by audience rather than treating all dog owners the same.
- **Late Licensing Flag:** Flags dogs licensed at age 2 or older as "Late (2+ years)." This is a new insight the original project never surfaced; late licensing correlates with missed first-year vaccinations, a direct public health concern.

#### 2. LOD (Level of Detail) Expressions (3 Expressions)

- **Borough Avg Dog Age (FIXED):**
  ```
  { FIXED [Borough] : AVG([DogAgeAtLicense]) }
  ```
Calculates the borough-level average dog age regardless of what filters or dimensions are in the view. Used this reference on the ZIP code so individual neighborhoods can be compared against their borough's baseline.

- **ZIP vs Borough Avg Licenses (Nested FIXED):**
  ```
  SUM([Number of Records])
  -
  { FIXED [Borough] : AVG({ FIXED [ZipCode] : SUM([Number of Records]) }) }
  ```
Compares each ZIP code's license count against its own borough's average ZIP-level count. Positive values indicate above-average ZIPs; negative values identify underperforming neighborhoods that are priority targets for outreach.

#### 3. Dashboard Redesign & Tableau Story

- **KPI Summary Cards:** Added 4 KPI cards across the top: Total Licenses, Avg Dog Age at Licensing, Late Licensing Rate, and Boroughs Below City Average.
- **Question-Driven Chart Titles:** Every chart title is phrased as a stakeholder question (e.g., "Which boroughs have the highest rates of late licensing?") rather than a generic label.
- **Definitions Box:** Added a section defining key terms (Late Licensing, Borough Average, Coverage Gap) so non-technical stakeholders can interpret the dashboard independently.
- **Key Findings Section:** Added a findings summary with specific numbers and a recommendation, matching the format used in professional analytical reports.
- **Data Sources:** Added proper attribution to NYC Open Data and the DOHMH Dog Licensing System.
- **Tableau Story (3 Story Points):** Converted the flat single-page dashboard into a guided narrative:
  - *Story Point 1 — "Where Are Dog Owners?"* Borough-level distribution and share of total licenses
  - *Story Point 2 — "When Should We Reach Them?"* Seasonal licensing patterns with Spring/Summer concentration
  - *Story Point 3 — "What Should We Focus On?"* Late licensing rates by borough and ZIP-level underperformers

#### 4. Interactive Elements

- **Dashboard Filter Actions:** Clicking on a borough in the bar chart or map filters all other sheets to that borough, enabling drill-down exploration without manual filter selection.

### Why Each Change Improves the Analysis

| Change | Why It Matters to the Stakeholder |
|--------|-----------------------------------|
| Season field | The Director plans town halls by season, not by month, this field maps directly to their decision cycle |
| Dog Age Category | Enables life-stage-targeted messaging instead of treating all dog owners identically |
| Late Licensing Flag | **New insight:** Surfaces a public health risk (missed vaccinations) the original never identified |
| FIXED LOD (Borough Avg) | Individual ZIPs can now be compared to their own borough's baseline, not just the citywide average |
| Nested FIXED (ZIP vs Borough) | **New capability:** Identifies specific underperforming neighborhoods — moves from 5 borough-level decisions to ZIP-level precision targets |
| EXCLUDE LOD (Borough Share) | Shows proportional contribution even when the dashboard is filtered by year or other dimensions |
| Tableau Story | Transforms a flat dashboard into a guided presentation a non-technical stakeholder can follow in a meeting |
| Dashboard Redesign | Professional dark-themed layout with KPIs, definitions, and key findings creates portfolio consistency and stakeholder readability |

---

### New Insights Created by This Expansion

**1. Late licensing as a public health signal.** The Late Licensing Flag revealed that a significant percentage of NYC dogs are licensed after age 2, meaning they likely missed their first-year vaccinations, including rabies. The original project discussed average age and age distribution, but never flagged late licensing as a risk indicator. The Director can now identify which boroughs have the highest late-licensing rates and prioritize vaccination awareness campaigns in those areas, rather than running generic citywide outreach.

**2. ZIP-level underperformers within boroughs.** The nested FIXED LOD reveals that even within high-licensing boroughs, specific ZIP codes fall well below their borough average. The original project could only recommend "focus on Brooklyn." This expansion identifies the exact ZIP codes within Brooklyn (and every other borough) where licensing rates lag, providing precision targets for town hall locations.

[Updated Tableau Dashboard](https://public.tableau.com/app/profile/ibrahima.diallo4653/viz/Dog_Licence_NYC/therealdashboard)
     







