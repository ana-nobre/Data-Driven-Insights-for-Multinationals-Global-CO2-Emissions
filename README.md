# 🌍 Data Insights: CO₂ Emissions by Country, Region, and Sector   

## Introduction    

This project presents a consultancy case at a **country-level granularity**. The analysis highlights how emissions differ across nations and regions, helping multinational companies, governments, and international organizations prioritize policies, investments, and ESG strategies.  

Climate change is not only an environmental challenge but also a strategic business and policy concern. Carbon dioxide (CO₂) emissions, as the main driver of global warming (IPCC, 2021), directly impact economic stability, regulatory frameworks, corporate sustainability strategies, and long-term investment decisions.  

This project develops an **interactive dashboard in Tableau/Power BI** to track and analyze CO₂ emissions by country, region, and sector. The goal is to provide decision-makers, analysts, and stakeholders with clear insights into emission trends, sectoral contributions, and global disparities.  

By leveraging this analysis, organizations and policymakers can benchmark performance, identify high-impact sectors, evaluate regional progress, and align strategies with global sustainability goals (e.g., Net Zero targets and ESG reporting).  

> **Note:** While CO₂ is the focus of this project, it is important to recognize that other greenhouse gases — such as methane (CH₄) and nitrous oxide (N₂O) — also play a critical role in global warming. Methane, for example, has been linked not only to climate impact but also to adverse public health effects, including an increased risk of cancer. Additionally, the energy transition is a long-term process, and depending on the industry under analysis, other gases might be more relevant to monitor. In this dataset, CO₂ was chosen, but future studies could fully leverage the GHG data in the database to expand the scope.

The dataset used comes from Kaggle: 
Dangi, S. (2024). *CO₂ Emissions across Countries, Regions and Sectors*. Kaggle. 

Available at: 
https://www.kaggle.com/datasets/shreyanshdangi/co-emissions-across-countries-regions-and-sectors  

**Ana Nobre – Project Lead and Scrum Master**  

GitHub Profile:  
https://github.com/ana-nobre

GitHub @CO₂ Emissions Insights Kaban's link:  
https://github.com/users/BiancaGemarR/projects/1  

Tableau public's project:  
https://public.tableau.com/views/DataInsightsCOEmissionsbyCountryRegionandSector/Dashboard-1Logarithmic?:language=en-GB&:sid=&:redirect=auth&:display_count=n&:origin=viz_share_link  

---

## 🎯 Project Objectives  
- Provide a clear and visual overview of CO₂ emissions at global and regional levels.  
- Identify **key sectors** responsible for the majority of emissions.  
- Detect **reduction patterns** in specific countries and regions.  
- Strengthen skills in **data analysis, advanced visualization, and data storytelling**.  
- Communicate findings in an **executive and decision-oriented** manner.  

---

## 📊 Key Analytical Questions  

This project aims to provide answers to the following research questions:  

1. **Which countries and continents contribute the most CO₂ emissions?**  
2. **How are CO₂ emissions distributed across continents and regions?**  
3. **What is the relationship between CO₂ emissions and primary energy consumption across time and regions?**  
4. **How does Spain’s CO₂ emissions trend compare with other regions?**  
5. **What is the relationship between CO₂ emissions and population, both at country and continental level?**  
6. **Which countries are outliers when comparing total CO₂ emissions vs per capita emissions?**  

> Note: Since the focus of the analysis is on industry and energy consumption, we selected the co2 column, which excludes land-use change (LUC) emissions, prioritizing only those directly linked to economic and industrial activity.

---

## 🛠️ Methodology  

**1. Exploratory Data Analysis (EDA)**  
- Reviewed data quality, missing values, and outliers.  
- Identified critical metrics: total, per capita, accumulated, and sectoral emissions.  

### 🔎 Data Cleaning – Python Applied Examples  

```python
# Rename columns: snake_case -> space separated (only where '_' exists)
df_filtrado.columns = [
    col.replace('_', ' ') if '_' in col else col
    for col in df_filtrado.columns]

# Map country -> continent
# diccionario_continentes = {'Spain': 'Europe', 'Qatar': 'Asia', ...}
df_filtrado['Continent'] = df_filtrado['Name'].map(diccionario_continentes)

# Consistent country naming
df_filtrado = df_filtrado.rename(columns={'Name': 'country'})

# Export cleaned data
df_filtrado.to_csv('data_clean_country.csv', index=False)
```

