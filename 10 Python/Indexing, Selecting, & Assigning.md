#Pandas 
# Native accessors[](https://www.kaggle.com/code/residentmario/indexing-selecting-assigning#Native-accessors)

Native Python objects provide good ways of indexing data. Pandas carries all of these over, which helps make it easy to start with.

Consider this DataFrame:

reviews

||country|description|designation|points|price|province|region_1|region_2|taster_name|taster_twitter_handle|title|variety|winery|
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|0|Italy|Aromas include tropical fruit, broom, brimston...|Vulkà Bianco|87|NaN|Sicily & Sardinia|Etna|NaN|Kerin O’Keefe|@kerinokeefe|Nicosia 2013 Vulkà Bianco (Etna)|White Blend|Nicosia|
|1|Portugal|This is ripe and fruity, a wine that is smooth...|Avidagos|87|15.0|Douro|NaN|NaN|Roger Voss|@vossroger|Quinta dos Avidagos 2011 Avidagos Red (Douro)|Portuguese Red|Quinta dos Avidagos|
|...|...|...|...|...|...|...|...|...|...|...|...|...|...|
|129969|France|A dry style of Pinot Gris, this is crisp with ...|NaN|90|32.0|Alsace|Alsace|NaN|Roger Voss|@vossroger|Domaine Marcel Deiss 2012 Pinot Gris (Alsace)|Pinot Gris|Domaine Marcel Deiss|
|129970|France|Big, rich and off-dry, this is powered by inte...|Lieu-dit Harth Cuvée Caroline|90|21.0|Alsace|Alsace|NaN|Roger Voss|@vossroger|Domaine Schoffit 2012 Lieu-dit Harth Cuvée Car...|Gewürztraminer|Domaine Schoffit|

129971 rows × 13 columns

In Python, we can access the property of an object by accessing it as an attribute. A `book` object, for example, might have a `title` property, which we can access by calling `book.title`. Columns in a pandas DataFrame work in much the same way.