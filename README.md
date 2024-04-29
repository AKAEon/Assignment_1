# Insights into Global Mental Health Trends

## Introduction

Mental health disorders refer to the abnormal manifestation of individual psychological functions, affecting their normal thinking, emotions, behavior, and social functioning. The range of these diseases is wide, including anxiety disorders, depression, schizophrenia, somatoform disorders, etc. Mental health disorders can significantly impact the quality of life of patients, making it difficult for them to work, study, and socialize normally. The impact is not limited to the patients themselves but also extends to their families, social circles, and workplaces. At the same time, it may also lead to dangers to themselves and others, such as suicide, violent behavior, etc., posing potential threats to both the patients themselves and society. With the increasing awareness of mental health, attention to mental health issues is also increasing. People are increasingly recognizing the close relationship between mental health and overall health, so the level of attention to mental health issues is also increasing. Mental health issues are common worldwide, regardless of age, race, gender, or social status. Therefore, their impact is widespread and requires full attention.

The Centers for Disease Control and Prevention (CDC) aims to address global mental health trends by identifying influencing factors underlying their occurrence and combating societal biases and discrimination against mental illness. Through scientific research and education, the CDC seeks to enhance public understanding of mental health issues, reduce discrimination and stigma against patients, and provide them with more support and empathy. Additionally, it assists governments and international organizations in formulating relevant policies and plans and allocating resources appropriately based on the needs of different regions and populations. Tailored mental health services and support are provided to address the specific challenges faced by different regions and populations. Early detection of mental health problems and high-risk populations is facilitated to enable effective prevention and intervention measures. Establishing early intervention mechanisms, enhancing mental health education, and providing mental health services can reduce the occurrence and development of mental health problems and promote population mental well-being. Furthermore, analyzing global trends can identify new research directions and challenges. With changes in society, economy, and environment, new mental health issues or changes in existing trends may arise, requiring timely adjustments in research focus and strategies to address emerging challenges.
>World Health Organization (WHO). (2017). Depression and Other Common Mental Disorders: Global Health Estimates.

We retrieved a dataset from the Kaggle database containing information on the prevalence of mental health disorders from countries worldwide spanning from 1990 to 2017. This data originates from https://ourworldindata.org/. We will utilize this dataset to analyze and discuss various aspects such as the types of mental health disorders affecting people worldwide, the distribution of individuals with mental health disorders across continents, and more.

## Materials and Methods

The dataset includes the prevalence rates of mental health issues such as schizophrenia, bipolar disorder, eating disorders, anxiety disorders, drug use disorders, depression, and alcohol use disorders across countries worldwide from 1990 to 2017.

### sample

The dataset contains the following information:
-Entity: Unique identifier for each country or region included in the dataset.
-Code: Unique code associated with each entity/country or region included in the dataset.
-Year: Year for which the data about a specific entity/country/region was collected.
-Schizophrenia (%): Percentage of the population in the country/region diagnosed with schizophrenia in a given year.
-Bipolar Disorder (%): Percentage of the population in the country/region diagnosed with bipolar disorder in a given year.
-Eating Disorders (%): Percentage of the population in the country/region diagnosed with eating disorders in a given year.
-Anxiety Disorders (%): Percentage of the population in the country/region diagnosed with anxiety disorders in a given year.
-Drug Use Disorders (%): Percentage of the population in the country/region diagnosed with drug use disorders in a given year.
-Depression (%): Percentage of the population in the country/region diagnosed with depression in a given year.
-Alcohol Use Disorders (%): Percentage of the population in the country/region diagnosed with alcohol use disorders in a given year.

### Measures
It seems like the dataset imported into Google Colab is quite messy. There are numerous NaN values present, and inconsistencies in the number of non-null values across different columns. For example, while the "Bipolar disorder" column has 19,406 non-null values, the "Anxiety disorders" column only has 6,468 non-null values. Additionally, the number of rows for unique identifiers and associated unique codes for each country or region varies.

Furthermore, upon inspecting the data, we noticed many unreasonable values, such as the presence of non-percentage data in the "Schizophrenia" column like "311665.769283". Considering these issues along with the abundance of NaN values, it's possible that this dataset is a result of merging several different datasets.

