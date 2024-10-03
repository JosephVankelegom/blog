+++
title = 'Baby-foot statistics'
date = 2024-09-28T13:13:39+02:00
draft = false
summary = "Statistiques from baby-games played with friends"
+++

## Introduction

During the year 2024, I started playing baby-foot with friends.
After an unknow quantity of games we wanted to start recording the scores of our games to increase the challenge of the games.
We keep all the games scores on a excel file, from there we wanted additional informations about our performance and I decided to create a little python notebook to do taht.
I just learned about deepnote and decided to try it out (several pieces of code where generated with the IA).

Visit the [Notebook](https://deepnote.com/workspace/vanjotom-690650e7-21e6-4e93-ab8c-6a827642f688/project/BabyFoot-4a2ef5da-34d9-49ae-ac9a-5186cf57ff1d/notebook/CleanCsv-7f49f2b3e4e64f3fb8a2e2f49c1d9c11)!

The first step was to clean the excel of useless information:

```python
import pandas as pd
df = pd.read_csv('baby2.csv', delimiter=',',skiprows=10)
print('Columns before dropping NaNs:', df.columns)

# Drop columns that are completely NaN
cleaned_df = df.dropna(axis=1, how='all')

print('Columns after dropping NaNs:', cleaned_df.columns)

# Drop columns 'Unnamed: 3' and 'Unnamed: 18' (unknown columns)
cleaned_df = df.loc[:,['Home', 'Visitor', 'H_s', 'V_s']]

# Checking the columns after dropping NaN columns
remaining_columns = cleaned_df.columns
print('Columns after dropping NaNs and unknown columns:', remaining_columns)

cleaned_df.to_csv('babyfoot_cleaned.csv', index=False, sep=';')

cleaned_df
```
