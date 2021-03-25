//# 4-bit-binary-asynchronous-up-counter
// Code your design here

module bcd(rst,clk,q);
  input  rst,clk;
  output reg [3:0] q;
  initial q=0;
  always@(rst,clk)
    if(rst==1)
      q=4'd0;
  else if(q==4'd9)
    @(posedge clk) q=4'd0;
   else
     @(posedge clk) q<=q+1'd1;
endmodule

// code for test bench in EDA playground software
// Code your testbench here

module tb;
  reg rst,clk;
  wire [3:0] q;
  bcd b(rst,clk,q);
  
 
  initial begin
    clk=0;
  forever
    #2clk=~clk;
  end
  initial begin
    forever#1 $display("q=%b",q);
      end
  
  initial 
    begin
      $dumpfile("dump.vcd"); $dumpvars;
     rst=0;
      #50rst=1;
      #50$finish;
    
  end
endmodule

//The code here is to simulate 4 bit synchronous up counter in Xilinx Design tools or EDA playground software
