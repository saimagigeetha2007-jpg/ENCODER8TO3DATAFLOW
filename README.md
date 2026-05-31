### ENCODER 8TO3 DATAFLOW Modelling

**AIM:**

To implement  Encoder 8 To 3 in Dataflow Modelling using verilog and validating their functionality using their functional tables

**SOFTWARE REQUIRED:** Quartus prime

**THEORY**

**Encoder 8 To 3**

The 8 to 3 line Encoder is also known as Octal to Binary Encoder. In 8 to 3 line encoder, there is a total of eight inputs, i.e., D0, D1, D2, D3, D4, D5, D6, and D7 and three outputs, i.e., A0, A1, and A2. In 8-input lines, one input-line is set to true at a time to get the respective binary code in the output side. Below are the block diagram and the truth table of the 8 to 3 line encoder.

![image](https://github.com/naavaneetha/ENCODER8TO3DATAFLOW/assets/154305477/0bc242c1-eb9e-4c47-afe5-30428470efc3)

Figure 01  Block Diagram of Encoder 8 * 3

**Truth Table**

![image](https://github.com/naavaneetha/ENCODER8TO3DATAFLOW/assets/154305477/35496b14-ae6e-4cd1-9abd-d6736b576575)

The logical expression of the term A0, A1, and A2 are as follows:

A0 = D1 + D3 + D5 + D7

A1 = D2 + D3 + D6 + D7

A2 = D4 + D5 + D6 + D7

Logical circuit of the above expressions is given below:

![image](https://github.com/naavaneetha/ENCODER8TO3DATAFLOW/assets/154305477/95acaee6-c873-4c75-89eb-ef09fb158053)

Figure 02  Encoder 8 * 3

**Procedure**

/* write all the steps invloved */

**PROGRAM**

/* Program for Encoder 8 To 3 in Dataflow Modelling and verify its truth table in quartus using Verilog programming. 



module jk_ff(q, qb,j,k,clock,reset);
    input j,k,clock,reset;
    output reg q, qb;
	 
always @ (posedge (clock))

    begin 
        if (!reset)
            begin
               q <= q;
               qb <=qb;
            end   
        
else
 //Write logic for JK flipflop using if else statement for four conditions

begin
               if (j == 0 && k == 0)
                    begin
                    q <= q;
                    qb <= qb;
                    end 
		else if (j != k)
                    begin
                    q <= j;
                    qb <= k;
                    end
               else if (j == 1 && k == 1) 
                    begin 
                    q <= ~q; 
                    qb <= ~qb; 
                    end 
            end
end  
endmodule

//SR Flip Flop Behavioral Level using ‘case’ 
module sr_ff(q, q_bar, s,r, clk, reset);
  input s,r,clk, reset;
  output reg q;
  output q_bar;
  assign q_bar = ~q;
 
  always@(posedge clk) begin // for synchronous reset
    if(!reset)       q <= 0;
    else 
  begin				q <= 1;
	
		case({s,r})    
	     2'b00: q <= q;    // No change
        2'b01: q <= 1'b0; // Write logic for reset
        2'b10: q <= 1'b1; // Write logic for set
        2'b11: q <= 1'bx; // Write logic for Invalid state
      endcase
    end
  end
  //assign q_bar = ~q;
Endmodul

//T FLIPFLOP POS-EDGE
module t_ff( input clk, rst_n, input t,
output reg q,
output q_bar
);
always@(posedge clk) 
begin // for synchronous reset
  //WRITE THE CONDITION OF TOGGLE FLIPFLOP HERE WITH RESET AND 
  //IMPLEMENT THE T LOGIC BY CONDITIONAL OPERATOR
if(!rst_n)
q<=0;
else 
begin
q<=(t?~q:q);
end
end
assign q_bar = ~q;
endmodule
module ripple_counter(clk,rst,t,A,B,C,D); 
input clk,rst,t; 
output A,B,C,D;
reg A,B,C,D;

Tff T0(D,clk,rst,t); 
Tff T1(C,D,rst,t); 
Tff T2(B,C,rst,t); 
Tff T3(A,B,rst,t); 

endmodule 

module Tff(q,clk,rst,t); 
input clk,rst,t; 
output q; 
reg q; 
output q_bar;
always @(posedge clk) 
	
begin 
if(!rst)
q<=0;
else 
begin
q<=(t?~q:q);
end
assign q_bar = ~q;

endmodule
//shift register_SISO
module shift_reg10(clk, sin, q);
input clk;
input sin;
output [3:0] q;
reg [3:0] q;
always @(posedge clk)
begin
q[0] <= sin;
q[1] <= q[0];
q[2] <= q[1];
q[3] <= q[2];
end
endmodule

**RTL LOGIC FOR Encoder 8 To 3 in Dataflow Modelling**
<img width="831" height="399" alt="Screenshot 2026-05-28 151253" src="https://github.com/user-attachments/assets/bb1c0e2c-04db-45c5-bac6-a2548defdc8d" />

**TIMING DIGRAMS FOR Encoder 8 To 3 in Dataflow Modelling**
<img width="846" height="471" alt="Screenshot 2026-05-28 151303" src="https://github.com/user-attachments/assets/c7adf1a2-bc24-46e2-a7f7-d0b63f6b5efa" />


**RESULTS**
Encoder 8 To 3 in Dataflow Modelling using verilog and validating their functionality using their functional tables is verified.



