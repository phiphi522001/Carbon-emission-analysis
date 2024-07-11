# General overview of the project

This report aims to analyze carbon emissions to examine carbon emissions in various industries. Specifically, identify the sectors with the highest emissions by analyzing them across countries and by year, as well as finding trends.

The database in this project includes 4 tables: product\_emissions, companies, countries, industry\_groups. Those tables contain information regarding the carbon emissions created during the production of goods.

```sql
SELECT * FROM product_emission LIMIT 10
```

| id | company\_id | country\_id | industry\_group\_id | year | product\_name | weight\_kg | carbon\_footprint\_pcf | upstream\_percent\_total\_pcf | operations\_percent\_total\_pcf | downstream\_percent\_total\_pcf |
| ---: | ---------: | ---------: | ----------------: | ---: | -----------: | --------: | -------------------: | -------------------------: | ---------------------------: | ---------------------------: |
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
| ---: | -----------: |
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
| ---: | -----------: |
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
| -: | ---------------------------------------------------------------------: | 
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
