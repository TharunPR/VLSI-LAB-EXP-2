# SIMULATION AND IMPLEMENTATION OF COMBINATIONAL LOGIC CIRCUITS

**AIM:**<br>

&emsp;&emsp;To simulate and implement the following circuits using VIVADO 2023.3.<br>

&emsp;&emsp;&emsp;&emsp;&emsp;1) Encode<br>
&emsp;&emsp;&emsp;&emsp;&emsp;2) Decoder<br>
&emsp;&emsp;&emsp;&emsp;&emsp;3) Multiplexer<br>
&emsp;&emsp;&emsp;&emsp;&emsp;4) Demultiplexer<br>
&emsp;&emsp;&emsp;&emsp;&emsp;5) Magnitude comparator<br>

**SOFTWARE REQUIRED:**<br>

&emsp;&emsp;VIVADO 2023.2<br>

**PROCEDURE:**<br>

 STEP:1 Launch the Vivado 2023.2 software.<br>
 STEP:2 Click on “create project ” from the starting page of vivado.<br>
 STEP:3 Choose the design entry method:RTL(verilog/VHDL).<br>
 STEP:4 Crete design source and give name to it and click finish.<br>
 STEP:5 Write the verilog code and check the syntax.<br>
 STEP:6 Click “run simulation” in the navigator window and click “Run behavioral simulation”.<br>
 STEP:7 Verify the output in the simulation window.<br>
 
**ENCODER:**

**LOGIC DIAGRAM:**

![image](https://github.com/navaneethans/VLSI-LAB-EXP-2/assets/6987778/3cd1f95e-7531-4cad-9154-fdd397ac439e)

**VERILOG CODE:**

```
 module encoder(a,y);
 input [7:0]a;
 output[2:0]y;
 or(y[2],a[6],a[5],a[4],a[3]);
 or(y[1],a[6],a[5],a[2],a[1]);
 or(y[0],a[6],a[4],a[2],a[0]);
 endmodule
```

**OUTPUT WAVEFORM:**

![encodefr](https://github.com/TharunPR/VLSI-LAB-EXP-2/assets/117915125/180bb043-6994-4bdf-9b37-3e081d493e5b)

**DECODER:**

**LOGIC DIAGRAM:**

![image](https://github.com/navaneethans/VLSI-LAB-EXP-2/assets/6987778/45a5e6cf-bbe0-4fd5-ac84-e5ad4477483b)

**VERILOG CODE:**

```
 module decoder1(a,y);
 input [2:0]a;
 output[7:0]y;
 and(y[0],~a[2],~a[1],~a[0]);
 and(y[1],~a[2],~a[1],a[0]);
 and(y[2],~a[2],a[1],~a[0]);
 and(y[3],~a[2],a[1],a[0]);
 and(y[4],a[2],~a[1],~a[0]);
 and(y[5],a[2],~a[1],a[0]);
 and(y[6],a[2],a[1],~a[0]);
 and(y[7],a[2],a[1],a[0]);
 endmodule
```

**OUTPUT WAVEFORM:**

![decoder](https://github.com/TharunPR/VLSI-LAB-EXP-2/assets/117915125/e129c495-447e-4265-adb7-25db522bacc3)

**MULTIPLEXER:**

**LOGIC DIAGRAM:**

![image](https://github.com/navaneethans/VLSI-LAB-EXP-2/assets/6987778/427f75b2-8e67-44b9-ac45-a66651787436)

**VERILOG CODE:**

```
 module mux(s,c,a);
 input [2:0]s;
 input [7:0]a;
 wire [7:0]w;
 output c;
 and(w[0],a[0],~s[2],~s[1],~s[0]);
 and(w[1],a[1],~s[2],~s[1],s[0]);
 and(w[2],a[2],~s[2],s[1],~s[0]);
 and(w[3],a[3],~s[2],s[1],s[0]);
 and(w[4],a[4],s[2],~s[1],~s[0]);
 and(w[5],a[5],s[2],~s[1],s[0]);
 and(w[6],a[6],s[2],s[1],~s[0]);
 and(w[7],a[7],s[2],s[1],s[0]);
 or (c,w[0],w[1],w[2],w[3],w[4],w[5],w[6],w[7]);
 endmodule
```

**OUTPUT WAVEFORM:**

![mux](https://github.com/TharunPR/VLSI-LAB-EXP-2/assets/117915125/6ceb4fb6-16f4-4b7d-98c7-361a8c450eec)

**DEMULTIPLEXER:**

**LOGIC DIAGRAM:**

![image](https://github.com/navaneethans/VLSI-LAB-EXP-2/assets/6987778/1c45a7fc-08ac-4f76-87f2-c084e7150557)

**VERILOG CODE:**

```
 module demux(s,a,y);
 input [2:0]s;
 input a;
 output [7:0]y;
 and(y[0],a,~s[2],~s[1],~s[0]);
 and(y[1],a,~s[2],~s[1],s[0]);
 and(y[2],a,~s[2],s[1],~s[0]);
 and(y[3],a,~s[2],s[1],s[0]);
 and(y[4],a,s[2],~s[1],~s[0]);
 and(y[5],a,s[2],~s[1],s[0]);
 and(y[6],a,s[2],s[1],~s[0]);
 and(y[7],a,s[2],s[1],s[0]);
 endmodule
```

**OUTPUT WAVEFORM:**

![demux](https://github.com/TharunPR/VLSI-LAB-EXP-2/assets/117915125/8271fcff-0be8-4bff-9054-59870bc9fa16)

**MAGNITUDE COMPARATOR:**

**LOGIC DIAGRAM:**

![image](https://github.com/navaneethans/VLSI-LAB-EXP-2/assets/6987778/b2fe7a05-6bf7-4dcb-8f5d-28abbf7ea8c2)

**VERILOG CODE:**

```
 module comparator(a,b,eq,lt,gt);
 input [3:0] a,b;
 output reg eq,lt,gt;
 always @(a,b)
 begin
 if (a==b)
 begin
 eq =1'b1;
 lt = 1'b0;
 gt = 1'b0;
 end
 else if (a>b)
 begin
 eq =1'b0;
 lt = 1'b0;
 gt = 1'b1;
 end
 else
 begin
 eq =1'b0;
 lt = 1'b1;
 gt = 1'b0;
 end
 end
 endmodule
```

**OUTPUT WAVEFORM:**

![magcomp](https://github.com/TharunPR/VLSI-LAB-EXP-2/assets/117915125/6956a78e-80f6-450d-aeee-bebf0601073c)

**RESULT:**<br>
&emsp;&emsp; Thus the simulation and implementation of combinational logic circuit is done and outputs are verified successfully.

