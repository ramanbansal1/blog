# A Comprehensive Guide to Using the Pytrends Python Library
## Introduction
With Pytrends, users can easily visualize the data they have collected, as well as create custom reports and dashboards. Additionally, Pytrends offers tutorials and documentation to help users get started with the library. In this article, we will discuss what Pytrends is and how it works so that you can start using it for your own data analysis projects.

## How to Install & Set Up the Pytrends Python Library
Installing and setting up the Pytrends Python library is easy and straightforward. 

Here, is the pip command that you need to run for installation

```bash
pip install pytrends
```

## Exploring the Different Features of the Pytrends Python Library
### Connecting to google
One of the initial steps for using pytrends is to connect it with Google and we need to import `TrendReq` from `pytrends.request`. Also, `pandas` library for data visualization.
```python
import pandas as pd
from pytrends.request import TrendReq
pytrend = TrendReq()
```

### Intreset By Region
Let's say we need to find the intreset of people of different countries in a given keyword. For this, we will use `interest_by_region` method to gennerate a dataFrame( which shows what proportions of people are interested in the given topic).

```python
kw = ['Python']
pytrend.build_payload(kw_list=kw)

df = pytrend.interest_by_region()
df.head()
```
The values goes from 0 to 100.

### Dialy Trends
Now let us get the top daily search trends worldwide. To do this we have to use the trending_searches() method. If you want to search worldwide just don't pass any parameter.

Pytrends API gives the facility to checkout the dialy search trends from worldwide. `trending_searches` method we get a report of trending searches but for a country just pass parameter `pn`

```python
df = pytrend.trending_searches(pn="india")
df.head()
```
You should enter the country name in lowercase
## Past trends
With `top_charts` method we can get the top trending searches yearly. 
```python
df = pytrend.top_charts(2022, hl="en-IN", tz=300, geo='GLOBAL')
df.head()
```

### Keyword Suggestion
Whenever we search on google, it will start giving suggestions according to the query given. To generate a list of suggestions, we need `suggestions` method.
```python
keyword = 'Python'
data = pytrend.suggestions(keyword)
df = pd.DataFrame(data)
df.head()
```

### Related Queries & Topics
Related queries means the queries related to the keyword. 

```python
pytrend.build_payload(kw_list=['Python'])
related_queries = pytrend.related_queries()
related_queries.values()

related_topic = pytrend.related_topics()
related_topic.values()
```

Thanks for reading.
Orignal article: [Dev.to](https://dev.to/ramanbansal/a-comprehensive-guide-to-using-the-pytrends-python-library-3l0d)
