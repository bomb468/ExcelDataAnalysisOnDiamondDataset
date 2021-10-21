# ExcelDataAnalysisOnDiamondDataset
Took a Dataset Analyzed it as much as I could using Excel. All the Graphs and Tables are Taken from the Excel file in the repository.

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
|type|Natural or lab-created diamonds string|
|date_fetched|Date the data was fetched date|

It has 119307 rows and 11 columns out of which id, url, report(only has one unique value) and data_fetched are useless for data analysis so the first thing we do is remove those Columns.

After Removing those, the data looks like this :

| id       | shape   | carat | cut       | color | clarity | report | type    | price |
| -------- | ------- | ----- | --------- | ----- | ------- | ------ | ------- | ----- |
| 10086429 | Round   | 0.3   | Very Good | J     | SI2     | GIA    | natural | 400   |
| 10016334 | Emerald | 0.31  | Ideal     | I     | SI1     | GIA    | natural | 400   |
| 9947216  | Emerald | 0.3   | Ideal     | I     | VS2     | GIA    | natural | 400   |
| 10083437 | Round   | 0.3   | Ideal     | I     | SI2     | GIA    | natural | 400   |
| 9946136  | Emerald | 0.3   | Ideal     | I     | SI1     | GIA    | natural | 400   |
| 10070154 | Emerald | 0.31  | Ideal     | E     | SI2     | GIA    | natural | 410   |

We'll go over each column, analyzing its statistics and how it affects the Carat and Price.
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

