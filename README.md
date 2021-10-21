# ExcelDataAnalysisOnDiamondDataset
Took a Dataset Analyzed it as much as I could using Excel.

The link to the dataset is : https://www.kaggle.com/miguelcorraljr/brilliant-diamonds

![image](https://user-images.githubusercontent.com/72384743/138219853-21cf756a-3e98-47ab-b815-22fe46f79f38.png)

The Data Looks like this :
	
|id|shape|carat|cut|color|clarity|report|type|price|
|:-|:----|:----|:--|:----|:------|:-----|:---|:---|
|10086429|Round|0.3|Very Good|J|SI2|GIA|natural|400|
|10016334|Emerald|0.31|Ideal|I|SI1|GIA|natural|400|
|9947216|Emerald|0.3|Ideal|I|VS2|GIA|natural|400|
|10083437|Round|0.3|Ideal|I|SI2|GIA|natural|400|
|9946136|Emerald|0.3|Ideal|I|SI1|GIA|natural|400|

# Context:

~119K natural and lab-created diamonds from brilliantearth.com to demystify the value of the 4 Cs – cut, color, clarity, carat.

# Content:

|Column|Description|
|:-----|:----------|
|id|Diamond identification number provided by Brilliant Earth	int|
|url|URL for the diamond details page	string|
|shape|External geometric appearance of a diamond	string/categorical|
|price|Price in U.S. dollars	int|
|carat|Unit of measurement used to describe the weight of a diamond	float|
|cut|Facets, symmetry, and reflective qualities of a diamond	string/categorical|
|color|Natural color or lack of color visible within a diamond, based on the GIA grade scale	string/categorical|
|clarity|Visibility of natural microscopic inclusions and imperfections within a diamond	string/categorical|
|report|Diamond certificate or grading report provided by an independent gemology lab	string|
|type|Natural or lab created diamonds string|
|date_fetched|Date the data was fetched date|

It has 119307 rows and 11 columns out of which id, url, report(only has one unqiue value) and data_fetched are useless for data analysis so the first thing we do is remove those Columns.

After Removing those, the data looks like this :

| id       | shape   | carat | cut       | color | clarity | report | type    | price |
| -------- | ------- | ----- | --------- | ----- | ------- | ------ | ------- | ----- |
| 10086429 | Round   | 0.3   | Very Good | J     | SI2     | GIA    | natural | 400   |
| 10016334 | Emerald | 0.31  | Ideal     | I     | SI1     | GIA    | natural | 400   |
| 9947216  | Emerald | 0.3   | Ideal     | I     | VS2     | GIA    | natural | 400   |
| 10083437 | Round   | 0.3   | Ideal     | I     | SI2     | GIA    | natural | 400   |
| 9946136  | Emerald | 0.3   | Ideal     | I     | SI1     | GIA    | natural | 400   |
| 10070154 | Emerald | 0.31  | Ideal     | E     | SI2     | GIA    | natural | 410   |

We'll go over each column, analysing it's statistics and how it affects the Carat and Price.
# Shape:
Here's a Pivot table I made in Excel,

| shape       | Count of id | Average of carat | Average of price |
| ----------- | ----------- | ---------------- | ---------------- |
| Asscher     | 650         | 1.594123077      | 7966.723077      |
| Radiant     | 1100        | 1.387681818      | 5898.5           |
| Heart       | 1374        | 0.876921397      | 3507.714702      |
| Marquise    | 1740        | 0.638741379      | 1884.655172      |
| Cushion     | 4279        | 1.488186492      | 6622.783361      |
| Princess    | 5135        | 1.044299903      | 3855.004869      |
| Emerald     | 6750        | 0.993897778      | 3964.291852      |
| Pear        | 9221        | 0.748760438      | 2203.720855      |
| Oval        | 12978       | 1.132606719      | 3940.499307      |
| Round       | 76080       | 0.796083859      | 2970.875         |
| Grand Total | 119307      | 0.884168741      | 3286.84327       |

![image](https://user-images.githubusercontent.com/72384743/138226480-53f213f5-d871-4f6b-b8a3-b494a935adc7.png)

![image](https://user-images.githubusercontent.com/72384743/138226689-c64fd373-21bd-4a2c-8595-bb85c4b8d2d0.png)

The Distribution of Shapes can be seen in the Pie Chart.
The Carat and Price definately show Positive Correlation as we can see the Shapes with Higher Carats have Higher Prices.
With Exceptions in 3 shapes where the order of Carats is Emrald, Princess and Oval but the order of Prices is Princess, Oval and Emrald. However, their Prices are almost similar and Carat values too do not differ by much(0.99-1.13).
We do not know Why they are priced higher, Maybe because the Emrald Shape is in More Demand or Maybe it's because People Do not know that the Oval Shape and Princess Shapes have Higher Carat Diamonds. 
# Carat
| Carot Statistics  |Values|
|:------------------|:-----|
| Mean               | 0.884168741 |
| Standard Error     | 0.001943027 |
| Median             | 0.70 |
| Mode               | 0.3 |
| Standard Deviation | 0.67113794 |
| Variance           | 0.450426135 |
| Kurtosis           | 16.43335938 |
| Skewness           | 2.551381862 |
| Range              | 15.07 |
| Minimum            | 0.25 |
| Maximum            | 15.32 |
| Sum                | 105487.52 |
| Count              | 119307 |
