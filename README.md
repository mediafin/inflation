
This is a public repository by the data team of the Belgian newspaper De Tijd. Using the featured scripts and data we try to take a deep dive in the Belgian inflation figures. The current version is work in progress. The main purpose of the repo is to make our research available for review. 

If you are a researcher willing to provide feedback please contact us directly.

## Questions for researchers

* In the CPI-dataset, the index per month can’t be reproduced as the weighted mean of the underlying coicop-elements and their weight. Is this due to rounding errors?

* What product codes should be in- and excluded from the hbs-data? 

In order to produce an inflation figure by income group we understand the need to filter the HBS data from products that aren’t used to calculate the CPI. We are aware of the fact that some corrections made in the the official inflation calculations of StatBel can’t be reproduced as they would need to make use of microdata. Yet NBB defines a selection of products and categories that should be in- and excluded in order to approach the officially published inflation figures as close as possible.

The list of INCLUDED coicop-levels (including all their child elements) is listed below.

| COICOP  | desc                                                                     |
|---------|--------------------------------------------------------------------------|
| CP01    | VOEDING EN NIET- ALCOHOLISCHE DRANKEN                                    |
| CP02    | ALCOHOLISCHE DRANKEN, TABAK                                              |
| CP03    | KLEDING EN SCHOENEN                                                      |
| CP041   | Reële huur                                                               |
| CP043   | Onderhoud en herstelling woning                                          |
| CP044   | Leidingwater, afvalophaling, andere kosten verbonoden aan de huisvesting |
| CP0451  | Elektriciteit                                                            |
| CP0452  | Gas                                                                      |
| CP0453  | Huisbrandolie                                                            |
| CP0454  | Vaste brandstoffen                                                       |
| CP05    | MEUBELEN, HUISHOUDTOESTELLEN EN ONDERHOUDSPRODUCTEN                      |
| CP06    | GEZONDHEID                                                               |
| CP071   | Aankoop van voertuigen                                                   |
| CP0721  | Banden, vervangstukken en onderdelen voor persoonlijk vervoer            |
| CP07221 | diesel                                                                   |
| CP07222 | benzine                                                                  |
| CP07223 | andere brandstoffen                                                      |
| CP07224 | smeermiddelen                                                            |
| CP0723  | Herstelling en onderhoud van voertuigen                                  |
| CP0724  | Overige uitgaven voor persoonlijk vervoer                                |
| CP073   | Diensten vervoer                                                         |
| CP08    | COMMUNICATIE                                                             |
| CP09    | CULTUUR EN VRIJE TIJD                                                    |
| CP10    | OPLEIDING                                                                |
| CP11    | RESTAURANT EN HORECA                                                     |
| CP12    | PERSOONLIJKE VERZORGING EN DIENSTEN                                      |

Additionally, We exclude the following products (and their child elements)

|     23 | drugs              |
|-------:|--------------------|
|    122 | prostitution       |
|   1251 | life insurance     |
| 12530B | hospital insurance |
| 12530C | health insurance   |

Further information about additional corrections that can be made using public available data would be very welcome.


* Do we need to rescale the filtered HBS data (based on categories above) per mille before additional price udpates?

* How do we calculate the price updates correctly? 

We currently load all publicly available HBS-data up to 2012. We update the weights using the followint formula (applied on coicop level 3)

I.E: Updated weight in 2021 = HBS-weight in 2018 * (index in December 2020 / mean index in 2018). 

* A further breakdown to coicop4 causes more category names and codes that change over time. Can a price update be done on coicop level 3?

* Can we calculate the inflation on coicop level 1 as the weighted average of the deeper coicop levels?

-------

## Credits

HBS and CPI data is property of StatBel, the Belgian Office of Statistics. The methodology used the reproduce the inflation is based on earlier reports by NBB (National Bank of Belgium)

Inflation calculations De Tijd © 2021 by De Tijd is licensed under Attribution-NonCommercial-ShareAlike 4.0 International￼ 


This license requires that reusers give credit to the creator. It allows reusers to distribute, remix, adapt, and build upon the material in any medium or format, for noncommercial purposes only. If others modify or adapt the material, they must license the modified material under identical terms.