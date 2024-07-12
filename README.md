# General overview of the project

This report aims to analyze carbon emissions to examine carbon emissions in various industries. Specifically, identify the sectors with the highest emissions by analyzing them across countries and by year, as well as finding trends.

The database in this project includes 4 tables: product\_emissions, companies, countries, industry\_groups. Those tables contain information regarding the carbon emissions created during the production of goods.

```sql
SELECT * FROM product_emission LIMIT 10
```

| id | company\_id | country\_id | industry\_group\_id | year | product\_name | weight\_kg | carbon\_footprint\_pcf | upstream\_percent\_total\_pcf | operations\_percent\_total\_pcf | downstream\_percent\_total\_pcf |
| :---: | :---------: | :---------: | :----------------: | :---: | :-----------: | :--------: | :-------------------: | :-------------------------: | :---------------------------: | :---------------------------: |
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

Those are first 10 rows of table `"product_emissions"`

```sql
SELECT * FROM companies LIMIT 10
```

| id | company\_name |
| :---: | :-----------: |
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

Those are first 10 rows of table `"companies"`

```sql
SELECT * FROM countries LIMIT 10
```

| id | country\_name |
| :---: | :-----------: |
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

Those are first 10 rows of table `"countries"`

```sql
SELECT * FROM industry_groups LIMIT 10
```

| id | industry_group                                                         | 
| :-: | :---------------------------------------------------------------------: | 
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

Those are first 10 rows of table `"industry_groups"`

# Research results

## Product groups generate the most carbon emissions

From the prepared data set, we can find top 30 products with the highest carbon emissions through the following query.

```sql
SELECT * FROM product_emissions ORDER BY carbon_footprint_pcf DESC LIMIT 30
```

The table below is the result of the above query

| id           | company_id | country_id | industry_group_id | year | product_name                                                                                                                       | weight_kg | carbon_footprint_pcf | upstream_percent_total_pcf                       | operations_percent_total_pcf                     | downstream_percent_total_pcf                     | 
| -----------: | ---------: | ---------: | ----------------: | ---: | ---------------------------------------------------------------------------------------------------------------------------------: | --------: | -------------------: | -----------------------------------------------: | -----------------------------------------------: | -----------------------------------------------: | 
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



