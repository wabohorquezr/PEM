.SUBCKT ZVS in GND outA outB
LRS outA outB 10µ Rser=1m
CRS outA outB 6.3µ
LPa in outB 200µ Rser=1m
LPb in outA 200µ Rser=1m
Ra in N001 470
Rb in N002 470
M§Qb outA N001 0 0 BSC060N10NS3
D1 N002 outA 1N5817
D2 N001 outB 1N5817
M§Qa outB N002 0 0 BSC060N10NS3
.model D D
.lib C:\users\alex\AppData\Local\LTspice\lib\cmp\standard.dio
.model NMOS NMOS
.model PMOS PMOS
.lib C:\users\alex\AppData\Local\LTspice\lib\cmp\standard.mos
* ZVS Circuito
.backanno
.ENDS ZVS