*During this process, we realized that some countries appeared with different column names depending on the source (e.g., territory, regional grouping, developed vs. developing nations). This forced us to clean and standardize them using Python and create two separate CSVs — one for countries and another for regions and economic groups — a small but important step to ensure consistency.*  

**2. Data Transformation and Preparation**  
- Cleaned and normalized the dataset.  
- Created new calculated metrics.  

**3. Visualization Design**  
- Time series to track CO₂ evolution over time.  
- Bar and line charts to compare **average emissions per continent** and their **long-term trends**.  
- Scenario analysis dashboards (e.g., *“What if we exclude China?”*) to show the disproportionate impact of large emitters.  
- Scatter plots *Population vs CO₂* (linear and logarithmic scales) with continental trendlines.  
- Bubble charts to visualize **Top 10 emitters**, **Top 10 most populated countries**, and **Top 10 emitters per capita**.  
- Dynamic filters (continent, country, year) for interactive exploration.  

**4. Interactive Dashboard Creation**  
- Minimalist design with accessible color palette.  
- Included **key KPIs**: global emissions since 2001, top 5 emitting countries, % by sector.  

**5. Scrum Methodology Applied**  
- Work divided into **2 weekly sprints** with clearly defined goals.  
- **Daily stand-ups** to track progress and remove blockers.  
- **Sprint reviews** at the end of each iteration, presenting the dashboard and gathering feedback.  
- **Sprint retrospectives** to continuously improve teamwork and workflow.  
- Agile task management tools were used to ensure transparency and accountability.  

---

## 📌 Key Insights  

### Tableau – Population vs CO₂  

![Tableau Dashboard](./Tableau-Dashboards/(1)dashboard-tableau.png)  

*This dashboard compares **population vs CO₂ emissions** in two perspectives: a standard scatter plot and a **logarithmic scale** version. The logarithmic view makes it possible to visualize both very large and very small emitters, while trendlines per continent help to understand expected emission levels relative to population.*  

- **How to read the logarithmic view:**  
  The vertical axis increases exponentially (2 → 5 → 10 → 20), so distances between points are not linear. What matters is whether a country lies **above or below** its continental trendline.  
  - Above the line → emitting **more CO₂ than expected** for its population size.  
  - Below the line → emitting **less CO₂ than expected**.  

- **Examples:**  
  - **India** (1.4B people, 3,062 MtCO₂) is **below** Asia’s trendline → very large population but relatively low per capita emissions.  
  - **Qatar** (3M people, 116 MtCO₂) is **well above** the trendline → small population but extremely high per capita emissions.  
  - **China and the US** are **outliers in absolute totals**, while **Qatar and Kuwait** are **outliers per capita**.  

**Key takeaway:** Global population explains part of CO₂ emissions, but not the full story — energy mix and consumption patterns are decisive.  

> **Note:** The logarithmic scatter plot was intentionally chosen for a specific target audience — analysts and decision-makers familiar with data interpretation. For a business-oriented or non-technical audience, this visualization could be complex, and alternative approaches such as bar charts, heatmaps, or simplified KPIs might be more intuitive. This reinforces the importance of tailoring visualization design to the knowledge level and needs of the end user.


---

### Tableau – Top 10 Analysis  

![Tableau Dashboard](./Tableau-Dashboards/(2)dashboard-tableau.png)  

Each bubble represents a country, with size indicating magnitude of emissions (left) or population (right).  

- **Left (Top 10 emitters):**  
  Countries combining large populations with high fossil fuel use dominate (China, US, India, Russia).  

- **Right (Top 10 most populated):**  
  The most populated countries are not always the top emitters. For example, **India and China** have similar population shares but very different emissions.  

**Insight:** Emissions depend less on population and more on **energy consumption and lifestyle models**.  

---

### Tableau – Dual Perspective: Total vs Per Capita  

![Tableau Dashboard](./Tableau-Dashboards/(3)dashboard-tableau.png)  

- **Left (Total emissions):**  
  Giants like **China, US, and India** dominate total CO₂ volumes. Even with lower per capita averages, their populations make them the largest contributors.  

- **Right (Per capita emissions):**  
  Smaller countries like **Qatar, Kuwait, UAE, Brunei** top the list, reflecting oil- and gas-based economies with carbon-intensive lifestyles.  

**Conclusion:** A small group of countries concentrates both the highest **total emissions** and the highest **per capita emissions**. This duality is critical for policymaking: large emitters need to reduce carbon intensity, while high per capita countries must shift toward sustainable models.  

---

### Power BI – CO₂ Emissions per Continent  

