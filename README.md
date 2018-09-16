# fve_http_api

Simple HTTP REST API for FVE. 

It enables communication towards a WattRouter, a device responsible for monitoring the FVE production statistics.

##### WattRouter is able to send a response to following requests:
- GET/meas.xml: actual FVE production statistics.
Structure of the XML file:
```
<meas>
<PL1>-2.20</PL1><-- phase L1 in kW output>
<PL2>1.50</PL2><-- phase L2 in kW output>
<PL3>-1.10</PL3><-- phase L3 in kW output>
<PPS>-1.80</PPS><-- output sum on phases L1+L2+L3 in kW>
<Te>25.0</Te><-- wattrouter temperature in °C>
<PA1>1.00</PA1><-- předp. výkon zátěže na výstupu 1 v kW>
<FA1>0.50</FA1><-- výkon na vstupu FB1>
<FE1>1.60</FE1><-- energie na vstupu FB1>
<DaR>1.1.2012</DaR><-- datum (regulátor)>
<TiR>0:00:00</TiR><-- čas (regulátor)>
<FW>S10</FW><-- typ firmwaru (první písmeno) a verze (2 číslice)>
<EL1>0</EL1><-- 0=není porucha, 1=chybí napětí L1>
<ETS>0</ETS><-- 0=není porucha, 1=chyba čidla teploty>
<ETL>0</ETL><-- 0=není porucha, 1=překročena max. teplota>
<ILT>0</ILT><-- 0=není, 1=indicates low tarif>
<ICW>0</ICW><-- 0=není, 1=indicates CombiWATT>
<ITS>0</ITS><-- 0=není, 1=indicates the output test>
<IDST>0</IDST><-- 0=není, 1=summer time indicated>
</meas>
```

- GET/conf.xml: configuration status of the WattRouter.

- GET/stat_day.xml?day={index}: FVE production statistics determined by day. {0} is actual date, {1} is yesterday, {7} is last 7th day.

- GET/stat_week.xml: FVE week production statistics.

- GET/stat_month.xml: FVE month production statistics.

- GET/stat_year.xml: FVE year production statistics.
