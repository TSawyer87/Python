#Pandas
Being able to create a [[DataFrame]] or [[Series]] by hand is handy. But, most of the time, we won't actually be creating our own data by hand. Instead, we'll be working with data that already exists.

Data can be stored in any of a number of different forms and formats. By far the most basic of these is the humble CSV file. When you open a CSV file you get something that looks like this:

```
Product A,Product B,Product C,
30,21,9,
35,34,1,
41,11,11
```

So a CSV file is a table of values separated by commas. Hence the name: "Comma-Separated Values", or CSV.

Let's now set aside our toy datasets and see what a real dataset looks like when we read it into a DataFrame. We'll use the `pd.read_csv()` function to read the data into a DataFrame. This goes thusly:

wine_reviews = pd.read_csv("../input/wine-reviews/winemag-data-130k-v2.csv")

We can use the `shape` attribute to check how large the resulting DataFrame is:

wine_reviews.shape

(129971, 14)

So our new DataFrame has 130,000 records split across 14 different columns. That's almost 2 million entries!

We can examine the contents of the resultant DataFrame using the `head()` command, which grabs the first five rows:

wine_reviews.head()

||Unnamed: 0|country|description|designation|points|price|province|region_1|region_2|taster_name|taster_twitter_handle|title|variety|winery|
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|0|0|Italy|Aromas include tropical fruit, broom, brimston...|Vulkà Bianco|87|NaN|Sicily & Sardinia|Etna|NaN|Kerin O’Keefe|@kerinokeefe|Nicosia 2013 Vulkà Bianco (Etna)|White Blend|Nicosia|
|1|1|Portugal|This is ripe and fruity, a wine that is smooth...|Avidagos|87|15.0|Douro|NaN|NaN|Roger Voss|@vossroger|Quinta dos Avidagos 2011 Avidagos Red (Douro)|Portuguese Red|Quinta dos Avidagos|
|2|2|US|Tart and snappy, the flavors of lime flesh and...|NaN|87|14.0|Oregon|Willamette Valley|Willamette Valley|Paul Gregutt|@paulgwine|Rainstorm 2013 Pinot Gris (Willamette Valley)|Pinot Gris|Rainstorm|
|3|3|US|Pineapple rind, lemon pith and orange blossom ...|Reserve Late Harvest|87|13.0|Michigan|Lake Michigan Shore|NaN|Alexander Peartree|NaN|St. Julian 2013 Reserve Late Harvest Riesling ...|Riesling|St. Julian|
|4|4|US|Much like the regular bottling from 2012, this...|Vintner's Reserve Wild Child Block|87|65.0|Oregon|Willamette Valley|Willamette Valley|Paul Gregutt|@paulgwine|Sweet Cheeks 2012 Vintner's Reserve Wild Child...|Pinot Noir|Sweet Cheeks|

The `pd.read_csv()` function is well-endowed, with over 30 optional parameters you can specify. For example, you can see in this dataset that the CSV file has a built-in index, which pandas did not pick up on automatically. To make pandas use that column for the index (instead of creating a new one from scratch), we can specify an `index_col`.

wine_reviews = pd.read_csv("../input/wine-reviews/winemag-data-130k-v2.csv", index_col=0)
wine_reviews.head()

||country|description|designation|points|price|province|region_1|region_2|taster_name|taster_twitter_handle|title|variety|winery|
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|0|Italy|Aromas include tropical fruit, broom, brimston...|Vulkà Bianco|87|NaN|Sicily & Sardinia|Etna|NaN|Kerin O’Keefe|@kerinokeefe|Nicosia 2013 Vulkà Bianco (Etna)|White Blend|Nicosia|
|1|Portugal|This is ripe and fruity, a wine that is smooth...|Avidagos|87|15.0|Douro|NaN|NaN|Roger Voss|@vossroger|Quinta dos Avidagos 2011 Avidagos Red (Douro)|Portuguese Red|Quinta dos Avidagos|
|2|US|Tart and snappy, the flavors of lime flesh and...|NaN|87|14.0|Oregon|Willamette Valley|Willamette Valley|Paul Gregutt|@paulgwine|Rainstorm 2013 Pinot Gris (Willamette Valley)|Pinot Gris|Rainstorm|
|3|US|Pineapple rind, lemon pith and orange blossom ...|Reserve Late Harvest|87|13.0|Michigan|Lake Michigan Shore|NaN|Alexander Peartree|NaN|St. Julian 2013 Reserve Late Harvest Riesling ...|Riesling|St. Julian|
|4|US|Much like the regular bottling from 2012, this...|Vintner's Reserve Wild Child Block|87|65.0|Oregon|Willamette Valley|Willamette Valley|Paul Gregutt|@paulgwine|Sweet Cheeks 2012 Vintner's Reserve Wild Child...|Pinot Noir|Sweet Cheeks|