![Power BI Dashboard](./Power-BI-Dashboards/(1)dashboard-powerbi.png)

*This dashboard presents the **average annual CO₂ emissions by continent** (bar chart) and the **trend of total CO₂ emissions (2001–2023)** (line chart).*

- **Key insights by continent:**
  - **Asia** leads both in annual average and continuous growth.  
  - **North America** remains high but relatively stable over time.  
  - **Europe** shows a **sustained decline since the early 2000s**; the chart annotations highlight the **Kyoto Protocol (2005)** and the **Paris Agreement (2015)** as regulatory milestones.  
  - **Africa, South America, and Oceania** contribute a smaller share to the global total.  

---

![Power BI Dashboard](./Power-BI-Dashboards/(2)dashboard-powerbi.png)

*This dashboard allows simulating the **impact of removing a single country** from continental totals, highlighting the disproportionate weight of major emitters (e.g., China, the US, India). Use the panel on the right to test different scenarios.*  

- **Top 10 Button (Total × Per Capita):**  
  - A **button/slicer** is provided to toggle toggle between **Top 10 by total emissions** and **Top 10 by per capita emissions**.  
  - **How it works in Power BI (technical note for README):**  
    1. A **Field Parameter** was created with two options: *Total CO₂ (MtCO₂)* and *CO₂ per capita (tCO₂/person)*.  
    2. This parameter is used in a **button-style slicer**, dynamically switching the metric displayed in rankings and visuals.  
    3. The ranking uses `RANKX()` over the selected metric to return the appropriate **Top 10**.  
  - **Analytical reading:** Switching to *per capita* highlights countries with small populations but very high individual footprints, while *total* emphasizes the largest economies/populations.  

---

### Power BI – Gauge Graph (Work in Progress)  

**Gauge visualization** will be used to compare **CO₂ emissions per capita** of each country or continent against the **global average**.

**Global context**: Instead of showing just absolute emissions, the gauge highlights whether a country is above or below the *world’s “normal”*.
**People-centric**: Per capita data links emissions to the population, showing the relative impact of individuals across countries.
**Regulatory risk**: Countries above the global average are more exposed to carbon taxes, tariffs, and stricter climate policies — key risks for multinational operations.
**ESG narrative**: This framing supports transparency and strategic communication with investors, customers, and regulators.

> Example: If the global average is ~5 tCO₂ per person, the gauge makes it evident that the U.S. (~14 tCO₂) or Qatar (~30+ tCO₂) are far above the baseline.

 
---

## 💻 Tools Used  
- **Python (pandas, matplotlib, seaborn)** – for data cleaning and exploratory analysis.  
- **Tableau / Power BI** – for advanced visualization and interactive dashboards.  
- **Kaggle Dataset** – main data source.  
- **Scrum Framework** – agile and collaborative project management.  

---

## 📂 Repository Structure  

```bash
DATA-DRIVEN-INSIGHTS-FOR-MULTINATIONALS/
├── EDA/
│   ├── EDA_CO2.ipynb
│   ├── EDA.ipynb
│   └── info.ipynb
├── Power-BI-Dashboards/
│   ├── (1)dashboard-powerbi.png
│   ├── (2)dashboard-powerbi.png
│   └── (3)dashboard-powerbi.png
├── Tableau-Dashboards/
│   ├── (1)dashboard-tableau.png
│   ├── (2)dashboard-tableau.png
│   └── (3)dashboard-tableau.png
├── data_clean_country.csv
├── data_clean_regions.csv
├── data.csv
└── README.md
```  

---

## ✔️ Next Steps  
- **Expand dataset scope** to include other greenhouse gases (CH₄, N₂O) for a broader climate impact assessment.  
- **Increase granularity** by analyzing emissions at the subnational level (states/provinces).  
- **Develop forecasting models** using machine learning to project emissions under different energy scenarios.  
- **Assess policy impact** by linking emission trends with international agreements (Kyoto, Paris).  
- **Automate data pipeline** to ensure dashboards remain updated with the latest datasets.  

---

## 👥 Roles  

The **EDA, data cleaning, and transformation** into two CSVs were collaboratively performed by **Ana Nobre, Bianca Gemar, Gabriela Layas, and Zara Valentinova**:  
- Extract, transform and load (ETL) processes, creating two CSVs: one focused on countries and territories, another with economic groups and continents (G7, developed vs developing).  
- Data visualization and dashboard development in Tableau and Power BI.  
- Business storytelling through data insights.  

