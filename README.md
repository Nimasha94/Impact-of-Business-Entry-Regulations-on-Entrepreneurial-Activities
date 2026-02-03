# Impact of Business Entry Regulations in Countries on Entrepreneurial Activities
## An Agent-based Simulation Approach

### Overview
The main goal of this project is to investigate the impact of business entry regulations in countries on entrepreneurial activities. Specifically, we seek to answer: (1) How do regulatory barriers to business entry shape a country’s readiness for entrepreneurship, and (2) which regulatory components – the quality of regulations for business entry, the availability of digital public services and transparency of information for business entry or the time and cost required to register new domestic and foreign firms – act as the main constraints on entrepreneurial activity.

### Data
We used two datasets from The World Bank. The primary dataset is the Business Entry dataset from their B-ready project. And we also used their country-classification dataset (based on the income) to classify the countries in our primary dataset into the four main income groups.

**[Business Entry Dataset 2025](https://www.worldbank.org/en/businessready/topic/business-entry)**

The B-Ready project is one of the World Bank Group’s initiatives to assess the business environment and investment climate worldwide. Business Entry is one of the categories assessed under this project. As mentioned in the World Bank website, the topics under this category measures the process of registration and start of operations of new companies based on different dimensions. These dimensions were classified into mainly three pillars.
- Pillar 1: Assess the quality of regulations for business entry
- Pillar 2: Assess the availability of digital public services and transparency of information for business entry
- Pillar 3: Assess the time and cost required to register new domestic and foreign firms
Each pillar is divided into categories, and each category is further divided into subcategories. Each subcategory has several indicators. A group of experts had analyzed 101 countries (economies) and assigned points to 18 indicators. Finally, all these points were aggregated to obtain the number of points for each subcategory, category, pillar, and overall score.

**[Current classification of countries by income](https://ddh-openapi.worldbank.org/resources/DR0095333/download)**

To classify the countries in the business entry dataset, we used a second dataset that provides the official World Bank country classifications by income level. This dataset classifies the countries into mainly four income groups as lower income, lower-middle income, higher-middle income and higher income.

## Methodology

- Normalizing the Structure of the Datasets
  
The Business Entry dataset had a complex, hierarchical header structure that represent the levels; pillars, categories, sub-categories and indicator. To handle this multilevel structure, data was loaded to the data frame by skipping the first three metadata-rows. There were no any rows or columns with missing values.

- Merging the Two Datasets
  
In order to analyze the data based on their income group, we wanted to identify the income group that each country in the Business Entry dataset belongs. For this purpose, we merged the second dataset (World Bank Country Classification) with our primary dataset.

- Agent-Based Simulation
  
We developed an agent-based model with agents (entrepreneurs) who are trying to enter different economies. The agents could be either domestic or foreign entrepreneurs. We simulated 10,000 agents with:
    - Agent attributes: Capital, Skill, Risk-taking, and Persistence.
    - External Factors: Regulatory quality, digital service availability, and operational time/cost.
    - Success Logic: A multiplicative probability model determining if an agent succeeds in the economy. And, if they failed, based on their persistance, they will either try to enter another market or exit from the system.

## Results
The exploratory data analysis revealed that most of the countries have moderate or high readiness for business entries (with overall score 60-90) while a fewer number of countries have low readiness (overall score < 60).

Furthermore, the “Quality of Regulations for Business Entry” is relatively strong globally and most countries have implemented supportive regulations. In contrast, “Digital Public Services and Transparency of Information for Business Entry” has the greatest heterogeneity among countries. This suggest that, some countries offer very efficient digital public services and transparency of information in terms of business entry, while others do not. In addition, the “Operational Efficiency (Cost and time) of Business Entry” is commonly seen among the country, but not evenly distributed.

The simulations show that, regardless of the income group, there is an increase in the number of Startups when the readiness to market entry increases. However, there is no patterns of Failures with the changes in the market readiness. When the countries improve their Digital Public Services and Transparency of Information for Business Entry, the number of Startups increases. In addition, when the countries decrease the processing time and cost (which means: increasing the relevant scores), they can increase their Startups by a noticeably high value. However, the countries in the lower income group seems to have no much impact by the changes in the processing cost.

## Conclusion

In conclusion, even though there are three main types of market-entry barriers were identified by the world bank’s B-ready project, this study shows that, mainly two types of barriers cause the variation among the countries’ readiness to new business entries. Therefore, by focusing on improving the;

- Digital public services and transparency of information
- Efficiency of the process by reducing time and cost
  
countries can increase their readiness for new business entries.

## Limitations

A main limitation of the ABM in this study is assigning equal weight to all the agent characteristics. In contrast, these characteristics are weighted unevenly in the real world. For example, without having a minimum cost-of-entry, no amount of “Skill” or “Risk tolerance” can prevent an agent from exiting. 

Besides, the ABM is based on the World Bank Business Entry Scores rather than calibrated against real-world startup data for 2025. Therefore, the model assumes that these scores are the primary drivers for the success of the agents. However, in real world, a country might have poor regulatory scores but high startup activity due to many other reasons like informal networks or methods to bypass the “official” procedure. Without actual startup figures, we cannot identify these "over-performing" economies. Additionally, actual startup-count data would have allowed for a regression analysis to determine which pillar is the statistically strongest predictor of new Startups.

Finally, we have programmed the agents in our simulation to "exit" or "fail" based on a multiplicative success probability. However, in real world, human behavior is often driven by non-economic factors and the entrepreneurs may continue trying due to emotional attachment, etc., or they may even find informal ways to bypass bureaucratic hurdles that a computational model cannot fully simulate.