![image](https://user-images.githubusercontent.com/72384743/138255715-4645b8ce-61bb-404d-9ec3-feb56c6e429d.png)

The Distribution of Shapes can be seen in the Pie Chart.
The Carat and Price show Positive Correlation as we can see the Shapes with Higher Carats have Higher Prices.
With Exceptions in 3 shapes where the order of Carats is Emerald, Princess, and Oval but the order of Prices is Princess, Oval, and Emerald. However, their prices are almost similar and Carat values too do not differ by much(0.99-1.13).
We do not know Why they are priced higher, Maybe because the Emerald Shape is in More Demand or Maybe it's because People Do not know that the Oval Shape and Princess Shapes have Higher Carat Diamonds. 
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

![image](https://user-images.githubusercontent.com/72384743/138249034-b07a9e19-e182-41e7-974e-d9bb26ad9237.png)

Many OutLiers.

Although I could have just used the built-in Data Analytics button for getting these properties. I decided to use the built-in formulas instead. Here are the Formulas I used:
| Statistic          | Value                      |
| ------------------ | -------------------------- |
| Mean               | SUM(Carot)/COUNT(Carot)    |
| Standard Error     | STDEV.P(Carot)/SQRT(Carot) |
| Median             | MEDIAN(Carot)              |
| Mode               | MODE(Carot)                |
| Standard Deviation | STDEV.P(Carot)             |
| Variance           | VAR.P(Carot)               |
| Kurtosis           | KURT(Carot)                |
| Skewness           | SKEW(Carot)                |
| Range              | MAX(Carot)-MIN(Carot)      |
| Minimum            | MIN(Carot)                 |
| Maximum            | MAX(Carot)                 |
| Sum                | SUM(Carot)                 |
| Count              | COUNT(Carot)               |

Along basic Carot vs Price Scatter Plot I also Plotted the Carot Square vs Price Scatter Plot because the trend in the Carot vs Price Plot didn't seem linear and As soon as I squared the Carot, The Trend became Linear. The Plot showed obvious HeteroSkestasticity but It should show GoodPositive Correlation Since we expect that the Higher the Carot, The Higher The Price.

|         | price    | carat   | carat^2 |
| ------- | -------- | ------- | ------- |
| price   | 1        |         |         |
| carat   | 0.555578 | 1       |         |
| carat^2 | 0.74548  | 0.83238 | 1       |

The Formula I used for every Cell was Simple, CORR(Array1, Array2).

It seems like using Carot Square to Compare the Prices is better than using Carot, because Carot Square and Price have Better Correlation(although Carot vs Price Correlation is not that bad either).
# Cut
| cut         | Count of id | Average of carat | Average of price |
| ----------- | ----------- | ---------------- | ---------------- |
| Fair        | 334         | 0.845988024      | 3125.299401      |
| Good        | 3398        | 0.853781636      | 3549.117128      |
| Very Good   | 20914       | 0.840739696      | 2798.297791      |
| Ideal       | 39417       | 0.986957912      | 2966.643073      |
| Super Ideal | 55244       | 0.829368981      | 3685.104084      |
| Grand Total | 119307      | 0.884168741      | 3286.84327       |

![image](https://user-images.githubusercontent.com/72384743/138255997-cc1ab55a-8eb0-460f-acc5-a55a9dfed2d8.png)

Order of Avg Carot is Very Different from Their Prices.
Super Ideal has the least Avg carot and the Avg highest Price.
Ideal has Avg Prices Lesser than Fair And Good which is Very Surprising as we'd have expected it to be better than them.
Very Good has the Least Avg Price.
Also, I did try and Compare Shape and Cut with Prices(I made this list by Listing the order of Avg Prices of Cut for each Shape). The Cut Order did Vary in Many Shapes(which is a good thing because the more similar the columns are, the more Correlation they have).
| correct  | Very Good | Ideal     | Fair      | Good        | Super Ideal |
| -------- | --------- | --------- | --------- | ----------- | ----------- |
| Marquise | Good      | Ideal     | Very Good | Fair        | Super Ideal |
| Pear     | Good      | Very Good | Ideal     | Fair        | Super Ideal |
| Round    | Very Good | Good      | Ideal     | Fair        | Super Ideal |
| Heart    | Very Good | Ideal     | Fair      | Good        | Super Ideal |
| Princess | Fair      | Ideal     | Very Good | Good        | Super Ideal |
| Oval     | Very Good | Ideal     | Good      | Super Ideal | Fair        |
| Emerald  | Fair      | Ideal     | Very Good | Good        | Super Ideal |
| Radiant  | Fair      | Very Good | Ideal     | Super Ideal | Good        |
| Cushion  | Very Good | Good      | Ideal     | Fair        | Super Ideal |
| Asscher  | Very Good | Fair      | Good      | Ideal       | Super Ideal |

It does Look Like The Order of Prices in Cut Varies Due to its Shape.
# Color
| color       | Count of id | Average of carat | Average of price |
| ----------- | ----------- | ---------------- | ---------------- |
| E           | 24730       | 0.726021027      | 2922.433886      |
| I           | 14409       | 1.192521341      | 3165.362621      |
| J           | 9012        | 1.320267421      | 3200.236352      |
| F           | 19833       | 0.80482277       | 3299.234105      |
| D           | 20896       | 0.641661083      | 3439.418549      |
| G           | 17559       | 0.926823851      | 3551.374224      |
| H           | 12868       | 0.995292975      | 3556.030463      |
| Grand Total | 119307      | 0.884168741      | 3286.84327       |

![image](https://user-images.githubusercontent.com/72384743/138258150-02286f41-74e7-458c-a640-d9e3397ca884.png)

Although the Avg Carots Have a Varying Range of 0.6-1.3, the Avg Prices Have a Varying Range of 2750-3500(I expected it to be more).
Even the Order of Prices is Different from the Carot.
I also Compared Color with Shape.
| correct | Marquise | Pear     | Round   | Heart    | Princess | Oval     | Emerald  | Radiant | Cushion | Asscher |
| ------- | -------- | -------- | ------- | -------- | -------- | -------- | -------- | ------- | ------- | ------- |
| E       | Marquise | Pear     | Round   | Princess | Heart    | Oval     | Emerald  | Asscher | Cushion | Radiant |
| I       | Marquise | Pear     | Round   | Emerald  | Heart    | Oval     | Princess | Radiant | Cushion | Asscher |
| J       | Marquise | Pear     | Emerald | Radiant  | Heart    | Round    | Princess | Oval    | Cushion | Asscher |
| F       | Marquise | Pear     | Round   | Oval     | Princess | Heart    | Emerald  | Radiant | Asscher | Cushion |
| D       | Marquise | Round    | Pear    | Heart    | Oval     | Emerald  | Princess | Radiant | Cushion | Asscher |
| G       | Pear     | Marquise | Round   | Heart    | Princess | Emerald  | Oval     | Radiant | Cushion | Asscher |
| H       | Marquise | Pear     | Heart   | Emerald  | Round    | Princess | Radiant  | Oval    | Cushion | Asscher |

And Color with Cut.
| correct | Very Good | Ideal     | Fair        | Good        | Super Ideal |
| ------- | --------- | --------- | ----------- | ----------- | ----------- |
| E       | Very Good | Ideal     | Fair        | Super Ideal | Good        |
| I       | Fair      | Ideal     | Very Good   | Good        | Super Ideal |
| J       | Fair      | Very Good | Ideal       | Good        | Super Ideal |
| F       | Very Good | Fair      | Ideal       | Good        | Super Ideal |
| D       | Very Good | Ideal     | Super Ideal | Good        | Fair        |
| G       | Fair      | Very Good | Good        | Ideal       | Super Ideal |
| H       | Fair      | Ideal     | Good        | Very Good   | Super Ideal |

It Looks Like The Color Affects the Price Order of the Cut More than the Shape but Both are not Same as The Avg Price order of Only Shape and Cut and Vary in many Rows.
# Clarity
| clarity     | Count of id | Average of carat | Average of price |
| ----------- | ----------- | ---------------- | ---------------- |
| FL          | 202         | 1.149356436      | 29821.18812      |
| IF          | 3667        | 0.581213526      | 4085.595855      |
| SI1         | 21205       | 0.880634284      | 2660.800755      |
| SI2         | 12771       | 1.014284708      | 3444.39668       |
| VS1         | 27259       | 0.958553505      | 3458.038079      |
| VS2         | 26440       | 0.919528366      | 3050.307489      |
| VVS1        | 10534       | 0.660311373      | 3586.5075        |
| VVS2        | 17229       | 0.818358581      | 3368.385861      |
| Grand Total | 119307      | 0.884168741      | 3286.84327       |

![image](https://user-images.githubusercontent.com/72384743/138264386-79d5e345-de8a-4f8f-b5eb-7997337dac34.png)

The Order of Avg Carot is Different in every place except FL which has the lowest count, highest Avg Carot and highest Avg Price.
I also Compared Clarity with shape.
| correct | Marquise | Pear     | Round    | Heart    | Princess | Oval     | Emerald  | Radiant | Cushion  | Asscher  |
| ------- | -------- | -------- | -------- | -------- | -------- | -------- | -------- | ------- | -------- | -------- |
| SI1     | Marquise | Pear     | Emerald  | Princess | Round    | Heart    | Asscher  | Oval    | Radiant  | Cushion  |
| VS2     | Marquise | Pear     | Round    | Heart    | Oval     | Princess | Emerald  | Radiant | Cushion  | Asscher  |
| VVS2    | Marquise | Pear     | Round    | Oval     | Princess | Emerald  | Heart    | Radiant | Cushion  | Asscher  |
| SI2     | Emerald  | Marquise | Heart    | Pear     | Round    | Asscher  | Princess | Radiant | Oval     | Cushion  |
| VS1     | Marquise | Pear     | Round    | Oval     | Heart    | Princess | Emerald  | Radiant | Cushion  | Asscher  |
| VVS1    | Marquise | Pear     | Emerald  | Round    | Heart    | Princess | Oval     | Radiant | Cushion  | Asscher  |
| IF      | Round    | Marquise | Oval     | Emerald  | Heart    | Pear     | Radiant  | Asscher | Cushion  | Princess |
| FL      | Round    | Pear     | Marquise | Asscher  | Heart    | Oval     | Cushion  | Emerald | Princess | Radiant  |

Compared Clarity with Cut.
| correct | Very Good   | Ideal     | Fair        | Good        | Super Ideal |
| ------- | ----------- | --------- | ----------- | ----------- | ----------- |
| SI1     | Ideal       | Very Good | Fair        | Good        | Super Ideal |
| VS2     | Very Good   | Ideal     | Super Ideal | Good        | Fair        |
| VVS2    | Fair        | Very Good | Ideal       | Super Ideal | Good        |
| SI2     | Fair        | Very Good | Good        | Ideal       | Super Ideal |
| VS1     | Fair        | Ideal     | Very Good   | Super Ideal | Good        |
| VVS1    | Very Good   | Ideal     | Super Ideal | Fair        | Good        |
| IF      | Super Ideal | Very Good | Ideal       | Good        | Fair        |
| FL      | Ideal       | Very Good | Super Ideal | Good        | Fair        |
Compared Clarity With Color.
| correct | E | I | J | F | D | G | H |
| ------- | - | - | - | - | - | - | - |
| SI1     | E | D | F | G | I | J | H |
| VS2     | D | E | J | I | F | H | G |
| VVS2    | I | J | H | G | E | F | D |
| SI2     | E | F | D | J | G | I | H |
| VS1     | I | D | J | H | F | E | G |
| VVS1    | J | I | G | E | F | H | D |
| IF      | I | E | H | F | G | J | D |
| FL      | J | H | I | E | F | G | D |

Shape, Cut and Color all Affect the order of Avg Prices of Clarity.
# report
| report      | Count of id | Average of carat | Average of price |
| ----------- | ----------- | ---------------- | ---------------- |
| HRD         | 1153        | 1.200511709      | 2818.447528      |
| GCAL        | 5782        | 1.43374265       | 4553.334486      |
| IGI         | 43590       | 1.190347327      | 3101.786878      |
| GIA         | 68782       | 0.638629147      | 3305.508273      |
| Grand Total | 119307      | 0.884168741      | 3286.84327       |

![image](https://user-images.githubusercontent.com/72384743/138266757-1ab1c257-e2f1-4fb3-ad82-9a691fe66f5d.png)

GIA and HRD Do not follow the Avg Carrot Trend.
As Before, I compared Report with shape.
| correct | Marquise | Pear     | Round   | Heart | Princess | Oval     | Emerald  | Radiant | Cushion | Asscher |
| ------- | -------- | -------- | ------- | ----- | -------- | -------- | -------- | ------- | ------- | ------- |
| HRD     | Heart    | Pear     | Radiant | Round | Emerald  | Marquise | Princess | Oval    | Cushion |         |
| IGI     | Pear     | Marquise | Round   | Oval  | Emerald  | Princess | Heart    | Radiant | Asscher | Cushion |
| GIA     | Marquise | Round    | Pear    | Heart | Emerald  | Princess | Oval     | Cushion | Radiant | Asscher |
| GCAL    | Marquise | Pear     | Round   | Oval  | Heart    | Princess | Cushion  | Radiant | Asscher | Emerald |

Report with Cut
| correct | Very Good | Ideal       | Fair      | Good        | Super Ideal |
| ------- | --------- | ----------- | --------- | ----------- | ----------- |
| HRD     | Ideal     | Super Ideal | Fair      | Very Good   | Good        |
| IGI     | Very Good | Good        | Ideal     | Super Ideal | Fair        |
| GIA     | Fair      | Ideal       | Very Good | Super Ideal | Good        |
| GCAL    | Good      | Very Good   | Ideal     | Super Ideal |             |

Report with Color
| correct | E | I | J | F | D | G | H |
| ------- | - | - | - | - | - | - | - |
| HRD     | I | H | J | E | G | D | F |
| IGI     | I | J | H | E | G | F | D |
| GIA     | E | F | D | G | I | H | J |
| GCAL    | J | F | I | G | H | E | D |

Report with Clarity
| correct | SI1  | VS2 | VVS2 | SI2  | VS1  | VVS1 | IF | FL |
| ------- | ---- | --- | ---- | ---- | ---- | ---- | -- | -- |
| HRD     | VVS2 | VS2 | VS1  | SI2  | SI1  | VVS1 | IF |    |
| IGI     | SI1  | VS2 | SI2  | VS1  | VVS2 | VVS1 | IF |    |
| GIA     | SI1  | VS2 | VS1  | VVS2 | VVS1 | SI2  | IF | FL |
| GCAL    | SI2  | SI1 | VS2  | VS1  | VVS2 | VVS1 |    |    |
# Type
| type        | Count of id | Average of carat | Average of price |
| ----------- | ----------- | ---------------- | ---------------- |
| lab         | 48994       | 1.216354656      | 3184.541372      |
| natural     | 70313       | 0.652702061      | 3358.127089      |
| Grand Total | 119307      | 0.884168741      | 3286.84327       |

![image](https://user-images.githubusercontent.com/72384743/138268121-06c70366-0219-4de8-ba4f-38c357832383.png)

The Natural diamonds have Higher Avg Price(significantly) even though they have Lower Avg Carat.
Compared Type with shape.
| correct | Marquise | Pear     | Round | Heart | Princess | Oval     | Emerald | Radiant | Cushion | Asscher |
| ------- | -------- | -------- | ----- | ----- | -------- | -------- | ------- | ------- | ------- | ------- |
| lab     | Pear     | Marquise | Round | Oval  | Princess | Heart    | Emerald | Radiant | Asscher | Cushion |
| natural | Marquise | Round    | Pear  | Heart | Emerald  | Princess | Oval    | Cushion | Radiant | Asscher |

Compared Type with Cut.
| correct | Very Good | Ideal     | Fair      | Good        | Super Ideal |
| ------- | --------- | --------- | --------- | ----------- | ----------- |
| lab     | Good      | Very Good | Ideal     | Super Ideal | Fair        |
| natural | Fair      | Ideal     | Very Good | Super Ideal | Good        |

Compared Type with Color
| correct | E | I | J | F | D | G | H |
| ------- | - | - | - | - | - | - | - |
| lab     | I | J | H | E | F | G | D |
| natural | E | F | D | G | I | J | H |

Compared type With Clarity
| correct | SI1 | VS2 | VVS2 | SI2  | VS1  | VVS1 | IF  | FL |
| ------- | --- | --- | ---- | ---- | ---- | ---- | --- | -- |
| lab     | SI2 | SI1 | VS2  | VVS2 | VS1  | VVS1 | IF  |    |
| natural | SI1 | VS2 | VVS2 | VS1  | VVS1 | IF   | SI2 | FL |

Compared Type with the report
| correct | HRD  | IGI | GIA | GCAL |
| ------- | ---- | --- | --- | ---- |
| lab     | GCAL | HRD | IGI |      |
| natural | GIA  | HRD | IGI |      |

Nothing We haven't seen before, Type also Affects Orders of Every other non-numeric Column.
# Price
| Price Statistic    | Value|
|:-------------------|:-----|
| Mean               | 3286.84327 |
| Standard Error     | 26.38805471 |
| Median             | 1770.00 |
| Mode               | 780 |
| Standard Deviation | 9114.657178 |
| Variance           | 83076975.47 |
| Kurtosis           | 5642.262123 |
| Skewness           | 54.8601096 |
| Range              | 1348450.00 |
| Minimum            | 270.00 |
| Maximum            | 1348720.00 |
| Sum                | 392143410.00 |
| Count              | 119307 |

![image](https://user-images.githubusercontent.com/72384743/138270242-6602c257-900a-4bc1-a379-cc199226d228.png)

![image](https://user-images.githubusercontent.com/72384743/138270476-6d38b39c-ed4f-4302-b28e-1fee0e1cdad8.png)

Most of the Data is Between 1000-3500 Range. Many Outliers.
Analysis of Each Column is Done and Here are Some Extra Statistics to Look at:
| Avg Prices of | Have Range of |
| ------------- | ------------- |
| Clarity       | 27160.38736   |
| Shape         | 6082.067905   |
| Report        | 1734.886958   |
| Cut           | 886.8062927   |
| Color         | 633.5965772   |
| Type          | 173.5857165   |

| Avg Prices of | Have Standard Deviation of |
| ------------- | -------------------------- |
| Clarity       | 8753.289719                |
| Shape         | 1856.191783                |
| Report        | 662.9906315                |
| Cut           | 310.5664658                |
| Color         | 213.3571374                |
| Type          | 86.79285823                |