### **Scrum Master & Project Lead – Ana Nobre**  
- Managed GitHub Project and Kanban dashboard, aligning tasks, objectives, and deadlines.  
- Apply agile leadership in a remote, pair programming and coding environment.  
- Ensured agile practices with **daily stand-ups, sprint reviews, retrospectives, and backlog refinement**.  

### **Further Individual Contributions – Ana Nobre**  
- Advanced the project individually by applying **quartile-based statistical analysis** to detect and justify outliers in both total emissions and emissions per capita.  
  - Outliers were defined using the **IQR rule**:  
    - Q1 = 25th percentile  
    - Q3 = 75th percentile  
    - IQR = Q3 – Q1  
    - Outlier thresholds = [Q1 – 1.5 × IQR, Q3 + 1.5 × IQR]  

> Note: Check EDA_CO2.ipynb for more details.  

- Created new **DAX measures** to enrich the insights presented in tooltips and visuals, including:  

```DAX
-- Rank by total CO₂ emissions (excluding Antarctica)
Rank Total CO2 =
RANKX (
    ALL ( 'data_clean_country'[country] ),
    [CO2 (less Antartica)],
    ,
    DESC,
    Dense
)

-- Rank by CO₂ emissions per capita
Rank CO2 per Capita (t) =
RANKX (
    ALL ( 'data_clean_country'[country] ),
    [CO2 per capita (t)],
    ,
    DESC,
    Dense
)
  ```

Creating dedicated **DAX measures** for ranking both total and per capita emissions is essential for producing accurate and dynamic insights in Power BI:  

**Comparability:** Without explicit ranking measures, visuals may misrepresent positions when filters or slicers are applied. The DAX ensures rankings always update consistently.  
**Dual perspective:** Total emissions highlight the largest economies and most populous nations, while per capita emissions reveal intensity at the individual level. This dual view prevents biased conclusions.  
**Dynamic tooltips and visuals:** By embedding these measures in tooltips, users get contextual insights directly in the dashboard, making the analysis more interactive and intuitive.  
**Policy and business relevance:** Governments and multinational organizations need both perspectives—absolute contribution to climate change and relative fairness per citizen—to design effective policies, negotiate targets, or benchmark corporate strategies.  


  - Refined **Power BI dashboards** to improve clarity, executive readability, and consultancy-style storytelling by:  
  - Standardizing all emission metrics into **MtCO₂** (millions of tonnes of CO₂).  
  - Highlighting Asia and Europe with stronger colors to emphasize key insights (Asia >50% global emissions; Europe’s post-2005 decline).  
  - Adding annotations for key climate milestones (Kyoto Protocol 2005, Paris Agreement 2015).  
  -Adding new executive-style titles and subtitles

---

## 🌱 Personal Learning  

This project went beyond technical work in EDA and visualization — it became an opportunity to apply my **10+ years leadership experience using agile practices** to a data-driven development conext. I led proven agile practices (remote collaboration, sprint planning, daily stand-ups, retrospectives, and backlog refinement) to drive efficiency and clarity in a coding and analytics environment.  

It allowed me to connect with the challenges of real technical and consultancy work:  
- Balancing **technical accuracy** with **executive-level storytelling**.  
- Practicing **pair programming and collaborative delivery** in distributed teams.
- Translating complex datasets into **clear, decision-oriented insights** for business stakeholders.  

This experience reinforced my ability to bridge **my leadership experience and advanced analytics**, ensuring that technical rigor and strategic impact move hand in hand.  

---

## References  

European Commission (no date) The Kyoto Protocol. Available at: https://climate.ec.europa.eu/eu-action/international-action-climate-change/kyoto-protocol_en 
(Accessed: 24 September 2025).

European Environment Agency (2024) *CO₂ emissions performance of new passenger cars in Europe*, European Environment Agency, 16 December. Available at: https://www.eea.europa.eu/en/analysis/indicators/co2-performance-of-new-passenger 
(Accessed: 16 September 2025).  

Intergovernmental Panel on Climate Change (2021) Climate Change 2021: The Physical Science Basis. Contribution of Working Group I to the Sixth Assessment Report of the Intergovernmental Panel on Climate Change. Cambridge University Press. Available at: https://www.ipcc.ch/report/ar6/wg1/ 
(Accessed: 17 September 2025).  

NASA (2023) Earth Fact Sheet. NASA Solar System Exploration. Available at: https://solarsystem.nasa.gov/planets/earth/overview/ 
(Accessed: 17 September 2025). 