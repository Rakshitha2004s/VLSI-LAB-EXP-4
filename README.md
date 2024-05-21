# VLSI-LAB-EXP-4
SIMULATION AND IMPLEMENTATION OF SEQUENTIAL LOGIC CIRCUITS

AIM: 
 To simulate and synthesis SR, JK, T, D - FLIPFLOP, COUNTER DESIGN using Vivado 2023.1.

APPARATUS REQUIRED:

Vivado 2023.1

PROCEDURE:

STEP:1 Launch the Vivado 2023.2 software.

STEP:2 Click on “create project ” from the starting page of vivado.

STEP:3 Choose the design entry method:RTL(verilog/VHDL).

STEP:4 Crete design source and give name to it and click finish.

STEP:5 Write the verilog code and check the syntax.

STEP:6 Click “run simulation” in the navigator window and click “Run behavioral simulation”.

STEP:7 Verify the output in the simulation window.


LOGIC DIAGRAM OF SR FLIPFLOP

![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/6987778/77fb7f38-5649-4778-a987-8468df9ea3c3)


VERILOG CODE

```
module srff(s,r,clk,rst,q);
input s,r,clk,rst;
output reg q;
always@(posedge clk)
begin
if(rst==1)
q=0;
else
begin
case({s,r})
2'b00:q=q;
2'b01:q=0;
2'b10:q=1;
2'b11:q=1'bX;
endcase
end
end
endmodule
```


OUTPUT

![image](https://github.com/Rakshitha2004s/VLSI-LAB-EXP-4/assets/161333609/34ee2d3d-776c-498e-b4d5-4cb17ceb0d2e)



JK FLIPFLOP

![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/6987778/1510e030-4ddc-42b1-88ce-d00f6f0dc7e6)


VERILOG CODE

```
module jkff(j,k,clk,rst,q);
input j,k,clk,rst;
output reg q;
always@(posedge clk)
begin
if(rst==1)
q=0;
else
begin
case({j,k})
2'b00:q=q;
2'b01:q=0;
2'b10:q=1;
2'b11:q=~q;
endcase
end
end
endmodule
```


OUTPUT

![image](https://github.com/Rakshitha2004s/VLSI-LAB-EXP-4/assets/161333609/40201b1f-a39c-48b5-9196-8a39c3613419)



T FLIPFLOP

![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/6987778/7a020379-efb1-4104-85ee-439d660baa08)


VERILOG CODE

```
module tff(clk,rst,t,q);
input clk,rst,t;
output reg q;
always @(posedge clk)
begin
if (rst==1)
q=1'b0;
else if (t==0)
q=q;
else
q=~q;
end
endmodule
```


OUTPUT

![image](https://github.com/Rakshitha2004s/VLSI-LAB-EXP-4/assets/161333609/3c71bcdd-a23d-4bca-b081-ff9c11621337)



D FLIPFLOP

![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/6987778/dda843c5-f0a0-4b51-93a2-eaa4b7fa8aa0)


VERILOG CODE

```
module dff(d,clk,rst,q);
input d,clk,rst;
output reg q;
always @(posedge clk)
begin
if (rst==1)
q=1'b0;
else
q=d;
end
endmodule
```


OUTPUT

![image](https://github.com/Rakshitha2004s/VLSI-LAB-EXP-4/assets/161333609/396c0e95-bd11-4066-ba4c-e9ac86c865cb)



COUNTERS

![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/6987778/a1fc5f68-aafb-49a1-93d2-779529f525fa)



UPDOWN COUNTER

VERILOG CODE

```
module dff(d,clk,rst,q);
input d,clk,rst;
output reg q;
always @(posedge clk)
begin
if (rst==1)
q=1'b0;
else
q=d;
end
endmodule
```

  
OUTPUT

![image](https://github.com/Rakshitha2004s/VLSI-LAB-EXP-4/assets/161333609/066078ce-f1d6-4726-a59a-1eac1edfbe43)



MOD 10 COUNTER

VERILOG CODE

```
module mod10(clk,rst,out);
input clk,rst;
output reg [3:0]out;
always@(posedge clk)
begin
if (rst==1 | out==4'b1001)
out=4'b0000;
else
out=out+1;
end
endmodule
```


OUTPUT

![image](https://github.com/Rakshitha2004s/VLSI-LAB-EXP-4/assets/161333609/e5271770-280a-43c6-8d8b-1168ffea2b0d)


RIPPLE COUNTER

VERILOG CODE
```
module tff(q,clk,rst);
input clk,rst;
output q;
wire d;
dff df1(q,d,clk,rst);
not n1(d,q);
endmodule
module dff(q,d,clk,rst);
input d,clk,rst;
output q;
reg q;
always @(posedge clk or posedge rst)
begin
if (rst)
q=1'b0;
else 
q=d;
end
endmodule








module ripplecounter(clk,rst,q);
input clk,rst;
output [3:0]q;
tff tf1(q[0],clk,rst);
tff tf3(q[2],q[1],rst);
tff tf4(q[3],q[2],rst);
endmodule
```


OUTPUT

![image](https://github.com/Rakshitha2004s/VLSI-LAB-EXP-4/assets/161333609/766a7309-7909-4e43-b055-7c607a982c24)




RESULT

Thus the simulation and implementation of sequential logic gates is done and verified.
