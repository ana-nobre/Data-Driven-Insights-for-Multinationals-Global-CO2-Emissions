# 🌍 Data Insights: CO₂ Emissions by Country, Region, and Sector   

## Introduction    

This project presents a consultancy case at a **country-level granularity**. The analysis highlights how emissions differ across nations and regions, helping multinational companies, governments, and international organizations prioritize policies, investments, and ESG strategies.  

Climate change is not only an environmental challenge but also a strategic business and policy concern. Carbon dioxide (CO₂) emissions, as the main driver of global warming (IPCC, 2021), directly impact economic stability, regulatory frameworks, corporate sustainability strategies, and long-term investment decisions.  

This project develops an **interactive dashboard in Tableau/Power BI** to track and analyze CO₂ emissions by country, region, and sector. The goal is to provide decision-makers, analysts, and stakeholders with clear insights into emission trends, sectoral contributions, and global disparities.  

By leveraging this analysis, organizations and policymakers can benchmark performance, identify high-impact sectors, evaluate regional progress, and align strategies with global sustainability goals (e.g., Net Zero targets and ESG reporting).  

## Introduction    

This project presents a consultancy case at a **country-level granularity**. The analysis highlights how emissions differ across nations and regions, helping multinational companies, governments, and international organizations prioritize policies, investments, and ESG strategies.  

Climate change is not only an environmental challenge but also a strategic business and policy concern. Carbon dioxide (CO₂) emissions, as the main driver of global warming (IPCC, 2021), directly impact economic stability, regulatory frameworks, corporate sustainability strategies, and long-term investment decisions.  

> **Note:** While CO₂ is the focus of this project, it is important to recognize that other greenhouse gases — such as methane (CH₄) and nitrous oxide (N₂O) — also play a critical role in global warming. Methane, for example, has been linked not only to climate impact but also to adverse public health effects, including an increased risk of cancer. Additionally, the energy transition is a long-term process, and depending on the industry under analysis, other gases might be more relevant to monitor. In this dataset, CO₂ was chosen, but future studies could fully leverage the GHG data in the database to expand the scope.

The dataset used comes from Kaggle: 
Dangi, S. (2024). *CO₂ Emissions across Countries, Regions and Sectors*. Kaggle. Available at: https://www.kaggle.com/datasets/shreyanshdangi/co-emissions-across-countries-regions-and-sectors  

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

*This dashboard shows the **average emissions by continent** (bar chart) and the **evolution of CO₂ emissions** over time (line chart).*  

- **Continental insights:**  
  - Asia leads in both average emissions and growth.  
  - North America remains high but relatively stable.  
  - Europe shows sustained decline since the 2000s, partly reflecting **Kyoto Protocol commitments**.  
  - The **Paris Agreement (2015)** set long-term targets, though effects are not yet visible in the data.  

- **Scenario dashboards:**  
  Removing one major emitter (e.g., China) drastically shifts global trajectories, showing the **disproportionate influence of a handful of countries**.  

---

### Power BI – Energy Consumption  

![Power BI Dashboard](./Power-BI-Dashboards/(2)dashboard-powerbi.png)  

This dashboard compares **primary energy consumption and CO₂ emissions by continent**, using line charts, stacked bars, and a pie chart. Asia represents **over 50%** of global primary energy consumption, linking directly to its CO₂ dominance.  

---

### Outlier Analysis – Boxplots  

(Boxplots under construction)  

Planned analysis:  
- **Total CO₂ emissions** → detecting countries with extreme total contributions.  
- **CO₂ per capita** → identifying disproportionate emitters (e.g., Qatar, Kuwait).  

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
├── research_questions.ipynb
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

### **Next Steps – Ana Nobre** 
- Individualy deu seguimento no projeto fazendo novos calculos estatisticos de quartis para para calcular tecnicamente os outliers de total emissions and emissions per capita.
- Enhace Power BI graphs to align with more executive and consultancy tone. 

---

## 🌱 Personal Learning  

This project was not only a technical exercise in EDA and visualization but also an opportunity to apply agile leadership in a remote and coding environment.  
For Ana, it was a chance to connect her **10+ years of agile experience at Apple** with the challenges of a data-driven consultancy project: balancing technical accuracy, business storytelling, and collaborative delivery.  

- Applied her professional background, where she lived agile practices daily that includes:  
  - **On-site and remote leadership**, coordinating teams both within the same country and across countries (e.g., Mexico–Brazil, Mexico–US).  
  - **Daily downloads and weekly scheduling huddles** to synchronize cross-functional teams.  
  - Collaboration with **Retail People Operations (RPO)** to align staffing and operations.  
  - Experience leading **cross-functional squads** across different time zones.  
  - Strong culture of **continuous improvement, transparency, and accountability**.  


---

## References  

European Environment Agency (2024) *CO₂ emissions performance of new passenger cars in Europe*, European Environment Agency, 16 December. Available at: https://www.eea.europa.eu/en/analysis/indicators/co2-performance-of-new-passenger (Accessed: 16 September 2025).  

Intergovernmental Panel on Climate Change (2021) Climate Change 2021: The Physical Science Basis. Contribution of Working Group I to the Sixth Assessment Report of the Intergovernmental Panel on Climate Change. Cambridge University Press. Available at: https://www.ipcc.ch/report/ar6/wg1/ (Accessed: 17 September 2025).  

NASA (2023) Earth Fact Sheet. NASA Solar System Exploration. Available at: https://solarsystem.nasa.gov/planets/earth/overview/ (Accessed: 17 September 2025).  
