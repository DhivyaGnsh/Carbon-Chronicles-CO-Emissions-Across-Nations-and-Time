# Carbon-Chronicles-CO-Emissions-Across-Nations-and-Time

This dataset provides a comprehensive look at carbon dioxide (CO₂) emissions on a country-by-country basis, enabling analysis of both historical trends and recent developments in global emissions. Sourced from data.gov.in and curated for accuracy and usability, this dataset includes annual emissions data for numerous countries, categorized by year and region.

Country: The name of the country for which CO₂ emissions data is recorded. This column allows for country-specific analysis and comparison.
Region: The geographical or administrative region to which each country belongs. This categorization facilitates regional analysis by grouping countries into broader areas, such as continents or economic zones.
Date: The year in which the CO₂ emissions data was recorded, formatted as a date for compatibility with time-series analysis and to allow temporal trends to be identified.
Kilotons of CO₂: The total amount of carbon dioxide emissions, measured in kilotons, released by each country in the specified year. This column provides a quantitative measure of national CO₂ emissions.
Metric Tons Per Capita: The per capita emissions of CO₂ for each country, expressed in metric tons. This value represents the average carbon dioxide emissions per person, offering insight into individual emissions contributions relative to population size.


#per capita emissions between high-emitting regions and low-emitting regions
data = pd.DataFrame(df)
code:
region_totals = data.groupby('Region')['Kilotons of Co2'].sum()
high_emit_regions = region_totals[region_totals > region_totals.median()].index
low_emit_regions = region_totals[region_totals <= region_totals.median()].index

high_per_capita = data[data['Region'].isin(high_emit_regions)].groupby('Region')['Metric Tons Per Capita'].mean()
low_per_capita = data[data['Region'].isin(low_emit_regions)].groupby('Region')['Metric Tons Per Capita'].mean()

high_per_capita, low_per_capita

result
(Region
 Americas    3.646733
 Asia        6.152303
 Name: Metric Tons Per Capita, dtype: float64,
 Region
 Africa     1.052448
 Europe     7.222740
 Oceania    3.801449
 Name: Metric Tons Per Capita, dtype: float64)
