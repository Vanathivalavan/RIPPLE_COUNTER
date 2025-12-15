# RIPPLE_COUNTER
AIM:
To implement 4 Bit Ripple Counter using verilog and validating their functionality using their functional tables

SOFTWARE REQUIRED:
Quartus prime

#THEORY
4 Bit Ripple Counter
A binary ripple counter consists of a series connection of complementing flip-flops (T or JK type), with the output of each flip-flop connected to the Clock Pulse input of the next higher-order flip-flop. The flip-flop holding the least significant bit receives the incoming count pulses. The diagram of a 4-bit binary ripple counter is shown in Fig. below.

<img width="752" height="400" alt="image" src="https://github.com/user-attachments/assets/18fb84aa-8502-4de5-a5b4-3b28bbde1d55" />


In timing diagram Q0 is changing as soon as the negative edge of clock pulse is encountered, Q1 is changing when negative edge of Q0 is encountered(because Q0 is like clock pulse for second flip flop) and so on.

<img width="445" height="339" alt="image" src="https://github.com/user-attachments/assets/7d71bbce-e5d3-454e-b04b-5273d151a9e9" />

#Procedure
Select four flip-flops (usually T or JK) and identify clock and outputs.

Apply the external clock to the first flip-flop only.

Connect the output of each flip-flop to the clock input of the next stage.

Set each flip-flop to toggle so it changes state on its clock edge.

Verify that the outputs count in binary from 0000 to 1111 asynchronously.

PROGRAM
```
module RIPPLECOUNTER(q, clk, reset); 
output [3:0] q;
input clk, reset;
T_FF tffo(q[0], clk, reset); 
T_FF tff1(q[1], q[0], reset); 
T_FF tff2(q[2], q[1], reset); 
T_FF tff3(q[3], q[2], reset); 
endmodule

module D_FF(q, d, clk, reset); 
output q;
input d, clk, reset;
reg q;
always @(posedge reset or negedge clk)
 if (reset)
q = 1'b0;
 else
q = d;
endmodule

module T_FF(q, clk, reset);
output q;
input clk, reset;
wire d;
D_FF dff0(q, d, clk, reset);
not n1(d, q); // not is Verilog-provided primitive. 
endmodule

```

Developed by: VANATHI T
RegisterNumber: 25013590

RTL LOGIC FOR 4 Bit Ripple Counter
![Uploading Screenshot 2025-12-15 204441.png…]()


TIMING DIGRAMS FOR 4 Bit Ripple Counter

RESULTS: Thus the 4 Bit Ripple Counter using verilog and validating their functionality using their functional tables is verified.


