## Introduction

Mental health disorder refers to the abnormal performance of an individual's psychological function, which affects his or her normal thinking, emotion, behavior and social functions. These disorders can span a wide spectrum, including anxiety disorders, depressive disorders, schizophrenia, somatoform disorders, and more. Mental health disorders can significantly impact a patient's quality of life, making it difficult for them to work, study and socialize normally. The impact is not limited to the patient himself, but also affects his family, social circle and workplace. At the same time, it may cause patients to pose dangers to themselves and others, such as suicide, violent behavior, etc., which poses a potential threat to both the patient himself and society. As people's awareness of mental health increases, so does the focus on mental health issues. People are increasingly aware of the close relationship between mental health and overall health, so the level of attention paid to mental health issues is also increasing. Mental health problems are common across the globe, regardless of age, race, gender or social status. Therefore, their scope of influence is very wide and needs to be fully valued and paid attention to.

By analyzing global trends in mental health disorders, we try to reveal the influencing factors of their occurrence and eliminate social prejudice and discrimination against mental illness. Through scientific research and education, we can help the public better understand mental health issues, reduce discrimination and stigmatization of patients, and provide them with more support and understanding. At the same time, it can help governments and international organizations better formulate relevant policies and plans and rationally allocate resources. According to the needs of different regions and groups, mental health services and support are provided in a targeted manner to solve the mental health challenges faced by different regions and groups. It can also help to detect the development trends of mental health problems and high-risk groups early, so that effective prevention and intervention measures can be taken. By establishing early intervention mechanisms, strengthening mental health education and providing mental health services, the occurrence and development of mental health problems can be reduced and the mental health of the population can be promoted. In addition, new research directions and challenges can be discovered through the analysis of global trends. With changes in society, economy, and environment, new mental health problems or changing trends in original problems may emerge, and research priorities and strategies need to be adjusted in a timely manner to meet new challenges.
>World Health Organization (WHO). (2017). Depression and Other Common Mental Disorders: Global Health Estimates.

我们在Kaggle数据库中检索得到了一个记录了1990年到2017年来自全球各国的有关精神健康障碍患病率的信息数据。这些数据是来自于https://ourworldindata.org/ 的信息。我们将使用这个数据集分析并讨论世界各地的人们患有哪些类型的心理健康障碍、每个国家患有心理健康问题的人数、性别对患抑郁症的影响等问题。
## Materials and Methods
该数据集包括了从1990年到2017年期间，精神分裂症、双相情感障碍、饮食失调、焦虑症、吸毒障碍、抑郁症和酒精使用障碍等心理健康问题在全球各国的患病率。

### sample
数据中包含以下信息：
-实体：数据集中包含的每个国家或地区的唯一标识符。
-代码：与数据集中包含的实体/国家或地区关联的唯一代码。
-年份：收集有关特定实体/国家/地区的数据的年份。
-精神分裂症 (%)：当年该国家/地区患有精神分裂症的人数百分比。
-双相情感障碍 (%)：该国家/地区当年患有双相情感障碍的人数百分比。
-饮食失调 (%)：该国家/地区当年患有饮食失调的人数百分比。
-焦虑症 (%)：当年该国家/地区患有焦虑症的人数百分比。
-吸毒障碍 (%)：当年该国家/地区患有吸毒障碍的人数百分比。
-抑郁症 (%)：当年该国家/地区患有抑郁症的人数百分比。
-酒精使用障碍 (%)：当年该国家/地区患有酒精使用障碍的人数百分比。
### Measures
我们将这个数据集导入Google Colab，查看数据情况。我们发现这个数据集有些混乱。例如，有很多的NaN值，dataset有108552行，但是"Bipolar disorder"列有19406行non-null值，"Anxiety disorders"列仅有6468行non-null值；此外，每个国家或地区的唯一标识符和关联的唯一代码行数也不相同；同时，在我们查看数据时发现，出现了大量不合理的数据，在"Schizophrenia"列中出现了类似"311665.769283"的明显不是百分比的数据。结合大量的NaN值，我们推测该数据集可能由几个不同的dataset合并得到。

观察数据，然后对dataset进行了数据切片。我们发现了这个数据集有4个不同数据集。Table 1: Top 6468 rows, Prevalence of mental health disorders in various countries around the world (%). Table 2: Rows between 6469 and 54276, Proportion of patients of each gender in the total population (%).Table 3: Rows between 54277 and 102084, Suicide rate and depression prevalence per 100,000 inhabitants (%). Table 4: After row 102,084, Prevalence of depression per 100,000 inhabitants(%).

我们先开始处理Table 1: 将多余的"index"列删除，将列明标准化。我们再次查看数据信息发现只有国家代码列有部分数据缺失。查看国家名称后发现是因为有一些国家集团或者地区名称的出现，我们使用了最简单的删除空值行来解决这个问题。然后将数字的数据类型改为numeric方便后续分析。最后将清理好的数据保存为csv文件，进行数据的备份。

我们用同样的方式处理Table 2：根据与raw data对比我们知道了，在Table 2中，第4列为各地区男性患者在总人口中的占比，第5列为女性患者占比，第6列为总人口数。处理的过程中发现，有男性患者和人口数据的丢失，我们同样用删除缺失值所在行来解决这个问题。最后将清理好的数据进行备份。

Table 3与Table 4的数据在本文中暂时不做讨论。

得到了以上数据后，我们开始对数据进行合理的分析，并将数据可视化以便更直观的明显的理解数据。
### Statistical analysis
首先，我们将各个国家按照所在大陆分组计算患病率平均值。因为2017年是最新的数据，所以首先制作2017年各大陆的患病情况的bar图。


## Results



## Discussion