>(https://drive.google.com/file/d/11InQhvimCWKPGfYUNPNVS5UU_7NteaIu/view?usp=drive_link)

Observing the data and performing data slicing, we discovered that this dataset actually consists of four distinct datasets.Table 1: Top 6468 rows, Prevalence of mental health disorders in various countries around the world (%). Table 2: Rows between 6469 and 54276, Proportion of patients of each gender in the total population (%).Table 3: Rows between 54277 and 102084, Suicide rate and depression prevalence per 100,000 inhabitants (%). Table 4: After row 102,084, Prevalence of depression per 100,000 inhabitants(%).


We'll start by processing Table 1: removing the extra "index" column and standardizing the column names. Upon reviewing the data information again, we noticed that only the country code column has some missing data. After examining the country names, we found that this was due to the presence of some country groups or regional names. We resolved this issue by simply dropping the rows with missing values. Then, we'll convert the numeric data types to numeric for ease of analysis. Finally, we'll save the cleaned data as a csv file for backup purposes.>(https://drive.google.com/file/d/1-2ul57Qq0fi6Rp8M6xxLOgEkm3_GO0WQ/view?usp=drive_link)

Table 2, Table 3, and Table 4 data will not be discussed in this article for now.

After obtaining the above data, we begin to analyze the data rationally and visualize it to facilitate a more intuitive understanding of the data.

### Statistical analysis

First, we utilize the data from Table 1 to analyze the Mental health disorder prevalence across countries grouped by continent. Since 2017 is the most recent year available, we focus on the prevalence of mental health disorders in that year.

We use geopandas to obtain global geographical data and merge it with Table 1 to create a new dataset. The new dataset includes the continent to which each country belongs. We group the data for the year 2017 by continent and calculate the mean prevalence for each mental health disorder, using the continent column as the identifier variable. We then use plotly.express to create an interactive bar plot. The x-axis represents different mental health disorders, the y-axis represents the average prevalence percentage of each disorder in 2017 across continents, and the bars are colored according to the continent.

![Disease situation in various continents in 2017](/2017.png)

>(https://drive.google.com/file/d/1-AAC9E9SCTFZdi8z3n-P861YM97JOf8u/view?usp=sharing)

From this bar plot, we can clearly see that globally, anxiety disorders have the highest prevalence compared to other disorders, followed by depression. The prevalence of anxiety disorders is higher than that of depression on most continents, but notably, in Africa, the prevalence of depression is higher than that of anxiety disorders. Another significant observation is regarding "alcohol use disorders", with Europe having the highest prevalence, followed by North America and South America.

Next, we generate a correlation heatmap based on the 2017 data to visualize the correlations between various mental health disorders. We use the corr function to calculate the correlation coefficients between mental health disorders and seaborn's heatmap function to plot the heatmap. The color of each cell represents the correlation coefficient between the respective mental health disorders, with darker colors indicating higher correlation and lighter colors indicating lower correlation.

![hotplot 2017](/hotplot2017.png)

From this heatmap, we can easily observe that schizophrenia, bipolar disorder, and anxiety disorder show relatively high correlations with eating disorders, followed by drug use disorders. Bipolar disorder also exhibits a high correlation with anxiety disorders, while anxiety disorders, drug use disorders, and alcohol use disorders even show some negative correlation.

Finally, we computed the difference between the data from 2017 and 1990 to analyze the changes in the prevalence of mental health disorders across continents over the 27-year period.

We created a table of the differences in prevalence rates between 1990 and 2017, and similarly used plotly.express to generate an interactive bar plot. The x-axis represents different mental health disorders, the y-axis represents the changes in the prevalence of disorders across continents, and the color of the bars indicates the different continents.

![Trends in mental health disorders from 1990 to 2017](/1990_2017.png)

>(https://drive.google.com/file/d/12s9XHKhZMVjMUKXpVmAppCjI1MGVx1WC/view?usp=drive_link)

In this plot, we can clearly see that the most significant change over the 27-year period from 1990 to 2017 is the decrease in the prevalence rate of depression in Europe, with a noticeable decline exceeding 0.2%. Additionally, there is a significant decrease in the prevalence rate of alcohol use disorders in North America, contrasting with the increase observed in Oceania. Over these 27 years, apart from depression, the prevalence rates of various mental health disorders have increased, with a notable rise in the prevalence rate of drug use disorders across all continents. This is a noteworthy observation.

## Results and Recommendations

In 2017, anxiety disorders had the highest prevalence globally, followed by depression. On most continents, the prevalence of anxiety disorders exceeded that of depression, except for Africa, where depression rates were higher than anxiety. Additionally, alcohol use disorders had the highest prevalence in Europe, followed by North and South America. Regarding correlations, anxiety disorders, bipolar disorder, and schizophrenia were highly correlated with eating disorders, followed by drug use disorders. Bipolar disorder showed the highest correlation with anxiety disorders, while drug use disorders exhibited the lowest correlation, even showing negative correlations.

Based on these findings, measures can be taken to address mental health issues. Firstly, efforts should be made to strengthen the prevention and treatment of anxiety and depression, with a focus on addressing depression issues in Africa. Secondly, regulatory and treatment efforts for alcohol use disorders should be strengthened, especially in Europe, North America, and South America. Furthermore, further research is needed to understand the correlation between drug use disorders and other mental health disorders, in order to develop targeted prevention and treatment strategies. Lastly, raising awareness and promoting mental health issues are essential for improving societal understanding and prioritization of mental health.

Additionally, actions can be taken to address observed trends. Firstly, in Europe, efforts should be made to identify and replicate factors contributing to the decrease in depression prevalence, possibly through increasing access to mental health services and community support programs. Secondly, in North America, interventions for alcohol use disorders should be strengthened, including measures to reduce drinking and support individuals struggling with alcohol addiction. Thirdly, globally, proactive measures should be implemented to address the increasing prevalence of drug abuse disorders, including prevention programs, early intervention strategies, and improving accessibility to drug abuse treatment services. Moreover, ongoing monitoring and research are crucial for understanding the fundamental drivers of these trends and developing effective intervention measures to alleviate the global burden of mental health disorders.

## Conclusion
In today's society, it is crucial to prioritize mental health issues as they are closely linked to overall happiness and quality of life. Neglecting mental health concerns can lead to various negative impacts on individuals and society, including decreased productivity, interpersonal problems, and increased risk of illness. Therefore, strengthening mental health education, providing mental health services and support is essential for building a healthy and harmonious society.

Through the study of this dataset, we can gain insights into global governance. Different continents face different challenges: while Europe has a high prevalence of alcohol use disorders, there has been a significant decrease in depression rates for certain reasons; Africa may need to pay attention to the management of depression. Depression has always been the most challenging mental health issue globally.

Additionally, one can explore the factors influencing different mental health disorders by considering the development trends of various continents in other aspects from 1990 to 2017, such as economic growth, total population, educational attainment, and so on.

Lastly, it is hoped that through efforts from all sectors, the number of people suffering from mental health disorders will decrease over time.

## Appendix
-Python code(https://colab.research.google.com/drive/1gV7ZS2dUYpj21yfELFXvzIcxnXLNZr_L?usp=sharing)
