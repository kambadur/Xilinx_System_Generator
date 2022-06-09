#### One digit BCD adder implementation in Xilinx System Generator

##### Work in progress..  

This repo contains XSG Simulink model for 1 digit BCD adder.  
Equivalent handwritten HDL implementation can be found below.  
https://github.com/kambadur/Projects/tree/main/bcdadder  

The goal is to verify both the implementations in Vivado (for learning purposes)  

##### XSG blocks used in this model:  
AddSub  
Slice  
Logical  
Relational  
Constant  
Mux  
Gatway In/Out  


Simulation, Compilation and Generation of netlist needs to be verified yet. After this it has to be tested in Vivado to see if the HDL wrapper that XSG generates synthesizes.  
![](assets/bcdadd_1dig.png)   


##### Notes:  
1. I have noticed Solver configuration and 'Simulink system period' parameter from System Generator token are not very important in this combinational circuit.  So, I left it as 1s as shown below.
2. While using an 'AddSub' block (full adder) seting the output config as 'Flag as error' upon overflow helps a lot. This would prove very helpful in case you are not using carry output.  
    ![](assets/addsub_overflow.png)  
3. I found Simulink compiler didnot complain if I treat 1bit values as UFix_1_0 (unsigned fixed-point 1bit width and 0bits after decimal point) instead of boolean. Please see below.  
   ![](assets/UFix_1_0.png)  
4. As you can see you can use Goto and From blocks in your XSG design without having to ge through Gateway blocks. This is good!  
5. Simulink gets to know the rate at which your XSG design to be simulated is via GatewayIn blocks. Specify the 'sample rate' parameter accordingly. Setting the 'Simulink system period' alone in the SysGen token will result in a warning and a default sample rate from the Gateway In blocks will be taken for simulation. Just be careful!  
6. 

At this point in time, I am still not very comfortable implementing my design in XSG. I find it easier and faster to do this in verilog and simulate it in iVerilog and GTKwave. Perhaps this might change once I get myself little more familiar with XSG and Simulink in general.  


##### Useful resources / Acknowledgements:  
http://www.ece.northwestern.edu/local-apps/matlabhelp/toolbox/simulink/slref/bitwiselogicaloperator.html  
https://hdlbits.01xz.net/wiki/Bcdadd4  
