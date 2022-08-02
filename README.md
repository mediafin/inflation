
This is a public repository by the data team of the Belgian newspaper [De Tijd](https://www.tijd.be). Using the featured scripts and data we try to take a deep dive in the Belgian inflation figures. The current version is a work in progress. The main purpose of this repo is to make our research available for review. 

If you are a researcher willing to provide feedback please contact us directly.

## Step 1

We were able to reproduce the officially published inflation figure (see the script from line 20 to 108). In this code we unchain and aggregate the indices. 


## Step 2
In line 113 till 177 we lwe load and clean the historical hbs data from 2012 until 2020. 


## Step 3
From line 182 until 207 we include and exclude certain product groups as provided in the methodology of NBB

In order to calculate an inflation figure by income group we understand the need to filter out the HBS data for products that aren’t used to calculate the CPI. We are aware of the fact that some corrections made to the official inflation calculations of StatBel can’t be reproduced as they would need to make use of microdata. Yet NBB defines a selection of products and categories that should be either included or excluded in order to approach the officially published inflation figures as closely as possible.

The list of INCLUDED coicop-levels (including all child elements) is listed below.


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

Additionally, we exclude the following products (and their child elements)

| COICOP | desc               |
|--------|--------------------|
|     23 | drugs              |
|    122 | prostitution       |
|   1251 | life insurance     |
| 12530B | hospital insurance |
| 12530C | health insurance   |

Further information about additional corrections that can be made using publicly available data would be very welcome.

* Do we need to rescale the filtered HBS data (based on categories above) per mille before additional price updates?

* How do we calculate the price updates correctly? 

We currently load all publicly available HBS data from 2012 on. We update the weights using the following formula (applied on coicop level 3)

I.E: Updated weight in 2021 = HBS weight in 2018 * (index in December 2020 / mean index in 2018). 

* A further breakdown to coicop4 causes more category names and codes that change over time. Can an accurate price update be done by sticking to coicop level 3?

* Can we calculate the inflation on coicop level 1 as the weighted average of the deeper coicop levels?

## Step 4: 

From line 218 to 245 we rebuild the hbs-weights after we filtered specific product codes

## Step 5: Price Update

Starting from line 260 we pdate the weights according the the methology provided by statbel. 




-------

## Credits

HBS and CPI data is property of StatBel, the Belgian Office of Statistics. The methodology used the reproduce the inflation is based on earlier reports by NBB (National Bank of Belgium)

Inflation calculations De Tijd © 2021 by De Tijd is licensed under Attribution-NonCommercial-ShareAlike 4.0 International

This license requires that reusers give credit to the creator. It allows reusers to distribute, remix, adapt, and build upon the material in any medium or format, for noncommercial purposes only. If others modify or adapt the material, they must license the modified material under identical terms.
