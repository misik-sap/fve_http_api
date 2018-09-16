# fve_http_api

Simple HTTP REST API for FVE. 

It enables communication towards a WattRouter, a device responsible for monitoring the FVE production statistics.

## WattRouter is able to send a response to following requests:

### GET/meas.xml: 
Actual FVE production statistics.

Structure of the XML file:
```
<meas>
<PL1>-2.20</PL1><-- phase L1 in kW output>
<PL2>1.50</PL2><-- phase L2 in kW output>
<PL3>-1.10</PL3><-- phase L3 in kW output>
<PPS>-1.80</PPS><-- output sum on phases L1+L2+L3 in kW>
<Te>25.0</Te><-- wattrouter temperature in °C>
<PA1>1.00</PA1><-- estimated power on output 1 in kW>
<FA1>0.50</FA1><-- power on input FB1>
<FE1>1.60</FE1><-- energy on input FB1>
<DaR>1.1.2012</DaR><-- date (wattrouter)>
<TiR>0:00:00</TiR><-- time (wattrouter)>
<FW>S10</FW><-- firmware type (first letter) and version (second number)>
<EL1>0</EL1><-- 0=no failure, 1=missing voltabe L1>
<ETS>0</ETS><-- 0=no failure, 1=error in temperature sensor>
<ETL>0</ETL><-- 0=no failure, 1=max temperature exceeded>
<ILT>0</ILT><-- 0=not present, 1=indicates low tarif>
<ICW>0</ICW><-- 0=not present, 1=indicates CombiWATT>
<ITS>0</ITS><-- 0=not present, 1=indicates the output test>
<IDST>0</IDST><-- 0=not present, 1=summer time indicated>
</meas>
```

### GET/conf.xml: 
Configuration status of the WattRouter.

### GET/stat_day.xml?day={index}: 
FVE production statistics determined by day. {0} is actual date, {1} is yesterday, {7} is last 7th day.

### GET/stat_week.xml: 
FVE week production statistics.

### GET/stat_month.xml: 
FVE month production statistics.

### GET/stat_year.xml: 
FVE year production statistics.
