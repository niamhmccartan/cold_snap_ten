# cold_snap_ten
Cold snaps lead to a 5-fold increase or a 3-fold decrease in disease proliferation depending on the baseline temperature. 

Niamh McCartan 1 (communicating author), Jeremy Piggott 1, Sadie DiCarlo 1,2, and Pepijn Luijckx 1. 

1 Discipline of Zoology, School of Natural Sciences, Trinity College Dublin, Dublin, Ireland.
2 Carleton College, Sayles Hill Campus Center, North College Street, Northfield, MN 55057, USA.

This dataset contains infection prevalence and burden observations collected from _Daphnia magna_ infected with its microsporidian parasite _Ordospora colligata_ at the School of Natural Sciences in Trinity College Dublin during summer 2022. This study looked at the effect of cold snaps on parasite fitness. Here, a cold snap meant a reduction in baseline temperature (constant mean temperature) at a specific amplitude and duration, occurring 10-days post infection. Infection prevalence data included all exposed individuals, while burden data included confirmed infections only. Baseline temperature was a continuous centered variable to reduce issues with collinearity and remove the need for a ‘water bath’ variable, thus avoiding any associated random effects. A polynomial (cubic for burden, and quadratic for infection prevalence) was added to account for non-linearity in the response to temperature. Amplitude and duration were ordered factors with two levels each (“-3ºC” and “-6 ºC” for amplitude, “3-days” and “6-days” for duration), both also included the constant treatments with the reference level “0”, this allowed for statistical testing on the two variables both independently and combined. The package ‘glmnet’ was used to model parasite fitness, and the package ‘emmeans’ was used to compare specific treatments. Data were analyzed using R Studio version 4.0.3. Custom contrast p-values were adjusted for multiple comparisons using the ‘Benjamini-Hochberg’ method. 

_________________________________________________


**R scripts for analysis:** 

_CS_Analysis.Rmd_: analysis and graphing for both infection prevalence and burden

-----

**List of datasets used for analysis:**

_CS_Data.csv_: observations on infection prevalence and burden

```
ID: unique sample number from 1 to 456
Timing: cold snap timing, either happening 10-days post infection “10”, or constant “C”
A_Temp: target baseline temperature
Real_Avg: the true temperature per bath read from the HOBO loggers at the end of the experiment 
Amplitude: How many degrees the cold snap decreased (“0” constant, “-3” -3 ºC, “-6” -6 ºC)
Duration: Duration of the cold snap (“0” constant, “3” 3-days, “6” 6-days)
Replicate: Replicate number of the treatment
Bath: Location of the individual micrososm (either bath A, B, or C)
Date: Date of death (last day 27/08/2022)
Day: Day of death (starting from day -10 and ending on day 33)
Sex: Sex of the individual 
Infection: Presence (1) or absence (0) of infection 
Spores: Number of spores present if infected, if exposed but uninfected NA entered
Exposed: Number of spores present if infected, if exposed but uninfected 0 entered
Include: Yes if included in analysis, no if excluded from analysis (e.g. before first confirmed infection, any males, or any inconclusive infections) 
Notes: Any important notes given when dissections occurred
Change: Explanation if any changes in the raw data were made
```

_CS_Temp_Logs.xlsx_: raw temperature data per bath per hour, also with overall mean temperature 

```
#: Time point recording ID
Date Time, GMT+00:00: Date and time of time point recording 	
Temp, °C: Temperature recorded					
Average Temp: Average temperature only including temperature points ±2 degrees
Logger ID: Logger ID used for the specific bath	
```
