# General overview of the project

This report aims to analyze carbon emissions to examine carbon emissions in various industries. Specifically, identify the sectors with the highest emissions by analyzing them across countries and by year, as well as finding trends.

The database in this project includes 4 tables: product_emissions, companies, countries, industry_groups. Those tables contain information regarding the carbon emissions created during the production of goods.

```sql
SELECT * FROM product_emissions LIMIT 10
```

| id | company\_id | country\_id | industry\_group\_id | year | product\_name | weight\_kg | carbon\_footprint\_pcf | upstream\_percent\_total\_pcf | operations\_percent\_total\_pcf | downstream\_percent\_total\_pcf |
| :---: | :---------: | :---------: | :----------------: | :---: | :----------- | :--------: | :-------------------: | :-------------------------: | :---------------------------: | :---------------------------: |
| 10056-1-2014 | 82 | 28 | 2 | 2014 | Frosted Flakes(R) Cereal | 0.7485 | 2 | 57.50 | 30.00 | 12.50 |
| 10056-1-2015 | 82 | 28 | 15 | 2015 | "Frosted Flakes, 23 oz, produced in Lancaster, PA (one carton)" | 0.7485 | 2 | 57.50 | 30.00 | 12.50 |
| 10222-1-2013 | 83 | 28 | 8 | 2013 | Office Chair | 20.68 | 73 | 80.63 | 17.36 | 2.01 |
| 10261-1-2017 | 14 | 16 | 25 | 2017 | Multifunction Printers | 110 | 1488 | 30.65 | 5.51 | 63.84 |
| 10261-2-2017 | 14 | 16 | 25 | 2017 | Multifunction Printers | 110 | 1818 | 25.08 | 4.51 | 70.41 |
| 10261-3-2017 | 14 | 16 | 25 | 2017 | Multifunction Printers | 110 | 2274 | 20.05 | 3.61 | 76.34 |
| 10324-1-2016 | 15 | 16 | 19 | 2016 | KURALON fiber | 1500 | 10000 | N/a (product with insufficient stage-level data) | N/a (product with insufficient stage-level data) | N/a (product with insufficient stage-level data) |
| 10418-1-2013 | 84 | 9 | 19 | 2013 | Portland Cement | 1000 | 1102 | N/a (product with insufficient stage-level data) | N/a (product with insufficient stage-level data) | N/a (product with insufficient stage-level data) |
| 10661-10-2014 | 85 | 28 | 11 | 2014 | Regular Straight 505® Jeans – Steel (Water | 0.7665 | 15 | N/a (product with insufficient stage-level data) | N/a (product with insufficient stage-level data) | N/a (product with insufficient stage-level data) |
| 10661-10-2015 | 85 | 28 | 6 | 2015 | Regular Straight 505® Jeans – Steel (Water | 0.7665 | 15 | N/a (product with insufficient stage-level data) | N/a (product with insufficient stage-level data) | N/a (product with insufficient stage-level data) |

Those are first 10 rows of table `product_emissions`.

```sql
SELECT * FROM companies LIMIT 10
```

| id | company\_name |
| :---: | :----------- |
| 1 | "Autodesk, Inc." |
| 2 | "Casio Computer Co., Ltd." |
| 3 | "Cisco Systems, Inc." |
| 4 | "CNX Coal Resources, LP" |
| 5 | "Coca-Cola Enterprises, Inc." |
| 6 | "Compañía Española de Petróleos, S.A.U. CEPSA" |
| 7 | "Daikin Industries, Ltd." |
| 8 | "Elitegroup computer systems co., Ltd." |
| 9 | "Fuji Xerox Co., Ltd." |
| 10 | "Gamesa Corporación Tecnológica, S.A." |

Those are first 10 rows of table `companies`.

```sql
SELECT * FROM countries LIMIT 10
```

| id | country\_name |
| :---: | :----------- |
| 1 | Australia |
| 2 | Belgium |
| 3 | Brazil |
| 4 | Canada |
| 5 | Chile |
| 6 | China |
| 7 | Colombia |
| 8 | Finland |
| 9 | France |
| 10 | Germany |

Those are first 10 rows of table `countries`.

```sql
SELECT * FROM industry_groups LIMIT 10
```

| id | industry_group                                                         | 
| :-: | :--------------------------------------------------------------------- | 
| 1  | "Consumer Durables, Household and Personal Products"                   | 
| 2  | "Food, Beverage & Tobacco"                                             | 
| 3  | "Forest and Paper Products - Forestry, Timber, Pulp and Paper, Rubber" | 
| 4  | "Mining - Iron, Aluminum, Other Metals"                                | 
| 5  | "Pharmaceuticals, Biotechnology & Life Sciences"                       | 
| 6  | "Textiles, Apparel, Footwear and Luxury Goods"                         | 
| 7  | Automobiles & Components                                               | 
| 8  | Capital Goods                                                          | 
| 9  | Chemicals                                                              | 
| 10 | Commercial & Professional Services                                     | 

Those are first 10 rows of table `industry_groups`.

# Research results

## 1. Product groups generate the most carbon emissions

From the prepared data set, we can find top 30 products with the highest carbon emissions through the following query:

```sql
SELECT * FROM product_emissions ORDER BY carbon_footprint_pcf DESC LIMIT 30
```

The table below is the result of the above query:

| id           | company_id | country_id | industry_group_id | year | product_name                                                                                                                       | weight_kg | carbon_footprint_pcf | upstream_percent_total_pcf                       | operations_percent_total_pcf                     | downstream_percent_total_pcf                     | 
| :-----------: | :---------: | :---------: | :----------------: | :---: | :--------------------------------------------------------------------------------------------------------------------------------- | :--------: | :-------------------: | :-----------------------------------------------: | :-----------------------------------------------: | :-----------------------------------------------: | 
| 22917-4-2015 | 10         | 23         | 13                | 2015 | Wind Turbine G128 5 Megawats                                                                                                       | 600000    | 3718044              | N/a (product with insufficient stage-level data) | N/a (product with insufficient stage-level data) | N/a (product with insufficient stage-level data) | 
| 22917-5-2015 | 10         | 23         | 13                | 2015 | Wind Turbine G132 5 Megawats                                                                                                       | 600000    | 3276187              | N/a (product with insufficient stage-level data) | N/a (product with insufficient stage-level data) | N/a (product with insufficient stage-level data) | 
| 22917-3-2015 | 10         | 23         | 13                | 2015 | Wind Turbine G114 2 Megawats                                                                                                       | 400000    | 1532608              | N/a (product with insufficient stage-level data) | N/a (product with insufficient stage-level data) | N/a (product with insufficient stage-level data) | 
| 22917-2-2015 | 10         | 23         | 13                | 2015 | Wind Turbine G90 2 Megawats                                                                                                        | 361000    | 1251625              | N/a (product with insufficient stage-level data) | N/a (product with insufficient stage-level data) | N/a (product with insufficient stage-level data) | 
| 8362-1-2016  | 11         | 16         | 7                 | 2016 | Land Cruiser Prado. FJ Cruiser. Dyna trucks. Toyoace.IMV def unit.                                                                 | 2272.33   | 191687               | 2.90                                             | 0.25                                             | 96.85                                            | 
| 904-2-2013   | 34         | 18         | 19                | 2013 | Retaining wall structure with a main wall (sheet pile): 136 tonnes of steel sheet piles and 4 tonnes of tierods per 100 meter wall | 140000    | 167000               | N/a (product with insufficient stage-level data) | N/a (product with insufficient stage-level data) | N/a (product with insufficient stage-level data) | 
| 12134-8-2017 | 17         | 16         | 19                | 2017 | TCDE                                                                                                                               | 12000     | 99075                | 64.95                                            | 34.40                                            | 0.66                                             | 
| 12134-8-2017 | 17         | 16         | 19                | 2017 | TCDE                                                                                                                               | 12000     | 99075                | 64.95                                            | 34.40                                            | 0.66                                             | 
| 4235-30-2016 | 61         | 10         | 7                 | 2016 | Mercedes-Benz GLE (GLE 500 4MATIC)                                                                                                 | 3500      | 91000                | N/a (product with insufficient stage-level data) | N/a (product with insufficient stage-level data) | N/a (product with insufficient stage-level data) | 
| 20527-1-2014 | 141        | 3          | 8                 | 2014 | Electric Motor                                                                                                                     | 90        | 87589                | 0.02                                             | 0.00                                             | 99.98                                            | 
| 4235-32-2016 | 61         | 10         | 7                 | 2016 | Mercedes-Benz S-Class (S 500)                                                                                                      | 2050      | 85000                | N/a (product with insufficient stage-level data) | N/a (product with insufficient stage-level data) | N/a (product with insufficient stage-level data) | 
| 4235-36-2016 | 61         | 10         | 7                 | 2016 | Mercedes-Benz SL (SL 350)                                                                                                          | 2065      | 72000                | N/a (product with insufficient stage-level data) | N/a (product with insufficient stage-level data) | N/a (product with insufficient stage-level data) | 
| 4235-14-2015 | 61         | 10         | 7                 | 2015 | Mercedes-Benz SL-Class                                                                                                             | 1730      | 69000                | N/a (product with insufficient stage-level data) | N/a (product with insufficient stage-level data) | N/a (product with insufficient stage-level data) | 
| 4235-34-2016 | 61         | 10         | 7                 | 2016 | Mercedes-Benz S-Class Hybrid (S 400 h)                                                                                             | 2595      | 66000                | N/a (product with insufficient stage-level data) | N/a (product with insufficient stage-level data) | N/a (product with insufficient stage-level data) | 
| 4235-22-2016 | 61         | 10         | 7                 | 2016 | Mercedes-Benz CLS (350 BlueEFFICIENCY)                                                                                             | 2220      | 60000                | N/a (product with insufficient stage-level data) | N/a (product with insufficient stage-level data) | N/a (product with insufficient stage-level data) | 
| 4235-10-2015 | 61         | 10         | 7                 | 2015 | Mercedes-Benz CLS-Class                                                                                                            | 1790      | 57100                | N/a (product with insufficient stage-level data) | N/a (product with insufficient stage-level data) | N/a (product with insufficient stage-level data) | 
| 4235-7-2015  | 61         | 10         | 7                 | 2015 | Mercedes-Benz S-Class                                                                                                              | 2015      | 54000                | N/a (product with insufficient stage-level data) | N/a (product with insufficient stage-level data) | N/a (product with insufficient stage-level data) | 
| 20527-1-2013 | 141        | 3          | 8                 | 2013 | Electric Motor                                                                                                                     | 90        | 53058                | 0.01                                             | 0.00                                             | 99.99                                            | 
| 4226-2-2017  | 7          | 16         | 8                 | 2017 | Commercial Air Conditioner                                                                                                         | 149.685   | 51066                | 0.98                                             | 0.13                                             | 98.88                                            | 
| 4235-33-2016 | 61         | 10         | 7                 | 2016 | Mercedes-Benz S-Class Hybrid (S 300 BlueTEC HYBRID)                                                                                | 2715      | 51000                | N/a (product with insufficient stage-level data) | N/a (product with insufficient stage-level data) | N/a (product with insufficient stage-level data) | 
| 4235-3-2015  | 61         | 10         | 7                 | 2015 | Mercedes-Benz C-Class                                                                                                              | 1505      | 50500                | N/a (product with insufficient stage-level data) | N/a (product with insufficient stage-level data) | N/a (product with insufficient stage-level data) | 
| 4235-23-2016 | 61         | 10         | 7                 | 2016 | Mercedes-Benz E-Class (E 200)                                                                                                      | 1500      | 50000                | N/a (product with insufficient stage-level data) | N/a (product with insufficient stage-level data) | N/a (product with insufficient stage-level data) | 
| 4235-13-2015 | 61         | 10         | 7                 | 2015 | Mercedes-Benz GLK-Class                                                                                                            | 1850      | 48800                | N/a (product with insufficient stage-level data) | N/a (product with insufficient stage-level data) | N/a (product with insufficient stage-level data) | 
| 4235-5-2015  | 61         | 10         | 7                 | 2015 | Mercedes-Benz E-Class Saloon                                                                                                       | 1680      | 47200                | N/a (product with insufficient stage-level data) | N/a (product with insufficient stage-level data) | N/a (product with insufficient stage-level data) | 
| 4235-37-2016 | 61         | 10         | 7                 | 2016 | Mercedes-Benz SLC (SLK 200 BlueEFFICIENCY)                                                                                         | 2015      | 45000                | N/a (product with insufficient stage-level data) | N/a (product with insufficient stage-level data) | N/a (product with insufficient stage-level data) | 
| 4235-6-2015  | 61         | 10         | 7                 | 2015 | Mercedes-Benz M-Class - Passenger Car                                                                                              | 2110      | 43600                | N/a (product with insufficient stage-level data) | N/a (product with insufficient stage-level data) | N/a (product with insufficient stage-level data) | 
| 4235-24-2016 | 61         | 10         | 7                 | 2016 | Mercedes-Benz E-Class (E 220 d (Estate))                                                                                           | 2320      | 41000                | N/a (product with insufficient stage-level data) | N/a (product with insufficient stage-level data) | N/a (product with insufficient stage-level data) | 
| 4235-11-2015 | 61         | 10         | 7                 | 2015 | Mercedes-Benz E-Class BlueTEC Hybrid                                                                                               | 1735      | 40600                | N/a (product with insufficient stage-level data) | N/a (product with insufficient stage-level data) | N/a (product with insufficient stage-level data) | 
| 20523-1-2014 | 140        | 28         | 5                 | 2014 | Alliance (HPLC)                                                                                                                    | 59        | 40215                | 1.41                                             | 0.30                                             | 98.28                                            | 
| 4226-3-2017  | 7          | 16         | 8                 | 2017 | Light commercial Air Conditioner                                                                                                   | 128.367   | 39653                | 0.70                                             | 0.10                                             | 99.21                                            | 


📄 INSIGHT: From the results table, we can see that the carbon emission level of wind turbine products is the highest on the list. Next are automobile products. They belong to the industry groups Automobiles & Components, Electrical Equipment and Machinery, and Materials the most.

## 2. The industries with the highest contribution to carbon emissions

To find the industry group with the highest carbon emissions, use the following sql query:

 ```sql
SELECT industry_group_id , industry_group, SUM(carbon_footprint_pcf) as sum_pcfs
FROM product_emissions INNER JOIN industry_groups 
ON product_emissions.industry_group_id = industry_groups.id
GROUP BY industry_group_id ORDER BY 3 DESC
```

We will get a result table as below:

| industry_group_id | industry_group                                                         | sum_pcfs | 
| :----------------: | :--------------------------------------------------------------------- | :-------: | 
| 13                | Electrical Equipment and Machinery                                     | 9801558  | 
| 7                 | Automobiles & Components                                               | 2582264  | 
| 19                | Materials                                                              | 577595   | 
| 25                | Technology Hardware & Equipment                                        | 363776   | 
| 8                 | Capital Goods                                                          | 258712   | 
| 2                 | "Food, Beverage & Tobacco"                                             | 111131   | 
| 5                 | "Pharmaceuticals, Biotechnology & Life Sciences"                       | 72486    | 
| 9                 | Chemicals                                                              | 62369    | 
| 24                | Software & Services                                                    | 46544    | 
| 20                | Media                                                                  | 23017    | 
| 14                | Energy                                                                 | 10774    | 
| 3                 | "Forest and Paper Products - Forestry, Timber, Pulp and Paper, Rubber" | 8909     | 
| 4                 | "Mining - Iron, Aluminum, Other Metals"                                | 8181     | 
| 11                | Consumer Durables & Apparel                                            | 7309     | 
| 10                | Commercial & Professional Services                                     | 5265     | 
| 12                | Containers & Packaging                                                 | 2988     | 
| 27                | Tires                                                                  | 2022     | 
| 16                | Food & Staples Retailing                                               | 1481     | 
| 1                 | "Consumer Durables, Household and Personal Products"                   | 931      | 
| 26                | Telecommunication Services                                             | 418      | 
| 6                 | "Textiles, Apparel, Footwear and Luxury Goods"                         | 387      | 
| 30                | Utilities                                                              | 244      | 
| 29                | Trading Companies & Distributors and Commercial Services & Supplies    | 239      | 
| 15                | Food & Beverage Processing                                             | 141      | 
| 17                | Gas Utilities                                                          | 122      | 
| 22                | Semiconductors & Semiconductor Equipment                               | 54       | 
| 21                | Retailing                                                              | 30       | 
| 23                | Semiconductors & Semiconductors Equipment                              | 3        | 
| 28                | Tobacco                                                                | 1        | 
| 18                | Household & Personal Products                                          | 0        | 


📄 INSIGHT: So, the industries that contribute the most to carbon emissions into the environment are industries with id codes 7, 13, 19.

## 3. The companies with the highest contribution to carbon emissions

To find the company with the highest carbon emissions during its operations, use the query below: 

```sql
SELECT company_id, company_name, SUM(carbon_footprint_pcf) as sum_pcfs
FROM product_emissions INNER JOIN companies
ON product_emissions.company_id = companies.id
GROUP BY company_id ORDER BY 3 DESC LIMIT 10
```

The results of the query are shown in the following table: 

| company_id | company_name                            | sum_pcfs | 
| :---------: | :-------------------------------------- | :------: | 
| 10         | "Gamesa Corporación Tecnológica, S.A."  | 9778464 | 
| 61         | Daimler AG                              | 1594300 | 
| 139        | Volkswagen AG                           | 655960  | 
| 17         | "Mitsubishi Gas Chemical Company, Inc." | 212016  | 
| 11         | "Hino Motors, Ltd."                     | 191687  | 
| 34         | Arcelor Mittal                          | 167007  | 
| 141        | Weg S/A                                 | 160655  | 
| 71         | General Motors Company                  | 137007  | 
| 16         | "Lexmark International, Inc."           | 132012  | 
| 7          | "Daikin Industries, Ltd."               | 105600  | 

📄 INSIGHT: So the companies listed in the results table are the top companies in contributing carbon emissions to the environment. Most of them belong to the automobile manufacturing sector.

## 4. The countries with the highest contribution to carbon emissions

To find the countries with the highest carbon emissions, use the query below: 

```sql
SELECT country_id, country_name, SUM(carbon_footprint_pcf) as sum_pcfs
FROM product_emissions INNER JOIN countries
ON product_emissions.country_id = countries.id
GROUP BY country_id ORDER BY 3 DESC LIMIT 10
```

Executing the query, we obtain the results table below:

| country_id | country_name | sum_pcfs | 
| :---------: | :----------- | :------: | 
| 23         | Spain        | 9786130 | 
| 10         | Germany      | 2251225 | 
| 16         | Japan        | 653237  | 
| 28         | USA          | 518381  | 
| 22         | South Korea  | 186965  | 
| 3          | Brazil       | 169337  | 
| 18         | Luxembourg   | 167007  | 
| 20         | Netherlands  | 70417   | 
| 26         | Taiwan       | 62875   | 
| 12         | India        | 24574   | 

📄 INSIGHT: We can see that the countries leading economically and holding key positions in the field of industrial production are the countries with the highest carbon emissions.

## 5. The trend of carbon footprints (PCFs) over the years

To find the trend of PCFs through each year, use the sql statement below: 

```sql
SELECT year, SUM(carbon_footprint_pcf) as sum_pcfs FROM product_emissions GROUP BY year
```

What we got here:

| year | sum_pcfs | 
| :---: | :------- | 
| 2013 | 503857   | 
| 2014 | 624226   | 
| 2015 | 10840415 | 
| 2016 | 1640182  | 
| 2017 | 340271   | 

📄 INSIGHT: Every year carbon emissions increase according to the development of the world economy. In 2015 alone, this number reached the largest level on the list because wind turbines were produced and operated 24/7 on a large scale.

## 6. Carbon emission reduction over the years of each industry

To find the year-over-year carbon emission reduction of each industry, use the following query:

```sql
SELECT industry_group_id, industry_group, year, SUM(carbon_footprint_pcf) as sum_pcfs
FROM product_emissions INNER JOIN industry_groups 
ON product_emissions.industry_group_id = industry_groups.id 
GROUP BY industry_group, year
```

Results table will look like below:

| industry_group_id | industry_group                                                         | year | sum_pcfs | 
| :----------------: | :--------------------------------------------------------------------- | :---: | :-------: | 
| 1                 | "Consumer Durables, Household and Personal Products"                   | 2015 | 931      | 
| 2                 | "Food, Beverage & Tobacco"                                             | 2013 | 4995     | 
| 2                 | "Food, Beverage & Tobacco"                                             | 2014 | 2685     | 
| 2                 | "Food, Beverage & Tobacco"                                             | 2015 | 0        | 
| 2                 | "Food, Beverage & Tobacco"                                             | 2016 | 100289   | 
| 2                 | "Food, Beverage & Tobacco"                                             | 2017 | 3162     | 
| 3                 | "Forest and Paper Products - Forestry, Timber, Pulp and Paper, Rubber" | 2015 | 8909     | 
| 4                 | "Mining - Iron, Aluminum, Other Metals"                                | 2015 | 8181     | 
| 5                 | "Pharmaceuticals, Biotechnology & Life Sciences"                       | 2013 | 32271    | 
| 5                 | "Pharmaceuticals, Biotechnology & Life Sciences"                       | 2014 | 40215    | 
| 6                 | "Textiles, Apparel, Footwear and Luxury Goods"                         | 2015 | 387      | 
| 7                 | Automobiles & Components                                               | 2013 | 130189   | 
| 7                 | Automobiles & Components                                               | 2014 | 230015   | 
| 7                 | Automobiles & Components                                               | 2015 | 817227   | 
| 7                 | Automobiles & Components                                               | 2016 | 1404833  | 
| 8                 | Capital Goods                                                          | 2013 | 60190    | 
| 8                 | Capital Goods                                                          | 2014 | 93699    | 
| 8                 | Capital Goods                                                          | 2015 | 3505     | 
| 8                 | Capital Goods                                                          | 2016 | 6369     | 
| 8                 | Capital Goods                                                          | 2017 | 94949    | 
| 9                 | Chemicals                                                              | 2015 | 62369    | 
| 10                | Commercial & Professional Services                                     | 2013 | 1157     | 
| 10                | Commercial & Professional Services                                     | 2014 | 477      | 
| 10                | Commercial & Professional Services                                     | 2016 | 2890     | 
| 10                | Commercial & Professional Services                                     | 2017 | 741      | 
| 11                | Consumer Durables & Apparel                                            | 2013 | 2867     | 
| 11                | Consumer Durables & Apparel                                            | 2014 | 3280     | 
| 11                | Consumer Durables & Apparel                                            | 2016 | 1162     | 
| 12                | Containers & Packaging                                                 | 2015 | 2988     | 
| 13                | Electrical Equipment and Machinery                                     | 2015 | 9801558  | 
| 14                | Energy                                                                 | 2013 | 750      | 
| 14                | Energy                                                                 | 2016 | 10024    | 
| 15                | Food & Beverage Processing                                             | 2015 | 141      | 
| 16                | Food & Staples Retailing                                               | 2014 | 773      | 
| 16                | Food & Staples Retailing                                               | 2015 | 706      | 
| 16                | Food & Staples Retailing                                               | 2016 | 2        | 
| 17                | Gas Utilities                                                          | 2015 | 122      | 
| 18                | Household & Personal Products                                          | 2013 | 0        | 
| 19                | Materials                                                              | 2013 | 200513   | 
| 19                | Materials                                                              | 2014 | 75678    | 
| 19                | Materials                                                              | 2016 | 88267    | 
| 19                | Materials                                                              | 2017 | 213137   | 
| 20                | Media                                                                  | 2013 | 9645     | 
| 20                | Media                                                                  | 2014 | 9645     | 
| 20                | Media                                                                  | 2015 | 1919     | 
| 20                | Media                                                                  | 2016 | 1808     | 
| 21                | Retailing                                                              | 2014 | 19       | 
| 21                | Retailing                                                              | 2015 | 11       | 
| 22                | Semiconductors & Semiconductor Equipment                               | 2014 | 50       | 
| 22                | Semiconductors & Semiconductor Equipment                               | 2016 | 4        | 
| 23                | Semiconductors & Semiconductors Equipment                              | 2015 | 3        | 
| 24                | Software & Services                                                    | 2013 | 6        | 
| 24                | Software & Services                                                    | 2014 | 146      | 
| 24                | Software & Services                                                    | 2015 | 22856    | 
| 24                | Software & Services                                                    | 2016 | 22846    | 
| 24                | Software & Services                                                    | 2017 | 690      | 
| 25                | Technology Hardware & Equipment                                        | 2013 | 61100    | 
| 25                | Technology Hardware & Equipment                                        | 2014 | 167361   | 
| 25                | Technology Hardware & Equipment                                        | 2015 | 106157   | 
| 25                | Technology Hardware & Equipment                                        | 2016 | 1566     | 
| 25                | Technology Hardware & Equipment                                        | 2017 | 27592    | 
| 26                | Telecommunication Services                                             | 2013 | 52       | 
| 26                | Telecommunication Services                                             | 2014 | 183      | 
| 26                | Telecommunication Services                                             | 2015 | 183      | 
| 27                | Tires                                                                  | 2015 | 2022     | 
| 28                | Tobacco                                                                | 2015 | 1        | 
| 29                | Trading Companies & Distributors and Commercial Services & Supplies    | 2015 | 239      | 
| 30                | Utilities                                                              | 2013 | 122      | 
| 30                | Utilities                                                              | 2016 | 122      | 

📄 INSIGHT: We see that industry groups with ids 2, 10, 11, 16, 20, 22, 24 have significantly reduced carbon emissions each year from 2013-2017.
