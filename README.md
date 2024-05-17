# SIMULATION AND IMPLEMENTATION OF COMBINATIONAL LOGIC CIRCUITS

## AIM: 
 To simulate and synthesis ENCODER, DECODER, MULTIPLEXER, DEMULTIPLEXER, MAGNITUDE COMPARATOR using Xilinx ISE.

## APPARATUS REQUIRED:

•vivado 2023.2

## PROCEDURE:
```
STEP:1  Start  the Xilinx navigator, Select and Name the New project.
STEP:2  Select the device family, device, package and speed.       
STEP:3  Select new source in the New Project and select Verilog Module as the Source type.                       
STEP:4  Type the File Name and Click Next and then finish button. Type the code and save it.
STEP:5  Select the Behavioral Simulation in the Source Window and click the check syntax.                       
STEP:6  Click the simulation to simulate the program and  give the inputs and verify the outputs as per the truth table.    
STEP:7  Select the Implementation in the Sources Window and select the required file in the Processes Window.
STEP:8  Select Check Syntax from the Synthesize  XST Process. Double Click in the  FloorplanArea/IO/Logic-Post Synthesis process in the User Constraints process group. UCF(User constraint File) is obtained. 
STEP:9  In the Design Object List Window, enter the pin location for each pin in the Loc column Select save from the File menu.
STEP:10 Double click on the Implement Design and double click on the Generate Programming File to create a bitstream of the design.(.v) file is converted into .bit file here.
STEP:11  On the board, by giving required input, the LEDs starts to glow light, indicating the output.
```

# LOGIC DIAGRAM:

# ENCODER:
![image](https://github.com/kamali109/VLSI-LAB-EXP-2/assets/160600794/1226a14a-e4eb-43d3-9127-89e0ea3212ff)

## CODE:

```h
module encoder(a,y);
input [7:0]a;
output[2:0]y;
or(y[2],a[6],a[5],a[4],a[3]);
or(y[1],a[6],a[5],a[2],a[1]);
or(y[0],a[6],a[4],a[2],a[0]);
endmodule

```
# OUTPUT: 
![316583214-c394369a-58e7-40cd-921e-0b02de3bd90b](https://github.com/kamali109/VLSI-LAB-EXP-2/assets/160600794/b4ab55c0-2cb5-4859-9df9-4bafea3485a1)

# DENCODER:
![image](https://github.com/kamali109/VLSI-LAB-EXP-2/assets/160600794/43207494-7237-435a-9715-f45dae0b2a39)

# CODE:
```h
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
# OUTPUT:
![image](https://github.com/kamali109/VLSI-LAB-EXP-2/assets/160600794/3bc4b836-0b87-4b05-a90c-2fbd5235df91)

# MULTIPLEXER:
![image](https://github.com/kamali109/VLSI-LAB-EXP-2/assets/160600794/4d79779b-61d0-4178-adcf-d861e5bd1099)

# CODE:
```h
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
# OUTPUT:

![image](https://github.com/kamali109/VLSI-LAB-EXP-2/assets/160600794/7fcef8f4-5631-46d2-91f8-b0459217c125)

# DEMULTIPLEXER:
![image](https://github.com/kamali109/VLSI-LAB-EXP-2/assets/160600794/ee9a11f7-fffb-4ffb-a811-d83cb2f44350)

# CODE:
```h
module demux_8(s,a,y);
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
# OUTPUT:
![image](https://github.com/kamali109/VLSI-LAB-EXP-2/assets/160600794/9bcd043d-f30d-497c-b8b7-47ec6df5eeab)


# MAGNITUDE COMPARATOR:
![image](https://github.com/kamali109/VLSI-LAB-EXP-2/assets/160600794/a129f76f-daba-48b3-8e3d-8d16e2d4393e)

# CODE:
```h
module comparator(a,b,eq,lt,gt);
input [3:0] a,b;
output reg eq,lt,gt;
always @(a,b)
begin
 if (a==b)
 begin
  eq = 1'b1;
  lt = 1'b0;
  gt = 1'b0;
 end
 else if (a>b)
 begin
  eq = 1'b0;
  lt = 1'b0;
  gt = 1'b1;
 end
 else
 begin
  eq = 1'b0;
  lt = 1'b1;
  gt = 1'b0;
 end
end 
endmodule
```
# OUTPUT:
![image](https://github.com/kamali109/VLSI-LAB-EXP-2/assets/160600794/b8c29138-e538-48bb-893e-daf99c55a8ef)


## RESULT:
```
Hence ENCODER, DECODER, MULTIPLEXER, DEMULTIPLEXER, MAGNITUDE COMPARATOR are simulated and synthesised using Xilinx ISE.
```

