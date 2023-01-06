# Day-0

## System Tool Setup Check and Git Hub ID Creation

this is my first repository

**Package**

Package is the container that holds the semiconductor die. It protects the die from potential damage and connects the chip to a board or other chips.

<img src = "https://user-images.githubusercontent.com/118953932/205524319-648a6f38-1bea-4289-8c5b-08fc34583e01.png" width = "200" height = "200">

Pads: connects with the pins and the core area

Core: consists main logics (NMOS and PMOS transistors)

<img src = "https://user-images.githubusercontent.com/118953932/205524420-6b0aa437-f32d-465b-9973-5708f1841c59.png" width = "782">

**Communication of Software and Hardware**

Synthesis is process of converting RTL to a technology specific Gate level netlist.

<img src = "https://user-images.githubusercontent.com/118953932/205524468-35fd33f7-d697-4afd-99c1-7283707ff258.png" width = "782">


**LAB RESULT**

<img src = "https://user-images.githubusercontent.com/118953932/205524545-c9211f9f-d460-4678-9774-b88b6d53be20.jpg" width = "500" height = "300">


# Day-1
## Introduction to Verilog RTL design and Synthesis
### SKY130RTL D1SK2 L1 Lab1 introduction to lab

**LAB RESULT**

Set up (git clone files)

<img src = "https://user-images.githubusercontent.com/118953932/205524714-d9b07322-28c5-413d-827c-e8e562a323c3.JPG" width = "500" height = "300">

### SKY130RTL D1SK2 L2 Lab2 introduction to lab

**LAB RESULT**

iverilog and gtkwave

<img src = "https://user-images.githubusercontent.com/118953932/205524787-ab6395c4-de0d-4f3c-b3ad-26a051f40647.JPG" width = "500" height = "300">


### SKY130RTL D1SK2 L3 Lab2 introduction to lab

**LAB RESULT**

RTL code

<img src = "https://user-images.githubusercontent.com/118953932/205524878-0e696495-bf5f-444b-a29d-c8a1f92c19d7.JPG" width = "500" height = "300">

### SKY130RTL D1SK4 L1 Lab3 Yosys 1 good mux Part1

**LAB RESULT**

Invoke yosys

- yosys

<img src = "https://user-images.githubusercontent.com/118953932/205528904-2c528986-b619-4ff8-913f-62b9788dec86.png" width = "500" height = "300">

Read Liberty

- read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib

Successfully Read Verilog File

- read_verilog good_mux.v

<img src = "https://user-images.githubusercontent.com/118953932/205528663-ee6437e6-5379-41ab-9f9d-2c62116887bf.png" width = "500" height = "300">

Synthesize module

- synth -top good_mux

<img src = "https://user-images.githubusercontent.com/118953932/205529293-805ccbd9-84ac-4223-8b05-f108e361e043.png" width = "500" height = "300">

Generate netlist

- abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib

<img src = "https://user-images.githubusercontent.com/118953932/205529804-74867478-7ec8-4b47-a0de-d902fa8c2c0f.png" width = "500" height = "300">

Graphical version of the logic

- show

<img src = "https://user-images.githubusercontent.com/118953932/205530013-0b43f83d-0097-4894-8d35-27a72e9bdc42.png" width = "500" height = "400">

### SKY130RTL D1SK4 L2 Lab3 Yosys 1 good mux Part2

<img src = "https://user-images.githubusercontent.com/118953932/205535826-ef31f6ca-319d-458f-9e56-151ed280150b.png" width = "500" height = "300">

the yellow highlighted is the name for the library used and the red underlined is the logical cell

### SKY130RTL D1SK4 L3 Lab3 Yosys 1 good mux Part3

**LAB RESULT**

Write netlist

- write_verilog good_mux_netlist.v

<img src = "https://user-images.githubusercontent.com/118953932/205532061-8c6491da-0d58-4dc4-8c0e-1d3655abf02b.png" width = "500">

- !vim good_mux_netlist.v

<img src = "https://user-images.githubusercontent.com/118953932/205533023-3c315c4b-3f73-435c-af16-e2d5563621e3.png" width = "500" height = "300">

Simplified netlist

- write_verilog -noattr good_mux_netlist.v

<img src = "https://user-images.githubusercontent.com/118953932/205533638-7dd57dcb-29ba-412d-9a40-8eb7abeefb38.png" width = "500">

- !vim good_mux_netlist.v

i0 = primary input

i1 = primary input 

sel = primary input

y = primary output

<img src = "https://user-images.githubusercontent.com/118953932/205533744-d7c3cdd4-31d0-4c0e-9c3b-251705ecbe00.png" width = "500" height = "400">

# Day 2
## Timing libs, hierarchical vs flat synthesis and efficient flop coding styles
### SKY130RTL D2SK1 - Introduction to timing .libs (SKY130RTL D2SK1 L1 Lab4 Introduction to dot Lib part1)

- dot lib is collection of a standard cell contains slow cells fast cells

Open sky130 library

- gvim ../lib/sky130_fd_sc_hd_tt_025C_1v80.lib

 yellow highlighted on the right is how to turn off the syntech

<img src = "https://user-images.githubusercontent.com/118953932/205811909-a5e0c4cc-d222-4f41-b8b5-0a972e8d7f12.png" width = "500" height = "300">  <img src = "https://user-images.githubusercontent.com/118953932/205811468-5785f612-d3c4-42fc-90eb-ddb684e6f311.png" width = "500" height = "300">


Understanding the terms
- tt = typical process
- 025C = temperature
- 1v80 = voltage

<img src = "https://user-images.githubusercontent.com/118953932/205812752-2093184f-7fd0-45b7-a71a-85351a522a94.png" width = "500" height = "300">

PVT
- P = Process
- V = Voltage
- T =Temperature

These will determine the silicon to work in various way

Libraries will be characterize to model these variations

<img src = "https://user-images.githubusercontent.com/118953932/205815366-16f4adb6-ccf0-4d41-9dc2-7fdccc585a79.png" width = "500" height = "300">

### SKY130RTL D2SK1 - Introduction to timing .libs (SKY130RTL D2SK1 L2 Lab4 Introduction to dot Lib part2)

Understanding dot lib
- the indicators/units used for dot lib

<img src = "https://user-images.githubusercontent.com/118953932/205867829-add71371-a450-4daa-a1e1-6663f8fe47d3.png" width = "500" height = "300"> <img src = "https://user-images.githubusercontent.com/118953932/205868482-f64c8fec-6941-4628-a7c7-21528cfc2eda.png" width = "500" height = "300">

Searching for keywords

- use "/"
- :g//

a = and, o = or, i = inverter

<img src = "https://user-images.githubusercontent.com/118953932/205873666-57b934f1-603c-42d8-acc4-b339c5edd7d7.png" width = "500" height = "300">

- features

eg:

a2111o = 2 AND and others are OR

"!" is low and no "!" is high

<img src = "https://user-images.githubusercontent.com/118953932/205875696-e3a075b7-73d9-4b7a-86a0-6f59df15314f.png" width = "500" height = "300">


area number and power port information

<img src = "https://user-images.githubusercontent.com/118953932/205876987-858be703-50b5-4fac-923e-9b23b0780aa9.png" width = "500" height = "300">

information of each input pin 

<img src = "https://user-images.githubusercontent.com/118953932/205878419-0982d646-597d-4a5f-ae72-556216698df7.png" width = "500" height = "300">

### SKY130RTL D2SK1 - Introduction to timing .libs (SKY130RTL D2SK1 L3 Lab4 Introduction to dot Lib part3)

Understanding dot lib

eg:

- 4 conditions for AND gate: 01, 00, 11, 10


<img src = "https://user-images.githubusercontent.com/118953932/205927278-1a5ca04c-020a-45e5-974c-5fc438e69195.png" width = "500" height = "300">

- use ":vs" to display it side by side

- If cell employing wider transistor, it will have larger area value
- wider cells -> faster but area and power is more 
- smaller cells -> delay more but area and power is less

<img src = "https://user-images.githubusercontent.com/118953932/205931339-57cdf6b2-092b-44f0-8168-cb4e73721049.png" width = "600">

### SKY130RTL D2SK2 - Hierarchical vs Flat Synthesis (SKY130RTL D2SK2 L1 Lab05 Hier synthesis flat synthesis part1)

Hierarchical synthesis and flat synthesis

- gvim multiple_modules.v

<img src = "https://user-images.githubusercontent.com/118953932/205934271-e6277db1-f16d-4575-a93d-c3e96d033511.png" width = "500" height = "300">

- translated into logic

<img src = "https://user-images.githubusercontent.com/118953932/205935440-30246ffb-67fd-4cdc-b423-94c9bcd13e1d.png" width = "500" height = "300">

- yosys
- read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
- read_verilog multiple_modules.v

<img src = "https://user-images.githubusercontent.com/118953932/205937266-903200d9-9229-4ae8-b8cf-bdf0f3cbd81d.png" width = "500" height = "300">

- synth -top multiple_modules

overall design have 2 cells (AND gate and OR gate)

<img src = "https://user-images.githubusercontent.com/118953932/205938400-64adb178-048c-4bab-be48-6ed81fe39dd1.png" width = "500" height = "300"> <img src = "https://user-images.githubusercontent.com/118953932/205938621-95658673-116d-4595-a811-c2fb805bc5b3.png" width = "500" height = "300">

Linking design to the library

- abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib

- show multiple_modules (display the hierarchical design)

<img src = "https://user-images.githubusercontent.com/118953932/206082435-688c7827-31a7-4e3b-aaf0-352aefe4feb1.png" width = "400">

Write the netlist
- write_verilog -noattr multiple_modules_hier.v
- !gvim multiple_modules_hier.v

<img src = "https://user-images.githubusercontent.com/118953932/206103090-b8534adc-5bca-4891-b121-0216ad233cb2.png" width = "700">

Situation where it does not use OR gate

- reason why NOR is not used: because it has stacked PMOS which means it has poor mobility

<img src = "https://user-images.githubusercontent.com/118953932/206104524-4db8fb57-6da9-47ab-ae9f-da7e325f6c81.png" height = "200"> <img src = "https://user-images.githubusercontent.com/118953932/206105575-274fb75d-c33a-4337-a0a3-258f54de2cf9.png" height = "200">

### SKY130RTL D2SK2 - Hierarchical vs Flat Synthesis (SKY130RTL D2SK2 L2 Lab05 Hier synthesis flat synthesis part2)

Flat Netlist
- flatten
- write_verilog -noattr multiple_modules_flat.v
- !gvim multiple_modules_flat.v

<img src = "https://user-images.githubusercontent.com/118953932/206108460-b49fc965-2a22-4735-902d-878132402898.png" width = "500" height = "300">

Distintion between using the flat end switch and not using the flat end switch

- :vsp multiple_modules_hier.v

- hierarchy of sub module 1 and sub module2 are preserved

<img src = "https://user-images.githubusercontent.com/118953932/206109377-3b8a3114-f705-4ccf-b76a-b142cb8f34ee.png" width = "500" height = "300">

- show

<img src = "https://user-images.githubusercontent.com/118953932/206110252-3d738d99-65c0-48b7-bab4-cca4caff7f9d.png" height = "300">

Create sub_module1 only 

-exit
- yosys
- read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
- read_verilog multiple_modules.v
- synth -top sub_module1
- abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
- show

<img src = "https://user-images.githubusercontent.com/118953932/206118830-11b57a3f-d65a-477f-ad47-a3dd0af8ca40.png" width = "500" height = "300">


Reasons why the do sub module synthesis 

-  synthesize one time and replicate netlist then stich it in the top module (when we have multiple instances of same module) 
-  to give one portion by one portion to the tool to achieve optimize netlist (when we have massive design and use divide and concure approach)

<img src = "https://user-images.githubusercontent.com/118953932/206113996-36b79699-048d-4957-a468-80a167cf6d5a.png" width = "500" height = "300">

### SKY130RTL D2SK3 - Various Flop Coding Styles and optimization (SKY130RTL D2SK3 L1 Why Flops and Flop coding styles part1)

Reason why glitch occured
- due to propagation delay

<img src = "https://user-images.githubusercontent.com/118953932/206128517-0cd22edf-f878-4d87-b113-22c6267c6f7c.png" width = "500" height = "300">

- the more the combinational circuit, the more the glitches
- the output of the flop will be stable although the input glitches (from the combi circuit) and thats why we use flop

<img src = "https://user-images.githubusercontent.com/118953932/206129515-e0c2c71f-1d9f-4091-9a96-08d761f012df.png" width = "500" height = "300">

Flop need to be initialized

<img src = "https://user-images.githubusercontent.com/118953932/206130184-6828f0d5-3ba6-4fa1-8468-c50a737d3885.png" width = "500" height = "300">

### SKY130RTL D2SK3 - Various Flop Coding Styles and optimization (SKY130RTL D2SK3 L2 Why Flops and Flop coding styles part2)

Circuit sensitive to posedge of the clock

<img src = "https://user-images.githubusercontent.com/118953932/206131666-67d7b89f-d5c4-43ce-8f97-82de7f6e032d.png" width = "500" height = "300">

Asynchronous
- can happen anytime
- irrespective of clock

D flip flop with asynchronous reset

<img src = "https://user-images.githubusercontent.com/118953932/206132694-554ed154-017d-4f19-aa61-d927cf376481.png" width = "500" height = "300">

Synchronous

- will come in the D pin of the flop
- awaits for the clock edge

<img src = "https://user-images.githubusercontent.com/118953932/206134088-ee603859-2951-4593-bc79-3d5531895204.png" width = "500" height = "300">

Flop with different reset

<img src = "https://user-images.githubusercontent.com/118953932/206135143-a8efe944-8bb4-4db6-8cb7-3d7fd9a0f574.png" height = "400"> <img src = "https://user-images.githubusercontent.com/118953932/206135632-f9b3cd23-f302-429e-ba38-76f256ca9fe9.png" height = "400">

### SKY130RTL D2SK3 - Various Flop Coding Styles and optimization (SKY130RTL D2SK3 L3 Lab flop synthesis simulations part1)

Search for file
- ls *dff *

**Asynchronous Reset**

- iverilog dff_asyncres.v tb_dff_asyncres.v
- ./a.out
- gtkwave tb_dff_asyncres.vcd

d may come up at any point but q is synchronous to the clock (will change upon clock)

<img src = "https://user-images.githubusercontent.com/118953932/206139540-a23cf67c-be81-436a-bfca-f96e1725e246.png" width = "500" height = "300">

output q went low immediately when reset came (due to the asynchrounous behaviour)

<img src = "https://user-images.githubusercontent.com/118953932/206140736-40a9b779-ad1c-4d44-845e-c59f0625c7c5.png" width = "500" height = "300">

**Asynchronous Set**

- iverilog dff_async_set.v tb_dff_async_set.v
- ./a.out
- gtkwave tb_dff_async_set.vcd

when set is present, q was at one irrespective to d

when set is low the q pin will follow the pos clock edge and affected by the d


<img src = "https://user-images.githubusercontent.com/118953932/206145368-a0ddfaf3-dfd2-4a59-8974-4ee6c9fc887d.png" width = "500" height = "300"> <img src = "https://user-images.githubusercontent.com/118953932/206144848-51922543-aad3-43a5-96c4-67dbf9f83212.png" width = "500" height = "300">

**Synchronous Behaviour**

- iverilog dff_syncres.v tb_dff_syncres.v
- ./a.out
- gtkwave tb_dff_syncres.vcd

reset went high but q waiting for the subsequent posedge of the clock and then went low
<img src = "https://user-images.githubusercontent.com/118953932/206149503-652defe6-63c3-44ea-be91-3d4bc5e7bc2e.png" width = "500" height = "300">

### SKY130RTL D2SK3 - Various Flop Coding Styles and optimization (SKY130RTL D2SK3 L4 Lab flop synthesis simulations part2)

Synthesis the circuit

**Asynchronous Reset**

- yosys
- read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
- read_verilog dff_asyncres.v
- synth -top dff_asyncres
- dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
- abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
- show

active high reset

<img src = "https://user-images.githubusercontent.com/118953932/206152672-f30e21cb-4ffb-47ae-be43-29eb64a66280.png" height = "300">

**Asynchronous Set**

- read_verilog dff_async_set.v
- synth -top dff_async_set
- dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
- abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
- show

<img src = "https://user-images.githubusercontent.com/118953932/206156094-ded2f43d-3369-40a7-b340-9cd9fa5fdb3f.png" height = "300">

**Synchronous Reset and Asynchronous Reset**

- read_verilog dff_syncres.v
- synth -top dff_syncres
- dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
- abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
- show

<img src = "https://user-images.githubusercontent.com/118953932/206184418-8f475efb-fab9-4c57-81da-ee8c51c78794.png" height = "300">


### SKY130RTL D2SK3 - Various Flop Coding Styles and optimization (SKY130RTL D2SK3 L5 Interesting optimisations part1)

RTL code for optimization 

- 3 bit input and 4 bit output

<img src = "https://user-images.githubusercontent.com/118953932/206187813-1c0a3932-e9d5-4d9e-bebb-d389ebf96de2.png" height = "300"> <img src = "https://user-images.githubusercontent.com/118953932/206188512-8297e072-6855-4a8a-b343-551b9a23c7c9.png" height = "300">

a(2:0)---------------- y(3:0)

         a(2) - y(3)

         a(1) - y(2)
         
         a(0) - y(1)
         
                y(0) ground

tips - *multiply 2 (add one zero at the end) multiply 4 (add two zero at the end) multiply 8 (add three zero at the end)*

- yosys
- read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
- read_verilog mult_2.v
- synth -top mul2
- abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
- show

<img src = "https://user-images.githubusercontent.com/118953932/206191959-e1c7958d-71de-4ab0-a7dd-df4d408fee00.png" height = "300">


### SKY130RTL D2SK3 - Various Flop Coding Styles and optimization (SKY130RTL D2SK3 L6 Interesting optimisations part2)

Special case

a(2:0) * 9 = y(5:0)

<img src = "https://user-images.githubusercontent.com/118953932/206198301-658c721f-c830-4386-9d5a-2d55708917a3.png" height = "200"> <img src = "https://user-images.githubusercontent.com/118953932/206198763-b58d2f95-8602-4315-afe4-211ae1498f67.png" height = "200">

Netlist

- write_verilog -noattr mul2_net.v
- !gvim mul2_net.v

<img src = "https://user-images.githubusercontent.com/118953932/206199728-0288f2c0-40f1-483a-a98c-b1ae935d9f4d.png" height = "350">

- read_verilog mult_8.v
- synth -top mult8
- abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
- show 

<img src = "https://user-images.githubusercontent.com/118953932/206202175-575de40a-e08b-40c3-9d55-96d20a872a6a.png" height = "300">

Netlist

- write_verilog -noattr mult8_net.v
- !gvim mult8_net.v

<img src = "https://user-images.githubusercontent.com/118953932/206202912-29de2303-1375-437c-99e0-83cb7471dfd4.png" height = "300">

# Day-3
## Combinational and sequential optmizations
### SKY130RTL D3SK1 L1 Introduction to optimisations part1

**Introduction to Logic Optimisation**

Logic optimization is a process of finding an equivalent representation of the specified logic circuit under one or more specified constraints. It is a process of a part of a logic synthesis applied in digital electronics and integrated circuit design.

<img src = "https://user-images.githubusercontent.com/118953932/206409949-31b372be-47a0-4273-9d52-3a7aa56ba642.png" height = "250"> <img src = "https://user-images.githubusercontent.com/118953932/206410486-e7527055-9172-4eba-aa47-67a35dfacd05.png" height = "250">

Digital logic contains two type of logic names:
- Combinational logic (one whose output solely depends on its current inputs)
- Sequential Logic (are built using combinational circuits and memory elements which are flip flops)

<img src = "https://user-images.githubusercontent.com/118953932/206600070-959b874d-c022-42cd-a9a5-cba0a403f40b.png" height = "300"> 
Combinational logic optimisation
- Squeeze the logic to get the most optimised design -- Area and Power savings
- Constant Propagation -- Direct Optimisation
- Boolean Logic Optimisation

**Constant Propagation**

Example:

- the inverter consume less area and power than the due to it only have 2 MOS transistor compare to 6 MOS transistor

- the constant 0 on A got propagated down the logic

<img src = "https://user-images.githubusercontent.com/118953932/206398316-8396c426-9b19-4688-a667-6c3053a834e6.png" height = "300">

Example of Boolean Logic Optimisation:

- from mux to exclusive or

- Boolean logic simplification and kmap reduction

<img src = "https://user-images.githubusercontent.com/118953932/206399612-2bfabb19-d600-4dd0-b95e-cdd21b11c580.png" height = "300">

### SKY130RTL D3SK1 L2 Introduction to optimisations part2

**Sequential Logic Optimisations**
- Basic -- Sequential Constant propagation
- Advanced -- State optimisation, Retiming, Sequential Logic Cloning (Floor Plan Aware Synthesis)

Example of Sequntial Constant Propagation:

<img src = "https://user-images.githubusercontent.com/118953932/206401881-a1becd24-cf2e-49cd-b4ec-6ed9e3d66fea.png" height = "300">

- set flop connected (not sequential constant = cannot optimize)
- Q pin doesnt take constant value

<img src = "https://user-images.githubusercontent.com/118953932/206404054-a4cc4525-7760-4733-818c-3b7be7f66d2e.png" height = "300">

### SKY130RTL D3SK1 L3 Introduction to optimisations part3

**State Optimisation**

Optimisation of unused state
1) Cloning (physical aware synthesis)
- avoid large routing delay

<img src = "https://user-images.githubusercontent.com/118953932/206466206-b7d9b39d-570a-4574-acfb-1a38b04786c7.png" height = "300">

2) Retiming
- improve perfomance of the circuit (can change the clock frequency) 
- reduce delay increase frequency

<img src = "https://user-images.githubusercontent.com/118953932/206470638-9ece86aa-f5c3-42f5-81f2-ae36b6d0455e.png" height = "300">

### SKY130RTL D3SK2 L1 Lab06 Combinational Logic Optimisations part1

Reading and understanding the file content

- ls *opt_check *
- gvim opt_check.v
- gvim opt_check2.v

<img src = "https://user-images.githubusercontent.com/118953932/206599871-5067db71-5598-4b50-b1b1-380af8e8a02d.png" height = "300">

Mux

The multiplexer or MUX is used to implement the Boolean functions or any of the logic gates, and it is called as universal logic which means all the standard logic gates can be implemented with multiplexers.

De Morgan's Theorem

The theorem explains that the complement of the product of all the terms is equal to the sum of the complement of each term.

<img src = "https://user-images.githubusercontent.com/118953932/206597325-ad0c2fd9-698d-4bcc-8b3b-f7db6602c6d2.png" height = "300">

mux to logic gate conversion:

<img src = "https://user-images.githubusercontent.com/118953932/206599034-d1ec0768-aaff-4db6-979f-1263b94e5a1a.png" height = "250"> <img src = "https://user-images.githubusercontent.com/118953932/206599127-e7597e30-4694-4984-9f33-4d06bea3208d.png" height = "250">

Implementation of 2 input NAND and NOR gate using 2x1 mux

<img src = "https://user-images.githubusercontent.com/118953932/206598366-51d8b5ac-5bdc-400d-8288-b72caeaacff9.png" height = "100">
<img src = "https://user-images.githubusercontent.com/118953932/206598460-410443ec-d593-466e-8003-4e1e31c3d12b.png" height = "120">

- yosys
- read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
- read_verilog opt_check.v
- synth -top opt_check
- opt_clean -purge
- abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
- show

opt_check.v (AND)

<img src = "https://user-images.githubusercontent.com/118953932/206601917-e0f94855-1685-4c13-bb53-c533c3ef0ca6.png" height = "250"> <img src = "https://user-images.githubusercontent.com/118953932/206603702-3fac52ea-1aae-42de-adee-fcad7b618aa8.png" height = "250">

opt_check2.v (OR)

y = a?1:b

<img src = "https://user-images.githubusercontent.com/118953932/206604249-f3374096-f1ef-4bb2-9a6a-ee8593695736.png" height = "250"> 

opt_check3.v (3 input AND gate)

y = a?(c?b:0):0

<img src = "https://user-images.githubusercontent.com/118953932/206605587-a3c9e315-2abc-48cc-ac36-de3f24e49409.png" height = "200"> <img src = "https://user-images.githubusercontent.com/118953932/206605102-a508cd17-48c0-46b3-96dc-6e4c9439ac79.png" height = "250">

opt_check4.v (xnor)

y = a?(b?(a&c):c):(!c)

<img src = "https://user-images.githubusercontent.com/118953932/206606111-82d30415-dead-4637-bac6-8988c17fa0af.png" height = "250">

multiple_module_opt.v

- yosys
- read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
- read_verilog multiple_module_opt.v
- synth -top multiple_module_opt
- opt_clean -purge
- abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
- flatten
- show

<img src = "https://user-images.githubusercontent.com/118953932/206629019-8d59731a-6907-47a6-a33b-cb370166bf22.png" height = "250"> <img src = "https://user-images.githubusercontent.com/118953932/206630903-6eca6311-ff70-4c10-946b-faed82216b8b.png" height = "250"> <img src = "https://user-images.githubusercontent.com/118953932/206629165-6ebae6a2-fbef-4cce-a10e-eb63d831aff6.png" height = "250"> 

- write_verilog multiple_module_opt_flat.v
- exit
- gvim multiple_module_opt_flat.v

 <img src = "https://user-images.githubusercontent.com/118953932/206630731-f94055a0-f3b8-4f9a-8a2c-a8ba42966205.png" height = "250">
 
 
multiple_module_opt2.v

- yosys
- read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
- read_verilog multiple_module_opt2.v
- synth -top multiple_module_opt2
- opt_clean -purge
- abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
- flatten
- show

<img src = "https://user-images.githubusercontent.com/118953932/206643022-7e0489dc-6324-491c-a580-14cd2eb2f4d3.png" height = "250"> <img src = "https://user-images.githubusercontent.com/118953932/206642726-991e71d4-da66-4b90-aff8-ddf8a4f83257.png" height = "250"> <img src = "https://user-images.githubusercontent.com/118953932/206643404-1c6018cf-1492-4e08-b4cb-8d4328d52b30.png" height = "250">
 
- write_verilog multiple_module_opt2_flat.v
- exit
- gvim multiple_module_opt2_flat.v

 <img src = "https://user-images.githubusercontent.com/118953932/206644340-f7dafc87-b43c-473a-b9e6-23c3d57a26b1.png" height = "250">


### SKY130RTL D3SK3 L1 Lab07 Sequential Logic Optimisations part1

Reading and understanding content

- ls *df *const *
- gvim dff_const1.v -o dff_const2.v

<img src = "https://user-images.githubusercontent.com/118953932/206609564-3dcbcdb9-7b77-474b-9ffb-eb4964b08342.png" height = "250"> <img src = "https://user-images.githubusercontent.com/118953932/206610254-523b2a15-aa2b-4ba7-b960-6d088b6a2cc9.png" height = "200">

Simulation

- iverilog dff_const1.v tb_dff_const1.v
- ./a.out
- gtkwave tb_dff_const1.vcd

<img src = "https://user-images.githubusercontent.com/118953932/206611056-44c5d703-cece-4e74-9c7c-fadbd33b0d4f.png" height = "250">

- iverilog dff_const2.v tb_dff_const2.v
- ./a.out
- gtkwave tb_dff_const2.vcd

<img src = "https://user-images.githubusercontent.com/118953932/206611387-a2cd6872-ada7-40f9-8206-8de44a6270e7.png" height = "250">

Synthesize (dff_cost1)

- yosys
- read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
- read_verilog dff_const1.v
- synth -top dff_const1
- dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
- abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
- show

<img src = "https://user-images.githubusercontent.com/118953932/206612348-f3b1d01f-014d-4ab1-a5fe-5fe17776c65b.png" height = "250">

### SKY130RTL D3SK3 L2 Lab07 Sequential Logic Optimisations part2

Synthesize (dff_cost2)

- read_verilog dff_const2.v
- synth -top dff_const2
- dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
- abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
- show

<img src = "https://user-images.githubusercontent.com/118953932/206614309-32289f6d-ce09-4325-ab7d-28d786446530.png" height = "250">

dff_cost3

- gvim dff_const3.v

<img src = "https://user-images.githubusercontent.com/118953932/206616067-f8afca5f-7f5f-445c-b8fd-29eb39de8d5f.png" height = "250">

- Q always high expect for one clock cycle

<img src = "https://user-images.githubusercontent.com/118953932/206615992-c7eefb85-c7cb-428e-bf18-2db01d61416b.png" height = "250">

### SKY130RTL D3SK3 L3 Lab07 Sequential Logic Optimisations part3

Simulate dff_const3

- iverilog dff_const3.v tb_dff_const3.v
- ./a.out
- gtkwave tb_dff_const3.vcd

<img src = "https://user-images.githubusercontent.com/118953932/206616786-6d911386-83e9-42aa-8254-084e61b3189e.png" height = "250">

Synthesize

- yosys
- read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
- read_verilog dff_const3.v
- synth -top dff_const3
- dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
- abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
- show

<img src = "https://user-images.githubusercontent.com/118953932/206617620-66edcab6-512f-4b40-90c8-22156324a5d3.png" height = "250">

**not every flop having constant got optimize (need to check if Q value constant or not)**

dff_const4

<img src = "https://user-images.githubusercontent.com/118953932/206618391-3d71c6bd-a85f-4df7-be5f-19ad68fd9412.png" height = "250"> <img src = "https://user-images.githubusercontent.com/118953932/206618227-bcdfd1f5-0e9d-4a8e-94ae-1d56aa846974.png" height = "250">

dff_const5.v

<img src = "https://user-images.githubusercontent.com/118953932/206618876-46145f1a-c185-4b51-96fa-2ef26f156201.png" height = "250"> <img src = "https://user-images.githubusercontent.com/118953932/206618785-68b2ae8c-b47e-4a10-939d-2b846ae40b4b.png" height = "250">

### SKY130RTL D3SK4 L1 Seq optimisation unused outputs part1

Reading from RTL code

- gvim counter_opt.v 

<img src = "https://user-images.githubusercontent.com/118953932/206622400-4dbc7745-e2d3-48de-91f7-7c69b7cb96ba.png" height = "250"> <img src = "https://user-images.githubusercontent.com/118953932/206622498-7e2a66bc-9414-48c4-b60d-41ffaa996580.png" height = "250">

Synthesize

- yosys
- read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
- read_verilog counter_opt.v
- synth -top counter_opt

<img src = "https://user-images.githubusercontent.com/118953932/206622902-0eb337fa-14dd-4282-930e-53670e838abc.png" height = "250">

- dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
- abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
- show

<img src = "https://user-images.githubusercontent.com/118953932/206623324-e6ceba1b-8fb1-439d-9e16-c7c993c1a1af.png" height = "250"> <img src = "https://user-images.githubusercontent.com/118953932/206623995-98db33ac-36f2-4cb9-ade7-a9fea6d46117.png" height = "150">

**2 bit of the unused is not connected to the primary input. hence, optimized. any logic that does not resulting in output, will be optimized**

### SKY130RTL D3SK4 L2 Seq optimisation unused outputs part2

Modify RTL

- cp counter_opt.v counter_opt2.v
- gvim counter_opt2.v

change code to make all 3 bit appears

<img src = "https://user-images.githubusercontent.com/118953932/206624852-c24a1d0b-19a0-48eb-a1ba-ff0a3e4f1465.png" height = "250">

Synthesize

- yosys
- read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
- read_verilog counter_opt2.v
- synth -top counter_opt

<img src = "https://user-images.githubusercontent.com/118953932/206625092-a66beff1-7d0a-4ef2-a048-0e74cbd1fd04.png" height = "250">

- dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
- abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
- show

<img src = "https://user-images.githubusercontent.com/118953932/206625936-e4add870-38cd-4bc2-885c-3f061cf47b2a.png" height = "250">
<img src = "https://user-images.githubusercontent.com/118953932/206626331-d59f1cb3-371a-42d9-975e-9dd8567e5c6e.png" height = "150">

**Conclusion: all the intermediate output that does not have direct role in determining the primary output will be optimized**

# Day-4
## GLS, Synthesis-Simulation mismatch and Blocking/Non-blocking statements
### SKY130RTL D4SK1 L1 GLSConceptsAndFlowUsingIverilog

Simulations are an important part of the verification cycle in the process of hardware designing. It can be performed at varying degrees of physical abstraction:

(a)    Transistor level

(b)    Gate level

(c)    Register transfer level (RTL)

<img src = "https://user-images.githubusercontent.com/118953932/207473225-385942d7-ea49-4209-947d-85c563b901a9.png" height = "350">

GLS is run before going into the last stage of chip manufacturing.

GLS = gate level simulation

- Running test bench with Netlist as Design Under Test
- Netlist same as RTL code (logically) = same test bench will align with design 
- it verify logical correctness of design after synthesis
- ensuring timing of the design is met (needs to be run with delay annotation)

<img src = "https://user-images.githubusercontent.com/118953932/207058975-ff8bce25-9f82-4bb6-996c-901ed7b1310d.png" height = "350">

Using iverilog

<img src = "https://user-images.githubusercontent.com/118953932/207057863-b2f657ca-83e9-49c8-b119-42df275acbf7.png" height = "350">

### SKY130RTL D4SK1 L2 SynthesisSimulationMismatch

Synthesis Simulation Mismatch

- missing sensitivity list
- blocking vs non-blocking assignments
- non standard verilog coding

Missing Sensitivity List

change in input only will change the output (only when there is change in select)

<img src = "https://user-images.githubusercontent.com/118953932/207063217-c73bfc02-b467-461e-afa3-0a9139e14e84.png" height = "350">

### SKY130RTL D4SK1 L3 BlockingAndNonBlockingStatementsInVerilog

Blocking and Non-Blocking Statements in Verilog

- inside always block
 > =  Blocking which executes the statements in the order it is written. so the first statement is evaluated before second statement
 
 > <= Non Blocking which executes all the RHS when always block is entered and assigns to LHS (parallel evaluation)

<img src = "https://user-images.githubusercontent.com/118953932/207064574-0fc432f7-f528-4a22-851d-51782612a9c1.png" height = "150">

Caveats with Blocking Statements

<img src = "https://user-images.githubusercontent.com/118953932/207065850-9ae26806-eda9-4014-9d9b-8502d6803e98.png" height = "250">

### SKY130RTL D4SK1 L4 CaveatsWithBlockingStatements

<img src = "https://user-images.githubusercontent.com/118953932/207066571-b6446aa7-505c-4995-93c2-b279df1c3548.png" height = "250">

be careful when using blocking!

<img src = "https://user-images.githubusercontent.com/118953932/207067538-6b9178d1-a745-4b13-99b5-250223a1f255.png" height = "250">

will synthesize only one flop

change order:

<img src = "https://user-images.githubusercontent.com/118953932/207068094-1293127e-42fa-45da-b9b2-6aa64be8cb27.png" height = "250">

that's why GLC needs to be run to match the expectated output!!

### SKY130RTL D4SK2 L1 Lab GLS Synth Sim Mismatch part1

- gvim ternary_operator_mux.v -o bad_mux.v -o good_mux.v
- iverilog ternary_operator_mux.v tb_ternary_operator_mux.v
- ./a.out
- gtkwave tb_ternary_operator_mux.vcd

<img src = "https://user-images.githubusercontent.com/118953932/207077430-1d5f21f0-8287-45df-a4e6-361ed424106e.png" height = "180"> <img src = "https://user-images.githubusercontent.com/118953932/207080297-18c12f79-2d6d-48c9-8ac7-c8239fceb32f.png" height = "180"> 

- yosys
- read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
- read_verilog ternary_operator_mux.v
- synth -top ternary_operator_mux
- abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
- write_verilog -noattr ternary_operator_mux_net.v
- show

- iverilog ../my_lib/verilog_model/primitives.v ../my_lib/verilog_model/sky130_fd_sc_hd.v ternary_operator_mux_net.v tb_ternary_operator_mux.v
- ./a.out
- gtkwave tb_ternary_operator_mux.vcd

<img src = "https://user-images.githubusercontent.com/118953932/207085336-53096edb-5dcc-42c1-940e-fb521e957d8b.png" height = "300"> 

### SKY130RTL D4SK2 L2 Lab GLS Synth Sim Mismatch part2

- iverilog bad_mux.v tb_bad_mux.v
- ./a.out
- gtkwave tb_bad_mux.vcd

yosys
- read_verilog bad_mux.v
- synth -top bad_mux
- abc -liberty ../my_lib/lib/sky130_fd_sc_hd__tt_025C_1v80.lib
- write_verilog -noattr bad_mux_net.v

RTLWave
- iverilog ../my_lib/verilog_model/primitives.v ../my_lib/verilog_model/sky130_fd_sc_hd.v bad_mux_net.v tb_bad_mux.v
- ./a.out
- gtkwave tb_bad_mux.vcd

<img src = "https://user-images.githubusercontent.com/118953932/207090265-8a7ecae3-42b2-44f5-a122-fc01b00e0620.png" height = "190"> <img src = "https://user-images.githubusercontent.com/118953932/207092457-c198f563-7f12-4d49-97ea-2a03f624c346.png" height = "190"> 

left picture is the synthesis simulation mixmatch due to missing sensitivity list 

### SKY130RTL D4SK3 L1 Lab Synth sim mismatch blocking statement part1

Reading RTL

- gvim blocking_caveat.v

<img src = "https://user-images.githubusercontent.com/118953932/207196416-896be252-d1bf-4c1f-80b7-76f8ca285157.png" height = "190"> <img src = "https://user-images.githubusercontent.com/118953932/207196311-56ec3963-9f42-40fb-95d8-778aced416c8.png" height = "190"> 


RTL Wave

- iverilog blocking_caveat.v tb_blocking_caveat.v
- ./a.out
- gtkwave tb_blocking_caveat.vcd

<img src = "https://user-images.githubusercontent.com/118953932/207194724-ba658c51-b18b-4ba0-a9b2-c6a00601b823.png" height = "300"> 

synth sim. mismatch due to blocking statement

### SKY130RTL D4SK3 L2 Lab Synth sim mismatch blocking statement part2

Synthesize

- yosys
- read_liberty -lib ../my_lib/lib/sky130_fd_sc_hd__tt_025C_1v80.lib
- read_verilog blocking_caveat.v
- synth -top blocking_caveat
- abc -liberty ../my_lib/lib/sky130_fd_sc_hd__tt_025C_1v80.lib
- write_verilog -noattr blocking_caveat_net.v
- show

<img src = "https://user-images.githubusercontent.com/118953932/207197080-b4f4f044-3b48-4689-acb5-071c06902143.png" height = "300"> 

- iverilog ../my_lib/verilog_model/primitives.v ../my_lib/verilog_model/sky130_fd_sc_hd.v blocking_caveat_net.v tb_blocking_caveat.v
- ./a.out
- gtkwave tb_blocking_caveat.vcd


<img src = "https://user-images.githubusercontent.com/118953932/207197873-cb63ee2e-752d-4660-8e20-698ba02afd9a.png" height = "300"> 

**Conclusion: use blocking statement carefully**

# Day-5

## DFT - Design For Testability


-> [3W for DFT](#3w-for-dft)

-> [Pro's and Con's](#pros-and-cons)

-> [Basic terminologies](#basic-terminologies)

-> [DFT Techniques](#dft-techniques)
* Ad-hoc Technique
* Structured Technique

-> [Introduction to scan chain](#introduction-to-scan-chain)
***

### 3W for DFT

❔ *What* is DFT?
* consists of IC design techniques that add testability features to a hardware product design
* a step of the design process in which testing features are added to the hardware
* facilitates design to become testable
* add extra design in existing design to test it before fabricating

📝 **Testibility** = design is *well-controllable* and *well-observable*


Examples:
> For macros, we include MBist (memory built in self test) Logic

> For flops, we include scan chain

> For combinational logic, we include generate test patterns

❔ *Why* DFT?
* makes testing easy at the post-production process.
* to increase productivity and improve quality
  * 3 main levels of testing after a chip being fabricated:
    * Chip-level (when chips are manufactured) ✔️ reduce cost/prevent much loss
    * Board-level (when chips are integrated on the boards/package)
    * System-level (when several boards are assembled together)

❔ *When or Where* DFT?

**When** = at the beginning of ASIC design flow

**Where** = during the "Synthesis"

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/207630710-7b379caa-aa6c-4ab3-a0eb-0645f1888199.png" height = "250"></p>

📝 **ASIC (Application Specific Integrated Circuit) design flow** = mature and silicon-proven IC design process which includes various steps like design conceptualization, chip optimization, logical/physical implementation, and design validation and verification

🤔 **Own opinions on DFT = can reduce cost or make it cost effective and can detects faulty at early stage. It also makes testing chip possible and easy.**

***

### Pro's and Con's

| Pro's | Con's |
| ----- | ----- |
| reduces tester complexity | adds complication to the design flow |
| reduces tester time | increase power, area and package pins |
| reduces the chances of going into loss due to faulty devices | design time increases |

***
### Basic Terminologies

📝 **_Controllability_** - ability to set node to a specific value

From DFT point of view, we intend if both '0' and '1' are able to propagate to each and every node within the target patterns. A point is said to be *controllable* if both 'o' and '1' propagated through scan patterns.

<img src = "https://user-images.githubusercontent.com/118953932/207746575-d41b9475-7fbc-4554-909c-7e0735be8021.png" height = "250"> <img src = "https://user-images.githubusercontent.com/118953932/207748424-408c55dc-ada1-42ca-9863-39b657c81d52.png" height = "250">

📝 **_Observability_** - ability to observe a node's value

we need to observe so that we can control it. It means we are able to make the value at the node can be shifted out through scan patterns and can be observe through scan points.


<img src = "https://user-images.githubusercontent.com/118953932/207749638-beb57d35-ba0b-4982-87f1-10edf49d5295.png" height = "300"> <img src = "https://user-images.githubusercontent.com/118953932/207749747-262fcd4d-48c0-4910-a613-7c2d11b67182.png" height = "300">

📝 **_Fault_** - physical damage/defect compared to the good system, which may or may not cause failure

📝 **_Error_** - caused by a fault because of which system went to erroneous state (unknown state)

📝 **_Failure_** - system is not providing the expected service

A **fault** causes an **error** which leads to the system **failure**.

📝 **_Fault Coverage_** - percentage of the total number of logical faults that can be tested using a given test set

📝 **_Defect Level_** - refers to the fraction of shipped parts that are defective. Or, proportion of the faulty chip in which fault isn't detected and has been classified as good
***
### DFT Techniques
1. **Ad-hoc Technique**
* avoid combinational feedback
* all flip flops must be initializable (dont want unknown state (x) so we need reset or set)
* partition a large circuit into small blocks (break it up)
* provide test control for the signals which are not controllable
* while designing the test logic, have to consider the ATE requirements

<img src = "https://user-images.githubusercontent.com/118953932/207756693-48a4a220-ad24-47d6-9ed2-b7d901c9e475.png" height = "300">

*Ad-hoc has limitations. need to be done in intial design state only*

2. **Structured Technique**
* Scan: in the design, all the flip flops will be converted to *scan flip flop*
* Boundary Scan (make it into small groups)
* Built-in self-test
  * MBist (in Macros)
  * LBist (Logic built in self test)

***
### Introduction to scan chain
**Scan-chain Technique**
* specifying the Scan constraints
* specifying Scan ports and Scan enables
* compiling the dft
* identifying the number of Scan Chains

**Scan based techniques/Scan-chains**
* are the elements in scan-based designs that are used to *shift-in* and *shift-out* test data
* formed by a number of flops connected back to back in a chain with the output of one flope connected to another
* the **input of first flop** is connected to the **input of the chip** (scan-in) from where scan is fed. the **output of the last flop** is connected to the **output pin of the chip** (scan-out) which is used to take the shifted data out. scan enable is something like enable line.
* there are 3 types of scan flip-flops configuration namely - **multiplexed**, clocked, lssd (level sensitive scan design)

<img src = "https://user-images.githubusercontent.com/118953932/207760572-dfe7ec77-372d-4b6c-9506-bcc589cfbf86.png" height = "300">

**Purpose of scan flops**
* to test stuck-at faults in manufactured devices
* to test paths in the manufactured devices for delay; i.e. to test whether each path is working at functional frequency or not

**Functionality of scan chain** (steps to do basic scan-in and scan-out)
* to make each node in the circuit controllable and observable
1. **Assert scan_enable** (make it high) so as to enable (SI -> Q) path for each flps
2. keep shifting in the scan data until the intended values at intended nodes are reached
3. **De-assert scan_enable** (for one pulse of clock in case of stuck-at testing and two or more cycles in case of transition testing) to enable D -> Q path so that the combinational cloud output can be captured at the next clock edge
4. again **assert scan_enable** and shift out the data through scan_out

<img src = "https://user-images.githubusercontent.com/118953932/207763621-16371a57-a22d-49d3-83c1-ea7c5dc0bee9.png" height = "200"> <img src = "https://user-images.githubusercontent.com/118953932/207763884-8913c113-549f-4da0-8625-3b63285a593e.png" height = "220">

<img src = "https://user-images.githubusercontent.com/118953932/207764076-c631fb23-772e-44f7-9078-7e1525c9b1f3.png" height = "200"> <img src = "https://user-images.githubusercontent.com/118953932/207764153-c0a2dfd6-9525-435a-befe-c4ffb9a67edd.png" height = "220">

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/207764232-65c45a70-b80d-4dc7-8137-f4b7f9dca1ba.png" height = "220"></p>

<p align="center">credits: orginal photo from anysilicon & edited by nurul</p>

Scan chain operation involves three stages: **Scan-in**, **Scan-capture** and **Scan-out**. Scan-in involves shifting in and loading all the flip-flops with an input vector. During scan-in, the data flows from the output of one flop to the scan-input of the next flop. Once the sequence is loaded, one clock pulse (also called the capture pulse) is allowed to excite the combinatorial logic block and the output is captured at the second flop. The data is then shifted out and the signature is compared with the expected signature. In case of any mismatch, they can point the nodes where one can possibly find any manufacturing fault.

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/207879146-8759bfc9-e3d0-41c3-a580-9bd8a3694e40.png" height = "220"></p>



**FAQ for scan chains**
1. How long one single scan chain is?
   - by chain length, it means the number of ff in a single scan chain. The larger the chain length, the more the number of cycles required to shift the data in and out. For 3 reg, data came out at the forth cycle. so we need to wait for the 4th cycle. However, considering the numbers of flops remains the same, small chain length means more number of input/output ports is needed as scan_in and scan_out ports.
   - Number of ports required = 2 x number of scan chain
   - also, since for each scan chain, scan_in and scan_out port is needed
   - **NOTE**: number of cycles required to run a pattern = length of largest scan chain in design

ATPG (Automatic Test Pattern Generator) also a ATE (Automatic Test Equipment)

**LSSD (Level sensitive scan design)** (not in the video ❗)

* Level-sensitive scan design (LSSD) is part of an integrated circuit manufacturing test process.
* An LSSD scan cell requires three clocks, a system clock, and two non-overlapping clocks that are used during shift.
* LSSD cell is used to replace a nonscan latch, and is suitable for latch based designs.
* For test operation, the two latches form a master/slave pair with one scan input, one scan output and non-overlapping scan clocks A and B which are held low during system operation but cause the scan data to be latched when pulsed high during scan.

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/207811476-93dfce4e-89e8-4e1a-8951-6c59373a9829.png" height = "300"> <img src = "https://user-images.githubusercontent.com/118953932/207812961-4d8f378d-a8b3-4aec-8e6b-3db87169b93e.png" height = "300"></p>

**ATE (Automatic Test Equipment)** (not in the video ❗)

* computerized machinery that uses test instruments to carry out and evaluate the results of functionality, performance, quality, and stress tests performed on electronic devices and systems
* widely used in the electronic manufacturing industry to test electronic components and systems after being fabricated

ATE tests perform two basic functions:

1. to test whether or not the Device Under Test is working correctly
2. when the DUT is not working correctly, to diagnose the reason

 <p align="center"><img src = "https://user-images.githubusercontent.com/118953932/207868477-0aab59c2-9b36-47e8-8c82-81b2c469db0f.png" height = "400"></p>


**Basic ATE functionality**
1. Scan-In Phase 
2. Parallel Measure
3. Parallel Capture
4. First Scan-Out Phase
5. Scan-Out Phase
***

# Day-6
# **ADVANCED SYNTHESIS AND STA WITH DC**
# Day-1 Introduction to Logic Synthesis
## DC_D1SK1_L1 - Lecture1 - Introduction to the course

**Agenda of the course** 📑
- Basics of Digital Logic Design and Synthesis (recap)
- Introduction to Design Compiler (DC)
- TCL (Tool Command Language)
- Constraining the Design, Synopsys Design Constraints (SDC)
- STA (Static Timing Analysis)
- Logic Optimizations
- Advanced Synthesis options
- Generating Timing Reports
- Analyzing Synthesis QoR

**Tools Used** 🧰
- Iverilog - for verilog compilation, simulationn
- gtkwave - for viewing the simulation output
- Synopsys Design Compiler - for logic synthesis
- Skywater 130nm Library - design standard of library

**Pre Requisites** 📚
- Digital Electronics
- Boolean Algebra
- Verilog HDL Coding
- Idea of Basics of Synthesis

**Course Outcomes** ✔️
- Understand various steps involved in Digital Logic Synthesis
- Understand and Write SDC (Sypnosys Design Constraints) for the given module
- Perform Synthesis and write out Netlist using DC
- Generate and Analyze the Synthesis reports/STA reports

<details>
<summary> Basics of Digital Logic Design and Synthesis ✒️ (>>>>❗ click HERE to read more ❗<<<<) </summary>
 <br>

- Digital Logic
  - Switching Function
  - Automation and Decision making

 > manipulation of binary values through printed circuit board technology that uses circuits and logic gates to construct the implementation of computer operations.

 > used to develop hardware, such as circuit boards and microchip processors.

- Behavioral Model of the design is written in HDL
  - VHDL (VHSIC Hardware Description Language)
    - a hardware description language (HDL) that can model the behavior and structure of digital systems at multiple levels of abstraction, ranging from the system level down to that of logic gates, for design entry, documentation, and verification purposes
      
  - Verilog
    - standardized as IEEE 1364
    - a hardware description language (HDL) used to model electronic systems
    - most commonly used in the design and verification of digital circuits at the register-transfer level of abstraction
 
 > 1.  VHDL is strongly typed. This makes it harder to make mistakes as a beginner because the compiler will not allow you to write code that is in valid. Verilog is weakly typed. It allows you to write code that is wrong, but more concise.
 > 2. Verilog looks closer to a software language like C. This makes it easier for someone who knows C well to read and understand what Verilog is doing.
 > 3. VHDL requires a lot of typing. Verilog generally requires less code to do the same thing.


<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/208057956-3cb12dff-1310-477f-929c-550f87030ee9.png" height = "350"></p>
<p align="center">source: FPGA Site</p>

> VHDL and Verilog implement register-transfer-level (RTL) abstractions.

RTL (Register Transfer Logic)
-  is a smaller subset of the full range of HDL code.
-  describes circuits at a level similar to the design description on a schematic.

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/208061364-401dea60-76db-4219-9147-6e249dbdf3cc.png" height = "300"></p>
<p align="center">The conversion of RTL to digital logic circuit</p>
 
Synthesis
- RTL to Gate level translation
- the design is converted into gates and connections are made between gates
- this is given out as a file called netlist (provide rtl and dot lib which from code to gates)
 
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/208065043-cc40c142-b6b2-47c4-98df-7267346600aa.png" height = "350"><img src = "https://user-images.githubusercontent.com/118953932/208066396-44c5ddc5-2884-4a39-8baa-e81679726b1e.png" height = "200"></p>
 
What is .lib
- collection of logical modules
- includes basic logic gates like AND, OR, NOT and others
- different flavours of same gate:
  - 2 input AND gate
    - slow
    - medium
    - fast
  - 3 input AND gate
    - slow
    - medium
    - fast

Why is there different flavours of gate
- combinational delay in logic path determines the maximum speed of operation of digital logic circuit
- want high performance
  - so we need cells that work fast to make Tcombi small
 <p align="center"><img src = "https://user-images.githubusercontent.com/118953932/208069270-424a8aff-880a-4152-acfb-39c0671b2854.png" height = "300"></p>

Why we need slow cells?
- to ensure that there are no hold issue at DFF B, we need cells that work slowly
- fast cell = to meet required performance (setup), slow cell = to meet HOLD
- the collection forms the .lib

 <p align="center"><img src = "https://user-images.githubusercontent.com/118953932/208070386-a158a646-d3eb-4643-9b86-c1d7f826c373.png" height = "300"></p>

Faster Cells vs Slower Cells
- load in digital logic circuit -> capacitance
- faster the charging/discharging of cap, lesser the cell delay
  - to charge/discharge the cap fast, we need transistors capable of sourcing more current
  - wider transistor -> low delay -> more area and power
  - narrow transistor -> more delay -> less area and power

Selection of Cells (convert hdl code to netlist)
- need to guide the Synthesizer to select the flavour of cells that is optimum for the implementation of logic circuit
- more use of **faster cells**
  - bad circuit in terms of power and area
  - hold time violation
- more use of **slower cells**
  - sluggish circuit, may not meet the performance
-the guidance offered to the Synthesizer is **Constraints**

Example:

<img src = "https://user-images.githubusercontent.com/118953932/208243318-7d0a499b-5144-42f8-b99e-75924869f6ef.png" height = "240"><img src = "https://user-images.githubusercontent.com/118953932/208243411-c07e906c-51b6-44dc-b0bb-b5477e7f22c2.png" height = "240">

<img src = "https://user-images.githubusercontent.com/118953932/208243655-1af8d515-2810-4308-810a-5e37bf56d6fc.png" height = "240"><img src = "https://user-images.githubusercontent.com/118953932/208243852-66fb82d8-837f-4a20-a4a5-5a894942ea91.png" height = "240">

Logic Synthesis
- Working Digital Logic Circuit
  - logically correct ✔️
  - electrically correct ✔️
  - timing met ✔️
- implementation 3 offers very less area and delay! 🥇
- but need to observe the hold met or not
  - to meet it we have to add delay (buffers)
    - add additional area 

What is the correct recipie?
- Constraints:
  - constraints are the guide to the synthesizer to pick the correct library cells which is the most for appropriate for the design
  - as illustrated implementation 1, 2, 3 all are correct and will be picked based on need or requirement

 </details>
 
## DC_D1SK1_L2 - Lecture2 - Intro to DC

**What is DC** ❔
- Design Compiler (DC): synthesis tool targeted for ASIC design flow from Synopsys
- Features of DC
  - established as a premium synthesis tool across semiconductor industry
  - interoperability with various backend tools from Synopsys
  - has the ability to perform DFT Scan stitch
  - can handle huge designs with extreme complexity and provide very good QoR

**Common Terminologies associated with DC** 🤔
- SDC (Synopsys Design Constraints): design constraints which are supplied to DC to enable appropriate optimization suitable for achieving the best implementation
  - Industry standard: used across Electronic Design Automation (EDA) implementation tools
- .LIB: Design Library which contains the standard cells
- DB: (same as .lib but in different format) understand libraries in .db format (convert .lib in db and then supply to DC)
- DDC: synopsys proprietary format for storing the design information. can write out and read in DDC
- Design: RTL files which has the behavioral model of the design

**Synopsys Design Constraints (SDC)**
- design intent in terms of timing, power and area constraints
- supported by EDA tools across  semiconductor industry
- based on Tool Command Language (TCL)

**DC Setup**

| Tools to setup | Supply to |
| ----- | ----- |
| RTL files | Design Compiler: |
|Library files|- verilog netlist|
|Constraints (SDC)|- DDC|
| |- synthesis reports|


**Implementation Flow of ASIC**
- steps in converting RTL to physical database (GDS)

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/208281661-da738be7-c9ef-4bd7-8076-a0ba003fb00c.png" height = "250"></p>

**DC Synthesis Flow**

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/208281929-7d6d08a4-8813-4eb0-b1c0-307bde269e8e.png" height = "250"></p>

## DC_D1SK2_L1 - lab1 - Invoking dc basic setup

1. change directory 
```
cd /nfs/png/disks/png_mip_gen6p9ddr_0032/nurul
```
2. make directory 
```
mkdir VLSI
```
3. git clone
```
git clone https://github.com/kunalg123/sky130RTLDesignAndSynthesisWorkshop.git
```
4. change directory
```
cd sky130RTLDesignAndSynthesisWorkshop
```
5. open DC_WORKSHOP
```
cd DC_WORKSHOP
```
6. open lib
```
cd lib
```
7. see list files 
```
ls

output: sky130_fd_sc_hd__tt_025C_1v80.db  sky130_fd_sc_hd__tt_025C_1v80.lib
```
**Note: DC can only read .db format. for reading and understanding, we will use .lib. for the tool, it will look at .db**

8. reading .lib

```
gvim sky130_fd_sc_hd__tt_025C_1v80.lib

:syn off (inside gvim: to close the syntax)
```

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/208288535-0c282ddd-7e1c-4725-a036-1fcc70036a77.png" height = "450"></p>

```
inside gvim
:se nu (number or line)
/cell (.*and [to find keyword cell & and]
/cell (.*inv [to find keyword cell & inv]
/cell (.*or [to find keyword cell & or]
```

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/208288884-9e5e03d5-cfc2-4159-8cf8-46c73af903ab.png" height = "180"><img src = "https://user-images.githubusercontent.com/118953932/208288822-e095fa46-ccbb-41ac-86b8-6174ed30eac6.png" height = "180"></p>


<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/208288999-9910cb09-fa23-4f09-a28c-d27319fd3371.png" height = "180"><img src = "https://user-images.githubusercontent.com/118953932/208289081-5b691191-5c8c-403b-8382-622f7cb4fb30.png" height = "180"></p>


<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/208289114-a50b9789-c79a-4ffd-9b29-d4e81af8af43.png" height = "180"><img src = "https://user-images.githubusercontent.com/118953932/208289178-ebdac398-1a65-4613-abe9-6599a9469405.png" height = "180"></p>

9. to invoke DC
```
cd ..
cd ..
/p/hdk/pu_tu/prd/sams/mig76_wlw/setup/enter_p31 -cfg ip76p31r08hp7rev03 -ov ./
csh
dc_shell
```
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/208290407-ae80aeef-4a90-4422-8fcd-3c8e4a31efda.png" height = "300"></p>

10. read std cell/tech .lib
```
echo $target_library
echo $link_library
``` 
**Note: used by the DC**

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/208290550-76b7b1f0-0745-4b3c-902f-9f4f1edf8b07.png" height = "300"></p>

11. exit
12. understanding file
```
gvim DC_WORKSHOP/verilog_files/lab1_flop_with_en.v
```
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/208290976-b5b5cbc0-141c-4fa8-9fd3-b5e16115d112.png" height = "300"></p>

13. read_verilog
```
read_verilog DC_WORKSHOP/verilog_files/lab1_flop_with_en.v
```
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/208291257-0968d46d-bd23-427c-8271-d8b05eac12b4.png" height = "300"></p>

14. write verilog
```
write -f verilog -out lab1_net.v

output: 
Warning: Can't read link_library file 'your_library.db'. (UID-3)
Writing verilog file '/nfs/png/disks/png_mip_gen6p9ddr_0032/nurul/VLSI/sky130RTLDesignAndSynthesisWorkshop/lab1_net.v'.

sh gvim lab1_net.v &
```
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/208291590-52eb715c-3fd2-4790-b950-18a0cdb1ba6b.png" height = "300"></p>

15. load the sky130 library
```
read_db DC_WORKSHOP/lib/sky130_fd_sc_hd__tt_025C_1v80.db
 
output:
Loading db file '/nfs/png/disks/png_mip_gen6p9ddr_0032/nurul/VLSI/sky130RTLDesignAndSynthesisWorkshop/DC_WORKSHOP/lib/sky130_fd_sc_hd__tt_025C_1v80.db'
Loaded 0 designs.

```
16. write verilog
```
write -f verilog -out lab1_net.v
sh gvim lab1_net.v &
```
**but it is still in gtech format - need to look at link_library and target_library (use echo $link_library)**
17. set library
```
set target_library /nfs/png/disks/png_mip_gen6p9ddr_0032/nurul/VLSI/sky130RTLDesignAndSynthesisWorkshop/DC_WORKSHOP/lib/sky130_fd_sc_hd__tt_025C_1v80.db
/nfs/png/disks/png_mip_gen6p9ddr_0032/nurul/VLSI/sky130RTLDesignAndSynthesisWorkshop/DC_WORKSHOP/lib/sky130_fd_sc_hd__tt_025C_1v80.db

set link_library {* /nfs/png/disks/png_mip_gen6p9ddr_0032/nurul/VLSI/sky130RTLDesignAndSynthesisWorkshop/DC_WORKSHOP/lib/sky130_fd_sc_hd__tt_025C_1v80.db}
```
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/208292352-d15efd21-0dc2-4f6e-a866-3c616ba698e3.png" height = "250"><img src = "https://user-images.githubusercontent.com/118953932/208292498-7b1fc2f1-0738-4410-bd03-7bcf2b323b71.png" height = "250"></p>

18. link
```
link

output:
  Linking design 'lab1_flop_with_en'
  Using the following designs and libraries:
  --------------------------------------------------------------------------
  lab1_flop_with_en           /nfs/png/disks/png_mip_gen6p9ddr_0032/nurul/VLSI/sky130RTLDesignAndSynthesisWorkshop/DC_WORKSHOP/verilog_files/lab1_flop_with_en.db
  sky130_fd_sc_hd__tt_025C_1v80 (library) /nfs/png/disks/png_mip_gen6p9ddr_0032/nurul/VLSI/sky130RTLDesignAndSynthesisWorkshop/DC_WORKSHOP/lib/sky130_fd_sc_hd__tt_025C_1v80.db
```
19. compile the design
```
compile
```
20. write new verilog
```
write -f verilog -out lab1_net_with_sky130.v
sh gvim lab1_net_with_sky130.v &

(inside gvim open the other file without using sky130)
:sp lab1_net.v
```
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/208292995-115275cb-e338-4678-8741-09af2d4aef96.png" height = "350"></p>

## DC_D1SK2_L2 - lab2 - Intro to ddc gui with design_vision

Design Vision
- supports gui

1. Write the previous lab in the format DDC
```
dc_shell> write -f ddc -out lab1.ddc
```
2. Launch Design Vision
```
csh
design_vision
```
3. Start gui
```
start_gui
```
4. read
```
read_ddc lab1.ddc
```
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/208297853-a80a97bf-fb4c-45dd-9468-6d81c906550b.png" height = "300"><img src = "https://user-images.githubusercontent.com/118953932/208298229-62b1eae7-a388-483b-a067-abf3610c2b4f.png" height = "300"></p>

**if use read_verilog = only read the verilog file**

**disadvantage: synopsys proprietary format (only understood by synopsys tool)**

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/208298410-d6f5ecec-b23c-4b98-b7e0-0a8886fdf2f0.png" height = "250"><img src = "https://user-images.githubusercontent.com/118953932/208298629-3aa78a51-7896-40cb-9ddb-7620b1a9d9f0.png" height = "300"></p>

## DC_D1SK2_L3 - lab3 - dc synopsys dc setup

1. open dc_shell
```
csh
dc_shell
```
2. check library
```
echo $target_library
echo $link_library
```
3. set library
```
set target_library DC_WORKSHOP/lib/sky130_fd_sc_hd__tt_025C_1v80.db
set link_library {* $target_library}
```
4. check library
```
echo $target_library

output: DC_WORKSHOP/lib/sky130_fd_sc_hd__tt_025C_1v80.db

echo $link_library

output: * $target_library
```
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/208301176-fb8b772c-0c6e-48fa-a3b1-65bd68b34ab0.png" height = "300"></p>
**all repetetive tasks (mainly target lib and link lib) which is needed for tool setup can be pointed in this file**

**can set automatically with the help of synopsys**

5. synopsys
- quit dc_shell
- go to path /nfs/png/disks/png_mip_gen6p9ddr_0032/nurul/VLSI/sky130RTLDesignAndSynthesisWorkshop (need to be in here)
```
gvim .synopsys_dc.setup

(inside gvim)
set target_library DC_WORKSHOP/lib/sky130_fd_sc_hd__tt_025C_1v80.db
set link_library {* $target_library}
```
**MUST USE .synopsys_dc.setup or else it will set the dummy/imaginary library** ❗❗❗

6. invoke dc_shell
```
csh
dc_shell
```
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/208301779-de9f7896-2dac-4ca7-97ea-d46c3c1f472f.png" height = "300"></p>

<p align="center">automatically set sky130 library as target library and link library</p>

## DC_D1SK3_L1 - Lecture3 - TCL quick refresher

Advanced Synthesis and STA using DC

TCL Quick Refresher
- set
  - creating and storing information in variable
  - note a square brackets are used for nesting the commands in TCL

```
eg:
set a 5
set a [expr $a + $b]


first line: a = 5
second line: a = a+b
```

- if else
```
if {condition}{
      statements if true;
   } else {
      statements if false;
   }

eg:
if {$a < 10}{
      echo "$a is less than 10";
   } else {
      echo "$a is greater than 10";
   }
```

- while
```
while {condition}{
      statements
   }
   
eg:
set i 0
while {$i < 10}{
       echo $i;
       incr i;
}
``` 
 **do not put the wrong variables, it could lead to infinite loops**

- for 
```
for {looping var}{condition}{looping var modification}{
      statements
   }
   
eg:
for {set i 0}{$i < 10}{incr i}{
       echo $i;
}
``` 

- foreach (very useful in DC!)
```
foreach var list {
      statements
   }
   
eg:
set my_design_list [list u_top/u_mod1\
                       u_top/u_mod3]
foreach my_module $my_design_list {
       set_size_only $my_module;
}
``` 
> my_design_list = name of list

> "\\" next line is the continuation of present command

> entry will be fetch one by one (looping through every element of the list)

> foreach general tcl statemnet or command

- foreach_in_collection (DC Specific [very useful in DC!])

```
foreach_in_collection var collection {
      statements
   }
   
eg:

foreach_in_collection cell_name [get_cells * -hier]{
    set cell_name [get_object_name $cell_name];
    set ref_name [get_attribute [get_cells $cell_name]ref_name];
    echo $cell_name, $ref_name;
}
``` 

> collections are DC objects like lists which are returned by many DC commands

> Note: nesting of TCL commands (very much used in DC)

> DC specific commands will be explained in detail in upcoming sessions

![image](https://user-images.githubusercontent.com/118953932/208286222-3da8bfcd-316b-40fb-abb3-5760def8806c.png)

## DC_D1SK3_L2 - lab4 - tcl scripting

Example of commands in TCL:
- set, echo & incr
```
set i 0
echo $i
incr i
echo $i
```
output: 
> 1
- for
```
for {set i 0} {$i < 12} {incr i} {                                                             
              echo $i
}
```
output:
> 0 \
1 \
2 \
3 \
4 \
5 \
6 \
7 \
8 \
9 \
10 \
11 

- while
```
set i 0
while {$i < 11} {
echo $i;
incr i;
}
```

**OR**

```
while {$i < 11} {
echo $i;
set i [expr $i + 1];
}
```
output:
> 0 \
1 \
2 \
3 \
4 \
5 \
6 \
7 \
8 \
9 \
10 

- list (create list)
```
set mylist [list a b c d e f g];
echo $mylist
```
output:
> a b c d e f g
- foreach (loop)
```
foreach my_var $mylist {
echo $my_var;
}
```
output:
> a \
b \
c\
d\
e\
f\
g
- foreach_in_collection
```
get_lib_cells */*and*
```
output:
> {sky130_fd_sc_hd__tt_025C_1v80/sky130_fd_sc_hd__and2_0 sky130_fd_sc_hd__tt_025C_1v80/sky130_fd_sc_hd__and2_1 sky130_fd_sc_hd__tt_025C_1v80/sky130_fd_sc_hd__and2_2 sky130_fd_sc_hd__tt_025C_1v80/sky130_fd_sc_hd__and2_4 sky130_fd_sc_hd__tt_025C_1v80/sky130_fd_sc_hd__and2b_1 sky130_fd_sc_hd__tt_025C_1v80/sky130_fd_sc_hd__and2b_2 sky130_fd_sc_hd__tt_025C_1v80/sky130_fd_sc_hd__and2b_4 sky130_fd_sc_hd__tt_025C_1v80/sky130_fd_sc_hd__and3_1 sky130_fd_sc_hd__tt_025C_1v80/sky130_fd_sc_hd__and3_2 sky130_fd_sc_hd__tt_025C_1v80/sky130_fd_sc_hd__and3_4 sky130_fd_sc_hd__tt_025C_1v80/sky130_fd_sc_hd__and3b_1 sky130_fd_sc_hd__tt_025C_1v80/sky130_fd_sc_hd__and3b_2 sky130_fd_sc_hd__tt_025C_1v80/sky130_fd_sc_hd__and3b_4 sky130_fd_sc_hd__tt_025C_1v80/sky130_fd_sc_hd__and4_1 sky130_fd_sc_hd__tt_025C_1v80/sky130_fd_sc_hd__and4_2 sky130_fd_sc_hd__tt_025C_1v80/sky130_fd_sc_hd__and4_4 sky130_fd_sc_hd__tt_025C_1v80/sky130_fd_sc_hd__and4b_1 sky130_fd_sc_hd__tt_025C_1v80/sky130_fd_sc_hd__and4b_2 sky130_fd_sc_hd__tt_025C_1v80/sky130_fd_sc_hd__and4b_4 sky130_fd_sc_hd__tt_025C_1v80/sky130_fd_sc_hd__and4bb_1 sky130_fd_sc_hd__tt_025C_1v80/sky130_fd_sc_hd__and4bb_2 sky130_fd_sc_hd__tt_025C_1v80/sky130_fd_sc_hd__and4bb_4 sky130_fd_sc_hd__tt_025C_1v80/sky130_fd_sc_hd__nand2_1 sky130_fd_sc_hd__tt_025C_1v80/sky130_fd_sc_hd__nand2_2 sky130_fd_sc_hd__tt_025C_1v80/sky130_fd_sc_hd__nand2_4 sky130_fd_sc_hd__tt_025C_1v80/sky130_fd_sc_hd__nand2_8 sky130_fd_sc_hd__tt_025C_1v80/sky130_fd_sc_hd__nand2b_1 sky130_fd_sc_hd__tt_025C_1v80/sky130_fd_sc_hd__nand2b_2 sky130_fd_sc_hd__tt_025C_1v80/sky130_fd_sc_hd__nand2b_4 sky130_fd_sc_hd__tt_025C_1v80/sky130_fd_sc_hd__nand3_1 sky130_fd_sc_hd__tt_025C_1v80/sky130_fd_sc_hd__nand3_2 sky130_fd_sc_hd__tt_025C_1v80/sky130_fd_sc_hd__nand3_4 sky130_fd_sc_hd__tt_025C_1v80/sky130_fd_sc_hd__nand3b_1 sky130_fd_sc_hd__tt_025C_1v80/sky130_fd_sc_hd__nand3b_2 sky130_fd_sc_hd__tt_025C_1v80/sky130_fd_sc_hd__nand3b_4 sky130_fd_sc_hd__tt_025C_1v80/sky130_fd_sc_hd__nand4_1 sky130_fd_sc_hd__tt_025C_1v80/sky130_fd_sc_hd__nand4_2 sky130_fd_sc_hd__tt_025C_1v80/sky130_fd_sc_hd__nand4_4 sky130_fd_sc_hd__tt_025C_1v80/sky130_fd_sc_hd__nand4b_1 sky130_fd_sc_hd__tt_025C_1v80/sky130_fd_sc_hd__nand4b_2 sky130_fd_sc_hd__tt_025C_1v80/sky130_fd_sc_hd__nand4b_4 sky130_fd_sc_hd__tt_025C_1v80/sky130_fd_sc_hd__nand4bb_1 sky130_fd_sc_hd__tt_025C_1v80/sky130_fd_sc_hd__nand4bb_2 sky130_fd_sc_hd__tt_025C_1v80/sky130_fd_sc_hd__nand4bb_4}

**it's in curly braces so it is a collection** ☑️

```
foreach_in_collection my_var [get_lib_cells */*and*] {
echo $my_var;
}
```

output:

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/208304894-388abebb-7930-48c4-8572-cdde68efe278.png" height = "300"></p>

Hence, need to use this:

```
foreach_in_collection my_var [get_lib_cells */*and*] {
set my_var_name [get_object_name $my_var]; echo $my_var_name;
}
```
output:

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/208305137-6939b7ac-c900-4de4-9ec3-12cb0c8875ae.png" height = "300"></p>

- multiple of these commands
```
sh gvim &

(inside gvim)

foreach_in_collection my_var [get_lib_cells */*and*] {
	set my_var_name [get_object_name $my_var]; echo $my_var_name;
}

echo "Printing Multiplication Table"

set i 10;
set j 1;
while {$j < 21} {
	echo $i*$j;
	incr j;
}

:w! myscript.tcl
:q!

source myscript.tcl
```

output:

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/208305600-e3cf3e0f-c25a-4302-bc42-0cc570dbb431.png" height = "300"></p>

```
sh gvim myscript.tcl &

(inside gvim)

foreach_in_collection my_var [get_lib_cells */*and*] {
	set my_var_name [get_object_name $my_var]; echo $my_var_name;
}

echo "Printing Multiplication Table"

set i 10;
set j 1;
while {$j < 21} {
	echo [expr $i*$j];
	incr j;
}

:wq!
```

output:

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/208305819-5b1dd5ea-4663-4c2a-b9c1-a3fdb32ef1e3.png" height = "350"></p>

- create list in gvim
```
gvim myscript.tcl &

(inside gvim add below original code)

set mylist [list a b c d e f g];

foreach myvar $mylist {
	echo $myvar;
}
echo $mylist;

:wq!

source myscript.tcl
```

output: 

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/208306051-314217a5-fa5f-4434-ad02-6a557fa50946.png" height = "350"></p>

# Day-7
## Basics of STA
### DC_D2SK1_L1 - lect4 - Intro to STA

STA = Static Timing Analysis

-	a way of evaluating a design's timing performance by testing for timing violations along all conceivable paths
-	breaks a design down into timing paths, calculates the signal propagation delay along each path, and checks for violations of timing constraints inside the design and at the input/output interface
-	basically method of adding the net delays and cell delays to obtain path delays

Why STA?
-	complete and exhaustive verification of all timing checks of a design
-	provides a faster and simpler way of checking and analyzing all the timing paths in a design for any timing violations

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/208794142-0d2de31d-bfd0-4c9f-bdb0-05ed43d99538.png" height = "350"></p>
<p align="center">source: physicaldesign4u</p>

**Max and Min Delay Constraints**

Path = multiple path in combinational logic, Case = interms of condition or PVT

Min Delay = shortest path and best case 

Max Delay = longest path and worst case 

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/208801934-57cddfa5-cd21-4879-8f49-6632eb1420d9.png" height = "200"><img src = "https://user-images.githubusercontent.com/118953932/208802218-f1dba537-c4de-4892-a216-9398b4b9219d.png" height = "200"></p> 


**Why Delay: Water Bucket Analogy**

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/208796698-879f85a3-4134-4018-862c-95ffa94662cc.png" height = "200"><img src = "https://user-images.githubusercontent.com/118953932/208797418-fb027be9-5d8d-4ed6-885a-e339318a3fe9.png" height = "200"></p> 

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/208797870-05c27c5e-68ee-4db8-bd88-ce74b5b1f9d6.png" height = "110"><img src = "https://user-images.githubusercontent.com/118953932/208798008-281687b8-e025-481f-bd56-11ff49396240.png" height = "110"></p> 

-	delay of a cell will be a function of input transition (inflow)
-	delay of a cell will be a function of output load (size of the bucket)
-	delay will increase if capacitance is large (lengthy net)
-	delay of a gate is a function of input of transition and output of a load
-	if a gate feeding to more gate, load capacitance increase and delay gate will also increase

**Timing Arc**
-	Combinational cell
	-	delay information from every input pin to every output pin which it can control
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/208799532-fc98ecce-42b6-4607-af92-6c355b21a1bc.png" height = "150"><img src = "https://user-images.githubusercontent.com/118953932/208799364-74efd11a-7735-41aa-9fe3-2f4404ec8c00.png" height = "150"></p> 
-	Sequential cell (DFF, D Latch)
	-	delay from Clock to Q to DFF
	-	delay from Clock to Q, Delay from D to Q for D Latch
	-	setup and hold time

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/208800831-fbf543ba-7a2d-42fe-a694-962112fa88ae.png" height = "350"></p>

### DC_D2SK1_L2 - Lect5 - What are constraints?

**Timing Path**

-	the path between start point and end point
-	each timing path has it's own "Start Point" and "End Point"

STA tool analyzes all paths from each and every startpoint to each and every endpoint and compares it against the constarint that exist for the path.

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/208806009-3e174c6a-b70b-4c84-a5a8-bfd9dfcc8b15.png" height = "350"><img src = "https://user-images.githubusercontent.com/118953932/208807736-63368f0b-d2d7-47bd-ad95-3ba38fa48e52.png" height = "250"></p>

Critical Path:
-	timing-sensitive functional path (no additional gates are allowed to be added to the path, to prevent increasing delay of the critical path)
-	the longest path in the circuit and limits the clock speed

Timing Paths:
-	start points
	-	input ports
	-	clock pins of register
-	end points
	-	output ports
	-	D pin of DFF/DLAT
-	always the timing paths start at one of the start points and ends at one of the end points
	-	clk to D (Reg 2 Reg Timing Path)
	-	Clk to Output (IO Timing Path)
	-	Input to D (IO Timing Path)
	-	Input to Output (IO Paths that ideally should not be present)

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/208814412-862a01e4-8c89-428b-9871-1d33dc930b5e.png" height = "350"></p>

**Constraining the Design - why constraints?**

-	D clock decides how much D combi logic are allowed


<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/208815853-b71adb76-ac2e-4d66-af5b-78dfc5646871.png" height = "350"></p>

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/208816371-f9e0deed-e5d3-4267-a1e9-226bcba439da.png" height = "250"><img src = "https://user-images.githubusercontent.com/118953932/208816603-970db57d-2a4e-44f4-9f41-588dbfb31ad3.png" height = "250"></p>

-	REG 2 REG: constrained by clock
-	REG 2 OUT: constrained by output external delay and clock period
-	IN 2 REG: constrained by input external delay and clock period
-	Collectively the REG2OUT and IN2REG are called IO paths and the delay modelling are referred above is called IO Delay Modelling

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/208818056-7991d386-feef-447f-a6f9-4113fdf0c8b6.png" height = "350"></p>

**Note: logic delay is the one that has to be adjustable/need to be squeeze**

### DC_D2SK1_L3 - Lect6 - Inp Trans Output Load

**IO Constraints**

**IO: IO Delay Modelling Sufficient?**

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/208818868-73ad2834-003c-4b30-8f12-5d47fc71df1b.png" height = "250"><img src = "https://user-images.githubusercontent.com/118953932/208819344-99c0d8fa-7db2-4c29-b32c-430dfb9a3ba6.png" height = "250"></p>

need input transition modelling.

**IO Delay and Input Transition Modelling Sufficient for IO Paths**

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/208820685-0ec31504-069e-4a46-b91b-09f7c32cfabb.png" height = "280"><img src = "https://user-images.githubusercontent.com/118953932/208821231-7bbe01c8-c6f4-432a-a727-4c9448c8918f.png" height = "280"></p>

-	REG 2 REG: constrained by clock
-	REG 2 OUT: constrained by output external delay, output load and clock period
-	IN 2 REG: constrained by input external delay, input transition and clock period
-	note: the IO paths needs to be constrained for both Max delay (setup) and Min delay (hold)

### DC_D2SK2_L1 - Lab5 - Timing dot Libs

**Exploring .lib**
 
We are not able to read .db because it is meant for DC and only DC understood it.
 
The information included in the .lib are such as: 
1)	library name
2)	units used
3)	technology used
4)	max constraint
5)	PVT
6)	delay model
 
 <p align="center"><img src = "https://user-images.githubusercontent.com/118953932/208835930-51c112ac-54c7-4ccb-a396-90bbff4fc33a.png" height = "200"><img src = "https://user-images.githubusercontent.com/118953932/208836560-d646699a-1e42-49ee-ac02-bfba2fc5eb1d.png" height = "250"></p>
 
 <p align="center"><img src = "https://user-images.githubusercontent.com/118953932/208840971-26b4f7ea-6296-487f-97c3-02b9d7401d6b.png" height = "300"></p>
 
 fanout = the number of input pins that are connected to a specific output pin
 
 net = connecting the output to all the inputs
 
 capacitance = gate terminal of a MOSFET
 
 <p align="center"><img src = "https://user-images.githubusercontent.com/118953932/208841036-2b849399-9e99-4e32-9ee6-3435ecff87e1.png" height = "350"></p>
  
 **Delay Model Lookup Table**
 
There are table for every cell. It will use to look for the delay using the output load and input transition. 
-	will calculate and do interpolation
-	there are multiple things that wil be present in the lookup table

 <p align="center"><img src = "https://user-images.githubusercontent.com/118953932/208843043-b06fda7e-7a22-4cb1-bd98-315aa2256a2f.png" height = "300"></p>
 
 **Note: lut = lookup table**


 <p align="center"><img src = "https://user-images.githubusercontent.com/118953932/208850708-7fd151ea-158b-4a4e-a4d9-1ac2071e2ef7.png" height = "500"></p>
 <p align="center"><img src = "https://user-images.githubusercontent.com/118953932/208852043-e9ff5939-b422-48f3-861a-07a46ed28641.png" height = "400"></p>
 
 Tools need to know unateness to propagate transition.
 
 AND & OR = positive unate
 
 NOT, NAND & NOR = negative unate
 
 XOR = both pos & neg unate

**Gates**

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/208844891-83ee2f59-4d28-4690-b04b-61570dab4959.png" height = "400"></p>

**Attribute**
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/208846187-80f02d0d-ca3e-437b-9e78-87c4f044a672.png" height = "500"></p>

-	clock pin
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/208848071-fcd2bf0b-314b-4a83-a86b-3e2aedd1d599.png" height = "500"></p>

### DC_D2SK2_L2 - Lab6 - Exploring dotLib

Example:

 cell ("sky130_fd_sc_hd__sdfbb**n**_1") = neg edge flop (n for negative edge flop, p for positive edge flop)
 
 Timing type: falling edge (if rising type, it's pos edge flop)
 
 <p align="center"><img src = "https://user-images.githubusercontent.com/118953932/208860403-d93b9212-3bd8-4408-840b-46f9aadb8951.png" height = "380"><img src = "https://user-images.githubusercontent.com/118953932/208862499-b55d511a-ccc8-4875-bb65-2815b7714f10.png" height = "250"></p>
 <p align="center"><img src = "https://user-images.githubusercontent.com/118953932/208864506-9c3da738-1317-4e8f-9705-4b869c99a8b9.png" height = "350"></p>
 
 <p align="center"><img src = "https://user-images.githubusercontent.com/118953932/208866025-b4ae4aa4-eb02-4a65-8499-ab2ef20fb306.png" height = "150"></p>
 
 Latch
 
 Command to look for library cell
 ```
 dc_shell> get_lib_cells */* -filter "is_sequential==true"
 ```
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/208869177-69116f4f-6086-472a-b97d-dbf2bdec997d.png" height = "350"></p>

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/208870305-c0284681-cee3-422a-a9af-f54be0470ad8.png" height = "400"><img src = "https://user-images.githubusercontent.com/118953932/208870844-a90d1566-e39f-4adb-ad87-b811f0ea247d.png" height = "300"></p>

### DC_D2SK2_L3 - Lab7 - Exploring - dotLib part2

**Properties of the .lib**

-	Library loaded
```
dc_shell> list_lib
```
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/208886428-a9d557a5-bf2c-4de9-b34e-aedf56d497b4.png" height = "150"></p>

currently loaded: sky130_fd_sc_hd__tt_025C_1v80

-	Want to know all the AND gate available in the library

>	in a collection form
```
dc_shell> get_lib_cells */*and* 
```

>	in list form
```
dc_shell> foreach_in_collection my_lib_cell [get_lib_cells */*and*] {
set my_lib_cell_name [get_object_name $my_lib_cell]; echo $my_lib_cell_name;
}
```
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/208888584-da502ce0-c97a-4531-88df-577abf253ff2.png" height = "200"><img src = "https://user-images.githubusercontent.com/118953932/208888835-ae8a86c2-c0ce-468d-aa29-92bf21e29090.png" height = "400"></p>

**DO NOT DO THIS AS IT WILL ONLY PRINT OUT THE POINTER** ❗
```
dc_shell> foreach_in_collection my_lib_cell [get_lib_cells */*and*] {
echo $my_lib_cell;
}
```
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/208889163-58e8599a-f884-497b-af5f-618087f4a8b9.png" height = "350"></p>

-	Want to know the pins available for a specific gate
```
dc_shell> get_lib_pins sky130_fd_sc_hd__tt_025C_1v80/sky130_fd_sc_hd__and2_0/*
```
Output:
>	{sky130_fd_sc_hd__tt_025C_1v80/sky130_fd_sc_hd__and2_0/A sky130_fd_sc_hd__tt_025C_1v80/sky130_fd_sc_hd__and2_0/B sky130_fdd__tt_025C_1v80/sky130_fd_sc_hd__and2_0/X}
-	Functionality of this gate
```
dc_shell> foreach_in_collection my_pins [get_lib_pins sky130_fd_sc_hd__tt_025C_1v80/sky130_fd_sc_hd__and2_0/*] {                  
set my_pin_name [get_object_name $my_pins];                                                                               
set pin_dir [get_lib_attribute $my_pin_name direction];                                                                   
echo $my_pin_name $pin_dir;                                                                                               
}                                                                                                                
```
>	can use this also to double confirm:
```
dc_shell> get_lib_attribute sky130_fd_sc_hd__tt_025C_1v80/sky130_fd_sc_hd__and2_0/X function
```
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/208891544-f8a7f4a0-85c2-460e-a1c0-1e444e207983.png" height = "150"><img src = "https://user-images.githubusercontent.com/118953932/208892371-7e8993e6-568a-4d84-87c5-4ddf0dfb2399.png" height = "130"></p>

Another Example:
-	nand4_1

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/208893699-6838ddde-4869-4dbd-b82e-963b4b1821bf.png" height = "250"></p>

-	and2b_1 & and4bb_1
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/208895051-fcd93f2b-c16d-44c6-85e4-b75c9a5054a8.png" height = "250"></p>

-	Writing script to print out output pin names and its functionality
```
dc_shell> sh gvim my_script.tcl

(inside gvim)
set my_list [list
*paste the gates copied]



#For each cell in the list, find the output pin name and its functionality


foreach my_cell $my_list {
	foreach_in_collection my_lib_pin [get_lib_pins ${my_cell}/*] {
		set my_lib_pin_name [get_object_name $my_lib_pin];
		set a [get_lib_attribute $my_lib_pin_name direction];
		if {a > 1} {
			set fn [get_lib_attribute $my_lib_pin_name function];
			echo $my_lib_pin_name $a $fn];
		}
	}
}

dc_shell> source my_script.tcl
```
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/208901398-2e7db589-c2f9-4c70-ada3-fc4550694b20.png" height = "350"><img src = "https://user-images.githubusercontent.com/118953932/208901892-7f0247bd-c89c-46c6-851f-11a54be4199d.png" height = "360"></p>

-	Can also use to get attribute that we wanted (eg: area, capacitance, clock pin or not)
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/208902517-a6854b3e-afe5-457e-bd2a-62d88be6104d.png" height = "150"></p>

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/208904142-a7a161b7-81dd-4549-b558-34dd7b2b0270.png" height = "450"></p>

-	To know all the attribute
```
dc_shell> list_attributes -app

(move it to a file)

dc_shell> list_attributes -app > a
dc_shell> sh gvim a &
```


<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/208905199-6a7800d0-6824-4bbf-9fde-1d775a0d470d.png" height = "550"></p>

# Day - 8
## Advanced constraints
### DC_D3SK1_L1 - Lecture7 - SDC Part1 Clock - Clock Tree Modelling - Uncertainty

Reg to Reg path = contraints by clock period (Tclk >= Tcq + Tcombi + Ts)

Input to Reg path = constraints by clock, input delay and input transition

Output to Reg path = constraints by clock, output delay and load

**What need to be contrainted for clocks (is clock period sufficient?)**


<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/209048821-28dd0db7-927b-4335-9ae4-411de7de3e7b.png" height = "300"></p>

Will clock arrive at the same time at these flops?
>	the answer is no

**Implementation Flow of ASIC**
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/209050705-2fa7f0ea-882c-40f7-90ea-3c1fe0fb4de0.png" height = "350"></p>
Should synthesis consider the practicality of clock network ❓

**Clock Generation**
-	Oscilator
-	PLL
-	External Clock Source
-	All the above clock sources have inherent variations in the clock period due to stochastic effects (jitter)

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/209052686-bc73785f-347a-4141-be92-0b81f9137fab.png" height = "400"></p>

jitter cause by stochastic variation clock generator

**Clock Distribution**
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/209054049-66a631b8-ab47-404a-9dc5-62e3fbb3426f.png" height = "400"></p>

**Clock Skew**
>	The difference in the arrival time of a clock signal at two different registers, which can be caused by path length differences between two clock paths.
>	caused by clock tree distribution network
-	clock tree built during CTS: practical Clock Tree
-	Logic optimization happens during in synthesis: Ideal Clock Tree
-	Timing Clean paths in Synthesis may fail after STA


<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/209055170-22ef9585-dee6-473a-97a8-8346488a06a9.png" height = "300"></p>

**Clock Modelling**
-	model the clock for following
	-	period
	-	source latency: time taken by the clock source to generate clock
	-	clock network latency: time taken by clock distribution network
	-	clock skew: clock path delay mismatches which causes difference in the arrival of clock
		-	CTS will balance clocks but still skew cannot be reduced to 0
	-	jitter: stochastic variation in the arrival of clock edge
		-	duty cycle jitter
		-	period jitter
	-	clock skew & jitter is called clock uncertainty
-	post CTS, the clock network is real and hence these modelled clock skew and clock network latency must be removed ❗

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/209075053-d4b5dd46-87b8-47fe-bc73-991a5c83897e.png" height = "200"><img src = "https://user-images.githubusercontent.com/118953932/209075946-65c436ce-74ac-47aa-a1a0-e16eb1565750.png" height = "200"></p>

| Stage | Clock Uncertainty |
| ----- | ----- |
| Synthesis | Jitter + Skew |
| Post CTS | Only Jitter |

### DC_D3SK1_L2 - Lecture8 - SDC Part2 IO delays

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/209143985-76293996-ec99-4cdd-a125-62d89d01fd17.png" height = "350"></p>

Nets = connections of 2 or more pins or pins and ports

**Commands to use**

-	To get the ports
```
get_ports clk;
get_ports *clk*;                         #a collections of ports
get_ports *;                             #get all ports
get_ports * -filter "direction==in";     #all input ports
get_ports * -filter "direction==out";    #all output ports
```

-	To get the clocks
```
get_clocks *                                        #all the clocks
get_clocks *clk*                                    #all clocks which has the name clk in it
get_clocks * - filter "period>10"                   #condition this query which get the attribute of period
get_attribute [get_clocks my_clk] is_generated
report_clocks my_clk                                #report all the detail of the clock
```

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/209251370-fdc461b1-aba7-4c49-9bd8-817396ccab5a.png" height = "350"></p>

**Clock Distribution**

Command to create clock
```
create_clock -name <clock name> -per <period> [clock definition point (eg: get_ports CLK)]

set_clock_latency 3 MY_CLK;    #this is the latency, modelling the clock delay in network

set_clock_uncertainty 0.5 MY_CLK;   #this is for setting the clock network (skew+jitter) pre CTS
```

Note: clocks must be created on the clock generators (PLL, OSCILLATORS) or Primary IO Pins (for external clocks). Clocks should not be created on hierarchical pins which are not clock generators

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/209252791-d4e7b3e2-aed5-479d-80f0-fed5a17d008b.png" height = "350"></p>

**Clocks - Waveform**

create waveform
```
create_clock -name MYCLK -per [get_ports clk] #default which means rise at 0 fall at 5
create_clock -name MYCLK -per [get_ports clk] -wave {5 10}  #rise at 5 fall at 10
```

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/209253449-16c6b8a4-eb74-4b0e-8821-07b1650389d1.png" height = "350"></p>

**Constraining the IO Paths**
Constraint the Input
```
set_input_delay -max 3 -clock [get_clocks MY_CLK][get_ports IN_*];
set_input_delay -min 1.5 -clock [get_clocks MY_CLK][get_ports IN_*];
set_input_transition -max 1.5 [get_ports IN_*];
set_input_transition -min .75 [get_ports IN_*];
```

Note: Both inputs IN_A, IN_B are coming wrt clock MY_CLK created on port CLK

Constraint the Input
```
set_output_delay -max 3 -clock [get_clocks MY_CLK][get_ports Out_y];
set_output_delay -min 0.5 -clock [get_clocks MY_CLK][get_ports Out_y];
set_output_load -max 80 [get_ports Out_y];
set_output_load -min 20 [get_ports Out_y];
```
Note: Output Out_y is generated wrt clock MY_CLK created on port CLK

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/209257037-43282ff4-c064-485c-9f34-f73062d5c103.png" height = "250"></p>

### DC_D3SK2_L1 - Lab8 - Loading design get_cells, get_ports, get_nets

Reading the file
```
cd /nfs/png/disks/png_mip_gen6p9ddr_0032/nurul/VLSI/sky130RTLDesignAndSynthesisWorkshop/DC_WORKSHOP/verilog_files
gvim lab8_circuit.v
```
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/209259993-fe00a5d9-8779-4d2b-95f6-8d66f2e8155d.png" height = "400"></p>


```
dc_shell> echo $target_library
dc_shell> echo $link_library
dc_shell> read_verilog lab8_circuit.v
```
make sure target_library and link_library are correct

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/209261889-ac3d7031-fcd1-4fc1-bb0c-124e56cbf6a5.png" height = "200"></p>

```
dc_shell> link
dc_shell> compile_ultra
```
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/209270352-428dd471-6e7c-4caa-af82-0025f5158b52.png" height = "350"></p>

```
dc_shell> get_ports
#output 
{rst clk IN_A IN_B OUT_Y out_clk} #collection
dc_shell>  foreach_in_collection my_port [get_ports *] {
set my_port_name [get_object_name $my_port]; echo $my_port_name; }
#output 
rst
clk
IN_A
IN_B
OUT_Y
out_clk
```

**To know the direction of a port**

```
dc_shell> get_ports rst
{rst}
dc_shell> get_attribute [get_ports rst] direction
in

```

**To know the direction of ports**

```
dc_shell> foreach_in_collection my_port [get_ports *] {
set my_port_name [get_object_name $my_port];
set dir [get_attribute [get_ports $my_port_name] direction];
echo $my_port_name $dir;
}
rst in
clk in
IN_A in
IN_B in
OUT_Y out
out_clk out
```

**Get Cells**

```
dc_shell> get_cells *
{REGA_reg REGB_reg REGC_reg U9 U10 U11 U12 U13 U14}
dc_shell> get_attribute [get_cells U9] is_hierarchical
false
dc_shell> get_attribute [get_cells U12] is_hierarchical
false
dc_shell> get_attribute [get_cells REGA_reg] is_hierarchical
false
dc_shell> get_cells * -filter "is_hierarchical == false"
{REGA_reg REGB_reg REGC_reg U9 U10 U11 U12 U13 U14}

```

Note: design has no hierarchical (the design only got 1 module)

Note: 
-	"REGC_reg" is instance name
-	reference name is name of the physical cell in the .lib

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/209272090-9c9ecb5e-1b11-4931-9d2c-8f879c4564a2.png" height = "350"><img src = "https://user-images.githubusercontent.com/118953932/209272977-c093d7f1-14c8-4440-9eaa-01f53500dd01.png" height = "350"></p>

**Get reference name of cell**

```
dc_shell> get_attribute [get_cells REGA_reg] ref_name
sky130_fd_sc_hd__dfrtp_1
# d flip flop with an asynchronous reset, posedge trigger and giving positive output (t =true output)

#ref name for all cells in the design

dc_shell> foreach_in_collection my_cell [get_cells * -hier] {                                                        
set my_cell_name [get_object_name $my_cell];                                                                 
set rname [get_attribute [get_cells $my_cell_name] ref_name];                                                
echo $my_cell_name $rname;                                                                                   
}
REGA_reg sky130_fd_sc_hd__dfrtp_1
REGB_reg sky130_fd_sc_hd__dfrtp_1
REGC_reg sky130_fd_sc_hd__dfrtp_1
U9 sky130_fd_sc_hd__clkinv_1
U10 sky130_fd_sc_hd__clkinv_1
U11 sky130_fd_sc_hd__nor2_1
U12 sky130_fd_sc_hd__clkinv_1
U13 sky130_fd_sc_hd__a21oi_1
U14 sky130_fd_sc_hd__nand2_1
```

Note: if output not in curly bracket, dont have to use get_object_name

**DDC**

```
dc_shell> write -f ddc -out lab8_circuit.ddc
Writing ddc file 'lab8_circuit.ddc'.
1

csh
design_vision

design_vision> pwd
/nfs/png/disks/png_mip_gen6p9ddr_0032/nurul/VLSI/sky130RTLDesignAndSynthesisWorkshop/DC_WORKSHOP/verilog_files

design_vision> read_ddc lab8_circuit.ddc
design_vision> get_nets *
{rst IN_A IN_B out_clk N0 N1 REGC REGB REGA n2 n3 OUT_Y n5}
design_vision> all_connected N1
{U13/Y REGB_reg/D}
```

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/209274430-86132a73-48d9-4bc8-9607-b3dd4856f39d.png" height = "450"></p>

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/209275422-fae3ad1b-0be7-4493-8683-3b1ad333a764.png" height = "250"></p>

**Want to know driver of the net**
```
design_vision> all_connected n5
{U11/Y U12/A U13/B1}

design_vision> foreach_in_collection my_pin [all_connected n5] {
set pin_name [get_object_name $my_pin];
set dir [get_attribute [get_pins $pin_name] direction];
echo $pin_name $dir;
}
U11/Y out
U12/A in
U13/B1 in
```

### DC_D3SK2_L2 - Lab9 get_pins, get_clocks, querying_clocks

**Get to know pins**

```
dc_shell> get_pins *
{REGA_reg/D REGA_reg/CLK REGA_reg/RESET_B REGA_reg/Q REGB_reg/D REGB_reg/CLK REGB_reg/RESET_B REGB_reg/Q REGC_reg/D REGC_reg/CLK REGC_reg/RESET_B REGC_reg/Q U9/A U9/Y U10/A U10/Y U11/A U11/B U11/Y U12/A U12/Y U13/A1 U13/A2 U13/B1 U13/Y U14/A U14/B U14/Y}

dc_shell> foreach_in_collection my_pin [get_pins *] {
set pin_name [get_object_name $my_pin];
echo $pin_name;
}
REGA_reg/D
REGA_reg/CLK
REGA_reg/RESET_B
REGA_reg/Q
REGB_reg/D
REGB_reg/CLK
REGB_reg/RESET_B
REGB_reg/Q
REGC_reg/D
REGC_reg/CLK
REGC_reg/RESET_B
REGC_reg/Q
U9/A
U9/Y
U10/A
U10/Y
U11/A
U11/B
U11/Y
U12/A
U12/Y
U13/A1
U13/A2
U13/B1
U13/Y
U14/A
U14/B
U14/Y

dc_shell> get_attribute [get_pins REGC_reg/RESET_B] direction
in

dc_shell> get_attribute [get_pins REGC_reg/RESET_B] clock
false

dc_shell> get_attribute [get_pins REGC_reg/CLK] clock
true

dc_shell> foreach_in_collection my_pin [get_pins *] {
set pin_name [get_object_name $my_pin];
set dir [get_attribute [get_pins $pin_name] direction];
echo $pin_name $dir;
}
REGA_reg/D in
REGA_reg/CLK in
REGA_reg/RESET_B in
REGA_reg/Q out
REGB_reg/D in
REGB_reg/CLK in
REGB_reg/RESET_B in
REGB_reg/Q out
REGC_reg/D in
REGC_reg/CLK in
REGC_reg/RESET_B in
REGC_reg/Q out
U9/A in
U9/Y out
U10/A in
U10/Y out
U11/A in
U11/B in
U11/Y out
U12/A in
U12/Y out
U13/A1 in
U13/A2 in
U13/B1 in
U13/Y out
U14/A in
U14/B in
U14/Y out

```
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/209283061-5134c30f-165c-46da-81b4-c2b4347bc989.png" height = "450"></p>

Note: clock attribute is present for input pin only

**Using regexp**

```
dc_shell> regexp abcd efgh
0
dc_shell> regexp abcd abcd
1
dc_shell>  set a in
in
dc_shell> regexp $a in
1
dc_shell> regexp $a out
0
dc_shell> foreach_in_collection my_pin [get_pins *] {
set pin_name [get_object_name $my_pin];                                                                                      
set dir [get_attribute [get_pins $pin_name] direction];                                                      
if { [regexp $dir in] } {                                                                                    
if { [get_attribute [get_pins $pin_name] clock] } {                                          
echo $pin_name;                                                                                              
}                                                                                                            
}                                                                                                            
}
REGA_reg/CLK
REGB_reg/CLK
REGC_reg/CLK
```

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/209283997-2fc217b0-d537-4a25-b094-838fdfd936ea.png" height = "450"></p>

Note: regexp will return one if it's matching

**Writing script**

```
dc_shell> sh gvim query_clock_pin.tcl &

(inside gvim)
foreach_in_collection my_pin [get_pins *] {
	set my_pin_name [get_object_name $my_pin];
        set dir [get_attribute [get_pins $my_pin_name] direction];                                                                                              
	if { [regexp $dir in] } {
		if { [get_attribute [get_pins $my_pin_name] clock ] } { 
			echo $my_pin_name $clk_name;

		}
	}
}	

dc_shell> source query_clock_pin.tcl
REGA_reg/CLK 
REGB_reg/CLK 
REGC_reg/CLK 
```

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/209285632-0a27e3e8-8008-4cb8-bbe4-8dbe6dc766ea.png" height = "450"></p>

**To check is there any clock coming in**

```
dc_shell> get_attribute [get_pins REGA_reg/CLK] clock
true
dc_shell> get_attribute [get_pins REGA_reg/CLK] clocks
Warning: Attribute 'clocks' does not exist on pin 'REGA_reg/CLK'. (UID-101)

```
Note:

get_attribute [get_pins REGA_reg/CLK] clock
-	To check if the pin meant to be a clock pin or not

get_attribute [get_pins REGA_reg/CLK] clock
-	What are the clocks reaching the pins

**Get the clock**
```
dc_shell> get_clocks *
Warning: Can't find clocks matching '*' in design 'lab8_circuit'. (UID-95)

#no clock because haven't created
```

### DC_D3SK2_L3 - lab10 - create_clock waveform

**To know the name of top moduel currently working**

```
dc_shell> current_design
Current design is 'lab8_circuit'.
{lab8_circuit}

```

**Get ports of the design**

```
dc_shell> get_ports *
{rst clk IN_A IN_B OUT_Y out_clk}
```

**Create Clock and Know Attribute**

```
dc_shell> create_clock -name MYCLK -per 10 [get_ports clk]
1

dc_shell> get_clocks *
{MYCLK}

dc_shell> get_attribute [get_clocks MYCLK] period
10.000000

dc_shell> get_attribute [get_clocks MYCLK] is_generated
false
#means it's a master clock

dc_shell> get_attribute [get_pins REGA_reg/CLK] clocks
{MYCLK}
```

**Reporting clocks**

```
dc_shell> report_clocks *
Information: Updating graph... (UID-83)
 
****************************************
Report : clocks
Design : lab8_circuit
Version: P-2019.03-SP5-3
Date   : Fri Dec 23 16:12:23 2022
****************************************

Attributes:
    d - dont_touch_network
    f - fix_hold
    p - propagated_clock
    G - generated_clock
    g - lib_generated_clock

Clock          Period   Waveform            Attrs     Sources
--------------------------------------------------------------------------------
MYCLK           10.00   {0 5}                         {clk}
--------------------------------------------------------------------------------
1

```

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/209298761-317ac8ac-7c88-4f7b-90d2-4a37c488c381.png" height = "450"></p>

```
dc_shell> get_attribute [get_pins REGA_reg/CLK] clocks
{MYCLK}
dc_shell> get_attribute [get_ports out_clk] clocks
{MYCLK}

dc_shell> sh gvim query_clock_pin.tcl 

(inside gvim)
foreach_in_collection my_pin [get_pins *] {
	set my_pin_name [get_object_name $my_pin];
        set dir [get_attribute [get_pins $my_pin_name] direction];                                                                                              
	if { [regexp $dir in] } {
		if { [get_attribute [get_pins $my_pin_name] clock ] } { 
			set clk [get_attribute [get_pins $my_pin_name] clocks]; # 	set clk_name [get_object_name [get_attribute [get_pins $my_pin_name] clocks]];
			set clk_name [get_object_name $clk];
 			echo $my_pin_name $clk_name;

		}
	}
}	

dc_shell> source query_clock_pin.tcl 
REGA_reg/CLK MYCLK
REGB_reg/CLK MYCLK
REGC_reg/CLK MYCLK

```

Conclusion: clock created and ensure it propagating everywhere

Note: create clock at port only

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/209302276-dd88a4d3-57a6-4ad7-b4a1-e8a286073028.png" height = "320"><img src = "https://user-images.githubusercontent.com/118953932/209302687-9aa1d262-65f4-4d25-9afd-725c6f1d798b.png" height = "300"></p>

```
dc_shell> create_clock -name BAD_CLK -per 10 [get_pins U14/Y]
1
dc_shell> get_clocks *
{MYCLK BAD_CLK}
dc_shell> report_clocks *
Information: Updating graph... (UID-83)
 
****************************************
Report : clocks
Design : lab8_circuit
Version: P-2019.03-SP5-3
Date   : Fri Dec 23 17:22:05 2022
****************************************

Attributes:
    d - dont_touch_network
    f - fix_hold
    p - propagated_clock
    G - generated_clock
    g - lib_generated_clock

Clock          Period   Waveform            Attrs     Sources
--------------------------------------------------------------------------------
BAD_CLK         10.00   {0 5}                         {U14/Y}
MYCLK           10.00   {0 5}                         {clk}
--------------------------------------------------------------------------------
1

#not reaching any clock pin of any flop and reaching the data path

dc_shell> all_connected U14/Y
{n3}

dc_shell> all_connected n3
{U14/Y REGC_reg/D}

#only confuses the tool and have no purpose
```

**Command to remove clock**

```
dc_shell> remove_clock BAD_CLK
1

dc_shell> get_clocks *
{MYCLK}

dc_shell> report_clocks *
Information: Updating graph... (UID-83)
 
****************************************
Report : clocks
Design : lab8_circuit
Version: P-2019.03-SP5-3
Date   : Fri Dec 23 17:30:05 2022
****************************************

Attributes:
    d - dont_touch_network
    f - fix_hold
    p - propagated_clock
    G - generated_clock
    g - lib_generated_clock

Clock          Period   Waveform            Attrs     Sources
--------------------------------------------------------------------------------
MYCLK           10.00   {0 5}                         {clk}
--------------------------------------------------------------------------------
1

```

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/209310674-31d47472-a5fa-4678-8f41-ee73511b9ae8.png" height = "350"></p>


**Adjusting Waveform**

```
dc_shell> remove_clock MYCLK
1

dc_shell> create_clock -name MYCLK -per 10 [get_ports clk] -wave {5 10}    #rise edge=5   fall edge =10
1

dc_shell> report_clocks *
Information: Updating graph... (UID-83)
 
****************************************
Report : clocks
Design : lab8_circuit
Version: P-2019.03-SP5-3
Date   : Fri Dec 23 17:34:59 2022
****************************************

Attributes:
    d - dont_touch_network
    f - fix_hold
    p - propagated_clock
    G - generated_clock
    g - lib_generated_clock

Clock          Period   Waveform            Attrs     Sources
--------------------------------------------------------------------------------
MYCLK           10.00   {5 10}                        {clk}
--------------------------------------------------------------------------------
1

```

**Adjusting Waveform**

```
dc_shell> remove_clock MYCLK
1
dc_shell> create_clock -name MYCLK -per 10 [get_ports clk] -wave {0 2.5}  #first rising edge = 0, fall edge = 2.5,  next rising edge = 10, fall edge =12.5
1

#order is not important

dc_shell> report_clocks *
Information: Updating graph... (UID-83)
 
****************************************
Report : clocks
Design : lab8_circuit
Version: P-2019.03-SP5-3
Date   : Fri Dec 23 17:38:49 2022
****************************************

Attributes:
    d - dont_touch_network
    f - fix_hold
    p - propagated_clock
    G - generated_clock
    g - lib_generated_clock

Clock          Period   Waveform            Attrs     Sources
--------------------------------------------------------------------------------
MYCLK           10.00   {0 0.25}                      {clk}
--------------------------------------------------------------------------------
1

#next waveform

dc_shell> remove_clock MYCLK
1
dc_shell> create_clock -name MYCLK -per 10 [get_ports clk] -wave {15 20}
1
dc_shell> report_clocks *
Information: Updating graph... (UID-83)
 
****************************************
Report : clocks
Design : lab8_circuit
Version: P-2019.03-SP5-3
Date   : Fri Dec 23 17:42:54 2022
****************************************

Attributes:
    d - dont_touch_network
    f - fix_hold
    p - propagated_clock
    G - generated_clock
    g - lib_generated_clock

Clock          Period   Waveform            Attrs     Sources
--------------------------------------------------------------------------------
MYCLK           10.00   {15 20}                       {clk}
--------------------------------------------------------------------------------
1

```


<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/209312783-aa3630e9-2d53-4952-8f81-f2383e073c64.png" height = "320"></p>

### DC_D3SK2_L4 - Lab11- Clock Network Modelling - Uncertainty, report_timing

Clock jitter is random variation in clock edge (source)

Clock skew is clock network (delay imbalance between flops)

CTS = clock tree synthesis (minimize the imbalance but cannot make it to 0)

clock uncertinty
-	skew + jitter (Pre CTS) 
-	jitter only because the clock network is actually built (post CTS)

Recall:

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/209323982-f4bbcb42-1468-4d14-9732-7e8b6d6edec1.png" height = "250"></p>

**Model the clock tree attribute**

```
dc_shell> report_clocks *
Information: Updating graph... (UID-83)
 
****************************************
Report : clocks
Design : lab8_circuit
Version: P-2019.03-SP5-3
Date   : Fri Dec 23 17:42:54 2022
****************************************

Attributes:
    d - dont_touch_network
    f - fix_hold
    p - propagated_clock
    G - generated_clock
    g - lib_generated_clock

Clock          Period   Waveform            Attrs     Sources
--------------------------------------------------------------------------------
MYCLK           10.00   {15 20}                       {clk}
--------------------------------------------------------------------------------
1
dc_shell> set_clock_latency -source 1 [get_clocks MYCLK] #modelling source latency
1
dc_shell> set_clock_latency 1 [get_clocks MYCLK] #modelling network latency
1
dc_shell> set_clock_uncertainty 0.5 [get_clocks MYCLK] #max delay time/setup time (default)
1
dc_shell> set_clock_uncertainty -hold 0.1 [get_clocks MYCLK] #min delay time/hold time
1

```

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/209324250-cc7307ce-6308-49ac-8238-f453bb7c7cf0.png" height = "350"><img src = "https://user-images.githubusercontent.com/118953932/209325061-31e59010-fde9-4c26-9be8-bb53f1496fe7.png" height = "250"></p>

**See timing**

```
dc_shell> remove_clock *
1
dc_shell> get_clocks *
Warning: Can't find clocks matching '*' in design 'lab8_circuit'. (UID-95)
dc_shell> report_timing
Information: Updating design information... (UID-85)
 
****************************************
Report : timing
        -path full
        -delay max
        -max_paths 1
Design : lab8_circuit
Version: P-2019.03-SP5-3
Date   : Fri Dec 23 19:00:22 2022
****************************************

Operating Conditions: tt_025C_1v80   Library: sky130_fd_sc_hd__tt_025C_1v80
Wire Load Model Mode: top

  Startpoint: REGC_reg (rising edge-triggered flip-flop)
  Endpoint: OUT_Y (output port)
  Path Group: (none)
  Path Type: max

  Point                                                   Incr       Path
  --------------------------------------------------------------------------
  REGC_reg/CLK (sky130_fd_sc_hd__dfrtp_1)                 0.00       0.00 r
  REGC_reg/Q (sky130_fd_sc_hd__dfrtp_1)                   0.34       0.34 f
  U10/Y (sky130_fd_sc_hd__clkinv_1)                       0.03       0.36 r
  OUT_Y (out)                                             0.00       0.36 r
  data arrival time                                                  0.36
  --------------------------------------------------------------------------
  (Path is unconstrained)


1

dc_shell> report_timing -to REGC_reg/D
 
****************************************
Report : timing
        -path full
        -delay max
        -max_paths 1
Design : lab8_circuit
Version: P-2019.03-SP5-3
Date   : Fri Dec 23 19:05:07 2022
****************************************

Operating Conditions: tt_025C_1v80   Library: sky130_fd_sc_hd__tt_025C_1v80
Wire Load Model Mode: top

  Startpoint: REGA_reg (rising edge-triggered flip-flop)
  Endpoint: REGC_reg (rising edge-triggered flip-flop)
  Path Group: (none)
  Path Type: max

  Point                                                   Incr       Path
  --------------------------------------------------------------------------
  REGA_reg/CLK (sky130_fd_sc_hd__dfrtp_1)                 0.00       0.00 r
  REGA_reg/Q (sky130_fd_sc_hd__dfrtp_1)                   0.33       0.33 f
  U14/Y (sky130_fd_sc_hd__nand2_1)                        0.05       0.38 r
  REGC_reg/D (sky130_fd_sc_hd__dfrtp_1)                   0.00       0.38 r
  data arrival time                                                  0.38
  --------------------------------------------------------------------------
  (Path is unconstrained)


1

#nothing to constraints
```


<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/209324811-b38d4ada-97fc-4fcb-8bfa-ad7910fd9990.png" height = "350"></p>
	
**Create clock again and report timing**
	
```
dc_shell> create_clock -name MYCLK -per 10 [get_ports clk]
1
dc_shell> report_timing -to REGC_reg/D
Information: Updating design information... (UID-85)
 
****************************************
Report : timing
        -path full
        -delay max
        -max_paths 1
Design : lab8_circuit
Version: P-2019.03-SP5-3
Date   : Fri Dec 23 19:06:46 2022
****************************************

Operating Conditions: tt_025C_1v80   Library: sky130_fd_sc_hd__tt_025C_1v80
Wire Load Model Mode: top

  Startpoint: REGA_reg (rising edge-triggered flip-flop clocked by MYCLK)
  Endpoint: REGC_reg (rising edge-triggered flip-flop clocked by MYCLK)
  Path Group: MYCLK
  Path Type: max

  Point                                                   Incr       Path
  --------------------------------------------------------------------------
  clock MYCLK (rise edge)                                 0.00       0.00
  clock network delay (ideal)                             0.00       0.00
  REGA_reg/CLK (sky130_fd_sc_hd__dfrtp_1)                 0.00       0.00 r
  REGA_reg/Q (sky130_fd_sc_hd__dfrtp_1)                   0.29       0.29 r
  U14/Y (sky130_fd_sc_hd__nand2_1)                        0.04       0.34 f
  REGC_reg/D (sky130_fd_sc_hd__dfrtp_1)                   0.00       0.34 f
  data arrival time                                                  0.34

  clock MYCLK (rise edge)                                10.00      10.00
  clock network delay (ideal)                             0.00      10.00
  REGC_reg/CLK (sky130_fd_sc_hd__dfrtp_1)                 0.00      10.00 r
  library setup time                                     -0.12       9.88
  data required time                                                 9.88
  --------------------------------------------------------------------------
  data required time                                                 9.88
  data arrival time                                                 -0.34
  --------------------------------------------------------------------------
  slack (MET)                                                        9.55 
```
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/209326727-fb3e8d48-091d-4060-8789-ccee736b563c.png" height = "350"><img src = "https://user-images.githubusercontent.com/118953932/209328285-2b79edcb-d059-4858-8329-118aaa2c1497.png" height = "200"></p>

**Model clock behaviour and Report Timing**

```
dc_shell> set_clock_latency -source 2 [get_clocks MYCLK]
1
dc_shell> set_clock_latency 1 [get_clocks MYCLK]
1
dc_shell> set_clock_uncertainty -setup  0.5 [get_clocks MYCLK]
1
dc_shell> set_clock_uncertainty -hold  0.1 [get_clocks MYCLK]
1
dc_shell> report_timing -to REGC_reg/D
Information: Updating design information... (UID-85)
 
****************************************
Report : timing
        -path full
        -delay max
        -max_paths 1
Design : lab8_circuit
Version: P-2019.03-SP5-3
Date   : Fri Dec 23 19:30:44 2022
****************************************

Operating Conditions: tt_025C_1v80   Library: sky130_fd_sc_hd__tt_025C_1v80
Wire Load Model Mode: top

  Startpoint: REGA_reg (rising edge-triggered flip-flop clocked by MYCLK)
  Endpoint: REGC_reg (rising edge-triggered flip-flop clocked by MYCLK)
  Path Group: MYCLK
  Path Type: max

  Point                                                   Incr       Path
  --------------------------------------------------------------------------
  clock MYCLK (rise edge)                                 0.00       0.00
  clock network delay (ideal)                             3.00       3.00
  REGA_reg/CLK (sky130_fd_sc_hd__dfrtp_1)                 0.00       3.00 r
  REGA_reg/Q (sky130_fd_sc_hd__dfrtp_1)                   0.29       3.29 r
  U14/Y (sky130_fd_sc_hd__nand2_1)                        0.04       3.34 f
  REGC_reg/D (sky130_fd_sc_hd__dfrtp_1)                   0.00       3.34 f
  data arrival time                                                  3.34

  clock MYCLK (rise edge)                                10.00      10.00
  clock network delay (ideal)                             3.00      13.00
  clock uncertainty                                      -0.50      12.50
  REGC_reg/CLK (sky130_fd_sc_hd__dfrtp_1)                 0.00      12.50 r
  library setup time                                     -0.12      12.38
  data required time                                                12.38
  --------------------------------------------------------------------------
  data required time                                                12.38
  data arrival time                                                 -3.34
  --------------------------------------------------------------------------
  slack (MET)                                                        9.05


1

```

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/209330040-e5bfa9ab-fa39-4151-a4a9-bf12e96ecdca.png" height = "350"></p>

Setup (left) & Hold (right):

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/209330524-ee51664f-7bea-4efc-bc30-8b40c18c3697.png" height = "200"><img src = "https://user-images.githubusercontent.com/118953932/209331204-5907ee59-7095-498b-8c24-664a68c381f2.png" height = "200"></p>

**For hold time**

```
dc_shell> report_timing -to REGC_reg/D -delay min
 
****************************************
Report : timing
        -path full
        -delay min
        -max_paths 1
Design : lab8_circuit
Version: P-2019.03-SP5-3
Date   : Fri Dec 23 19:50:17 2022
****************************************

Operating Conditions: tt_025C_1v80   Library: sky130_fd_sc_hd__tt_025C_1v80
Wire Load Model Mode: top

  Startpoint: REGB_reg (rising edge-triggered flip-flop clocked by MYCLK)
  Endpoint: REGC_reg (rising edge-triggered flip-flop clocked by MYCLK)
  Path Group: MYCLK
  Path Type: min

  Point                                                   Incr       Path
  --------------------------------------------------------------------------
  clock MYCLK (rise edge)                                 0.00       0.00
  clock network delay (ideal)                             3.00       3.00
  REGB_reg/CLK (sky130_fd_sc_hd__dfrtp_1)                 0.00       3.00 r
  REGB_reg/Q (sky130_fd_sc_hd__dfrtp_1)                   0.29       3.29 r
  U14/Y (sky130_fd_sc_hd__nand2_1)                        0.04       3.33 f
  REGC_reg/D (sky130_fd_sc_hd__dfrtp_1)                   0.00       3.33 f
  data arrival time                                                  3.33

  clock MYCLK (rise edge)                                 0.00       0.00
  clock network delay (ideal)                             3.00       3.00
  clock uncertainty                                       0.10       3.10
  REGC_reg/CLK (sky130_fd_sc_hd__dfrtp_1)                 0.00       3.10 r
  library hold time                                      -0.05       3.05
  data required time                                                 3.05
  --------------------------------------------------------------------------
  data required time                                                 3.05
  data arrival time                                                 -3.33
  --------------------------------------------------------------------------
  slack (MET)                                                        0.28


1

```

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/209331871-10229685-395d-45a6-9fa8-a9ab9bf1535c.png" height = "400"></p>

**Report about all the port**

```
dc_shell> report_port -verbose
 
****************************************
Report : port
        -verbose
Design : lab8_circuit
Version: P-2019.03-SP5-3
Date   : Fri Dec 23 19:53:43 2022
****************************************


                       Pin      Wire     Max     Max     Connection
Port           Dir     Load     Load     Trans   Cap     Class      Attrs
--------------------------------------------------------------------------------
IN_A           in      0.0000   0.0000   --      --      --         
IN_B           in      0.0000   0.0000   --      --      --         
clk            in      0.0000   0.0000   --      --      --         
rst            in      0.0000   0.0000   --      --      --         
OUT_Y          out     0.0000   0.0000   --      --      --         
out_clk        out     0.0000   0.0000   --      --      --         


              External  Max             Min                Min       Min
              Number    Wireload        Wireload           Pin       Wire
Port          Points    Model           Model              Load      Load
--------------------------------------------------------------------------------
IN_A               1      --              --              --        -- 
IN_B               1      --              --              --        -- 
clk                1      --              --              --        -- 
rst                1      --              --              --        -- 
OUT_Y              1      --              --              --        -- 
out_clk            1      --              --              --        -- 

                    Input Delay
                  Min             Max       Related   Max
Input Port    Rise    Fall    Rise    Fall   Clock  Fanout
--------------------------------------------------------------------------------
IN_A          --      --      --      --      --      -- 
IN_B          --      --      --      --      --      -- 
clk           --      --      --      --      --      -- 
rst           --      --      --      --      --      -- 




--------------------------------------------------------------------------------






               Max Tran        Min Tran
Input Port    Rise    Fall    Rise    Fall
--------------------------------------------------------------------------------
IN_A          --      --      --      -- 
IN_B          --      --      --      -- 
clk           --      --      --      -- 
rst           --      --      --      -- 


                    Output Delay
                  Min             Max      Related  Fanout
Output Port   Rise    Fall    Rise    Fall  Clock     Load
--------------------------------------------------------------------------------
OUT_Y         --      --      --      --      --      0.00
out_clk       --      --      --      --      --      0.00

1


#no IO delay, not modelled

dc_shell> report_timing -from IN_A
 
****************************************
Report : timing
        -path full
        -delay max
        -max_paths 1
Design : lab8_circuit
Version: P-2019.03-SP5-3
Date   : Fri Dec 23 19:54:47 2022
****************************************

Operating Conditions: tt_025C_1v80   Library: sky130_fd_sc_hd__tt_025C_1v80
Wire Load Model Mode: top

  Startpoint: IN_A (input port)
  Endpoint: REGA_reg (rising edge-triggered flip-flop clocked by MYCLK)
  Path Group: (none)
  Path Type: max

  Point                                                   Incr       Path
  --------------------------------------------------------------------------
  input external delay                                    0.00       0.00 f
  IN_A (in)                                               0.00       0.00 f
  U11/Y (sky130_fd_sc_hd__nor2_1)                         0.12       0.12 r
  U12/Y (sky130_fd_sc_hd__clkinv_1)                       0.07       0.18 f
  REGA_reg/D (sky130_fd_sc_hd__dfrtp_1)                   0.00       0.18 f
  data arrival time                                                  0.18
  --------------------------------------------------------------------------
  (Path is unconstrained)


1

```

### DC_D3SK2_L5 - Lab12- IO Delays

**Recap**

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/209341970-369eb4e9-cf5d-4106-a889-c66d354e235c.png" height = "250"></p>

**IO Constraints**

```
dc_shell> report_timing -from IN_A

dc_shell> report_timing

dc_shell> report_timing -to OUT_Y

```

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/209342624-21b5a163-62d6-433a-9f8b-43b36c6b3986.png" height = "450"></p>

**List all the ports**
```
dc_shell> report_port -verbose
 
****************************************
Report : port
        -verbose
Design : lab8_circuit
Version: P-2019.03-SP5-3
Date   : Fri Dec 23 21:20:28 2022
****************************************


                       Pin      Wire     Max     Max     Connection
Port           Dir     Load     Load     Trans   Cap     Class      Attrs
--------------------------------------------------------------------------------
IN_A           in      0.0000   0.0000   --      --      --         
IN_B           in      0.0000   0.0000   --      --      --         
clk            in      0.0000   0.0000   --      --      --         
rst            in      0.0000   0.0000   --      --      --         
OUT_Y          out     0.0000   0.0000   --      --      --         
out_clk        out     0.0000   0.0000   --      --      --         


              External  Max             Min                Min       Min
              Number    Wireload        Wireload           Pin       Wire
Port          Points    Model           Model              Load      Load
--------------------------------------------------------------------------------
IN_A               1      --              --              --        -- 
IN_B               1      --              --              --        -- 
clk                1      --              --              --        -- 
rst                1      --              --              --        -- 
OUT_Y              1      --              --              --        -- 
out_clk            1      --              --              --        -- 

                    Input Delay
                  Min             Max       Related   Max
Input Port    Rise    Fall    Rise    Fall   Clock  Fanout
--------------------------------------------------------------------------------
IN_A          --      --      --      --      --      -- 
IN_B          --      --      --      --      --      -- 
clk           --      --      --      --      --      -- 
rst           --      --      --      --      --      -- 



--------------------------------------------------------------------------------






               Max Tran        Min Tran
Input Port    Rise    Fall    Rise    Fall
--------------------------------------------------------------------------------
IN_A          --      --      --      -- 
IN_B          --      --      --      -- 
clk           --      --      --      -- 
rst           --      --      --      -- 


                    Output Delay
                  Min             Max      Related  Fanout
Output Port   Rise    Fall    Rise    Fall  Clock     Load
--------------------------------------------------------------------------------
OUT_Y         --      --      --      --      --      0.00
out_clk       --      --      --      --      --      0.00

1

#have not modelled anything yet
```

**Modelling**

-	input delay
```
dc_shell> set_input_delay -max 5 -clock [get_clocks MYCLK] [get_ports IN_A]
1
dc_shell> set_input_delay -max 5 -clock [get_clocks MYCLK] [get_ports IN_B]
1
dc_shell> report_port -verbose
Information: Updating design information... (UID-85)
 
****************************************
Report : port
        -verbose
Design : lab8_circuit
Version: P-2019.03-SP5-3
Date   : Fri Dec 23 21:23:31 2022
****************************************


                       Pin      Wire     Max     Max     Connection
Port           Dir     Load     Load     Trans   Cap     Class      Attrs
--------------------------------------------------------------------------------
IN_A           in      0.0000   0.0000   --      --      --         
IN_B           in      0.0000   0.0000   --      --      --         
clk            in      0.0000   0.0000   --      --      --         
rst            in      0.0000   0.0000   --      --      --         
OUT_Y          out     0.0000   0.0000   --      --      --         
out_clk        out     0.0000   0.0000   --      --      --         


              External  Max             Min                Min       Min
              Number    Wireload        Wireload           Pin       Wire
Port          Points    Model           Model              Load      Load
--------------------------------------------------------------------------------
IN_A               1      --              --              --        -- 
IN_B               1      --              --              --        -- 
clk                1      --              --              --        -- 
rst                1      --              --              --        -- 
OUT_Y              1      --              --              --        -- 
out_clk            1      --              --              --        -- 

                    Input Delay
                  Min             Max       Related   Max
Input Port    Rise    Fall    Rise    Fall   Clock  Fanout
--------------------------------------------------------------------------------
IN_A          --      --      5.00    5.00  MYCLK     --    
IN_B          --      --      5.00    5.00  MYCLK     --    
clk           --      --      --      --      --      -- 
rst           --      --      --      --      --      --

----------------------------------------------------------------------------



               Max Tran        Min Tran
Input Port    Rise    Fall    Rise    Fall
--------------------------------------------------------------------------------
IN_A          --      --      --      -- 
IN_B          --      --      --      -- 
clk           --      --      --      -- 
rst           --      --      --      -- 


                    Output Delay
                  Min             Max      Related  Fanout
Output Port   Rise    Fall    Rise    Fall  Clock     Load
--------------------------------------------------------------------------------
OUT_Y         --      --      --      --      --      0.00
out_clk       --      --      --      --      --      0.00

1
```
```
dc_shell> report_timing -from IN_A
 
****************************************
Report : timing
        -path full
        -delay max
        -max_paths 1
Design : lab8_circuit
Version: P-2019.03-SP5-3
Date   : Fri Dec 23 21:26:06 2022
****************************************

Operating Conditions: tt_025C_1v80   Library: sky130_fd_sc_hd__tt_025C_1v80
Wire Load Model Mode: top

  Startpoint: IN_A (input port clocked by MYCLK)
  Endpoint: REGA_reg (rising edge-triggered flip-flop clocked by MYCLK)
  Path Group: MYCLK
  Path Type: max

  Point                                                   Incr       Path
  --------------------------------------------------------------------------
  clock MYCLK (rise edge)                                 0.00       0.00
  clock network delay (ideal)                             3.00       3.00
  input external delay                                    5.00       8.00 f    #added
  IN_A (in)                                               0.00       8.00 f
  U11/Y (sky130_fd_sc_hd__nor2_1)                         0.12       8.12 r
  U12/Y (sky130_fd_sc_hd__clkinv_1)                       0.07       8.18 f
  REGA_reg/D (sky130_fd_sc_hd__dfrtp_1)                   0.00       8.18 f
  data arrival time                                                  8.18

  clock MYCLK (rise edge)                                10.00      10.00
  clock network delay (ideal)                             3.00      13.00
  clock uncertainty                                      -0.50      12.50
  REGA_reg/CLK (sky130_fd_sc_hd__dfrtp_1)                 0.00      12.50 r
  library setup time                                     -0.12      12.38
  data required time                                                12.38
  --------------------------------------------------------------------------
  data required time                                                12.38
  data arrival time                                                 -8.18
  --------------------------------------------------------------------------
  slack (MET)                                                        4.19


1


dc_shell> report_timing -from IN_A -trans -net -cap
 
****************************************
Report : timing
        -path full
        -delay max
        -nets
        -max_paths 1
        -transition_time
        -capacitance
Design : lab8_circuit
Version: P-2019.03-SP5-3
Date   : Fri Dec 23 21:28:25 2022
****************************************

Operating Conditions: tt_025C_1v80   Library: sky130_fd_sc_hd__tt_025C_1v80
Wire Load Model Mode: top

  Startpoint: IN_A (input port clocked by MYCLK)
  Endpoint: REGA_reg (rising edge-triggered flip-flop clocked by MYCLK)
  Path Group: MYCLK
  Path Type: max

  Point                                       Fanout       Cap     Trans      Incr       Path
  ----------------------------------------------------------------------------------------------
  clock MYCLK (rise edge)                                                     0.00       0.00
  clock network delay (ideal)                                                 3.00       3.00
  input external delay                                                        5.00       8.00 f
  IN_A (in)                                                         0.00      0.00       8.00 f
  IN_A (net)                                    2         0.00                0.00       8.00 f
  U11/Y (sky130_fd_sc_hd__nor2_1)                                   0.13      0.12       8.12 r
  n5 (net)                                      2         0.01                0.00       8.12 r
  U12/Y (sky130_fd_sc_hd__clkinv_1)                                 0.04      0.07       8.18 f
  N0 (net)                                      1         0.00                0.00       8.18 f
  REGA_reg/D (sky130_fd_sc_hd__dfrtp_1)                             0.04      0.00       8.18 f
  data arrival time                                                                      8.18

  clock MYCLK (rise edge)                                                    10.00      10.00
  clock network delay (ideal)                                                 3.00      13.00
  clock uncertainty                                                          -0.50      12.50
  REGA_reg/CLK (sky130_fd_sc_hd__dfrtp_1)                                     0.00      12.50 r
  library setup time                                                         -0.12      12.38
  data required time                                                                    12.38
  ----------------------------------------------------------------------------------------------
   data required time                                                                   12.38
   data arrival time                                                                    -8.18
  ----------------------------------------------------------------------------------------------
   slack (MET)                                                                           4.19

dc_shell> report_timing -from IN_A -trans -net -cap -nosplit > a
dc_shell> sh gvim a &
14222
```
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/209345582-beff267b-76de-4093-8c45-cc096a0b6380.png" height = "450"></p>

hold timing

```
dc_shell> report_timing -from IN_A -trans -net -cap -nosplit -delay_type min
 
****************************************
Report : timing
        -path full
        -delay min
        -nets
        -max_paths 1
        -transition_time
        -capacitance
Design : lab8_circuit
Version: P-2019.03-SP5-3
Date   : Fri Dec 23 21:45:49 2022
****************************************

Operating Conditions: tt_025C_1v80   Library: sky130_fd_sc_hd__tt_025C_1v80
Wire Load Model Mode: top

  Startpoint: IN_A (input port)
  Endpoint: REGB_reg (rising edge-triggered flip-flop clocked by MYCLK)
  Path Group: (none)
  Path Type: min

  Point                                       Fanout       Cap     Trans      Incr       Path
  ----------------------------------------------------------------------------------------------
  IN_A (in)                                                         0.00      0.00       0.00 r
  IN_A (net)                                    2         0.00                0.00       0.00 r
  U13/Y (sky130_fd_sc_hd__a21oi_1)                                  0.03      0.04       0.04 f
  N1 (net)                                      1         0.00                0.00       0.04 f
  REGB_reg/D (sky130_fd_sc_hd__dfrtp_1)                             0.03      0.00       0.04 f
  data arrival time                                                                      0.04
  ----------------------------------------------------------------------------------------------
  (Path is unconstrained)

#not modelled respected to any clock
```

**modelled hold time**

```
dc_shell> set_input_delay -min 1 -clock [get_clocks MYCLK] [get_ports IN_A]
1
dc_shell> set_input_delay -min 1 -clock [get_clocks MYCLK] [get_ports IN_B]
1
dc_shell> report_timing -from IN_A -trans -net -cap -nosplit -delay_type min
Information: Updating design information... (UID-85)
 
****************************************
Report : timing
        -path full
        -delay min
        -nets
        -max_paths 1
        -transition_time
        -capacitance
Design : lab8_circuit
Version: P-2019.03-SP5-3
Date   : Fri Dec 23 21:48:29 2022
****************************************

Operating Conditions: tt_025C_1v80   Library: sky130_fd_sc_hd__tt_025C_1v80
Wire Load Model Mode: top

  Startpoint: IN_A (input port clocked by MYCLK)
  Endpoint: REGB_reg (rising edge-triggered flip-flop clocked by MYCLK)
  Path Group: MYCLK
  Path Type: min

  Point                                       Fanout       Cap     Trans      Incr       Path
  ----------------------------------------------------------------------------------------------
  clock MYCLK (rise edge)                                                     0.00       0.00
  clock network delay (ideal)                                                 3.00       3.00
  input external delay                                                        1.00       4.00 r
  IN_A (in)                                                         0.00      0.00       4.00 r
  IN_A (net)                                    2         0.00                0.00       4.00 r
  U13/Y (sky130_fd_sc_hd__a21oi_1)                                  0.03      0.04       4.04 f
  N1 (net)                                      1         0.00                0.00       4.04 f
  REGB_reg/D (sky130_fd_sc_hd__dfrtp_1)                             0.03      0.00       4.04 f
  data arrival time                                                                      4.04
clock MYCLK (rise edge)                                                     0.00       0.00
  clock network delay (ideal)                                                 3.00       3.00
  clock uncertainty                                                           0.10       3.10
  REGB_reg/CLK (sky130_fd_sc_hd__dfrtp_1)                                     0.00       3.10 r
  library hold time                                                          -0.05       3.05
  data required time                                                                     3.05
  ----------------------------------------------------------------------------------------------
   data required time                                                                    3.05
   data arrival time                                                                    -4.04
  ----------------------------------------------------------------------------------------------
   slack (MET)                                                                           0.99

```

new max value

```
dc_shell> set_input_delay -max 5 -clock [get_clocks MYCLK] [get_ports IN_A]
1
dc_shell> report_timing -from IN_A -trans  -cap -nosplit > a
dc_shell> sh gvim a &
32224
```

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/209347318-80b4ca18-9349-48f8-bdef-3c122b5b0b56.png" height = "450"></p>

-	input transition

```
dc_shell> set_input_transition -max 0.3 [get_ports IN_A]
1
dc_shell> set_input_transition -max 0.3 [get_ports IN_B]
1
dc_shell> set_input_transition -min 0.1 [get_ports IN_B]
1
dc_shell> set_input_transition -min 0.1 [get_ports IN_A]
1
dc_shell> report_timing -from IN_A -trans  -cap -nosplit > a_trans
```

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/209348056-3cef9473-0b61-48be-aef1-a5b658a5cb3d.png" height = "450"></p>

-	output delay

```
dc_shell> set_output_delay -max 5 -clock [get_clocks MYCLK] [get_ports OUT_Y]
1
dc_shell> set_output_delay -min 1 -clock [get_clocks MYCLK] [get_ports OUT_Y]
1
dc_shell> report_timing -to OUT_Y
 
****************************************
Report : timing
        -path full
        -delay max
        -max_paths 1
Design : lab8_circuit
Version: P-2019.03-SP5-3
Date   : Fri Dec 23 22:10:39 2022
****************************************

Operating Conditions: tt_025C_1v80   Library: sky130_fd_sc_hd__tt_025C_1v80
Wire Load Model Mode: top

  Startpoint: REGC_reg (rising edge-triggered flip-flop clocked by MYCLK)
  Endpoint: OUT_Y (output port clocked by MYCLK)
  Path Group: MYCLK
  Path Type: max

  Point                                                   Incr       Path
  --------------------------------------------------------------------------
  clock MYCLK (rise edge)                                 0.00       0.00
  clock network delay (ideal)                             3.00       3.00
  REGC_reg/CLK (sky130_fd_sc_hd__dfrtp_1)                 0.00       3.00 r
  REGC_reg/Q (sky130_fd_sc_hd__dfrtp_1)                   0.34       3.34 f
  U10/Y (sky130_fd_sc_hd__clkinv_1)                       0.03       3.36 r
  OUT_Y (out)                                             0.00       3.36 r
  data arrival time                                                  3.36

  clock MYCLK (rise edge)                                10.00      10.00
  clock network delay (ideal)                             3.00      13.00
  clock uncertainty                                      -0.50      12.50
  output external delay                                  -5.00       7.50
  data required time                                                 7.50
  --------------------------------------------------------------------------
  data required time                                                 7.50
  data arrival time                                                 -3.36
  --------------------------------------------------------------------------
  slack (MET)                                                        4.14


1

dc_shell> report_timing -to OUT_Y -cap -trans
 
****************************************
Report : timing
        -path full
        -delay max
        -max_paths 1
        -transition_time
        -capacitance
Design : lab8_circuit
Version: P-2019.03-SP5-3
Date   : Fri Dec 23 22:12:05 2022
****************************************

Operating Conditions: tt_025C_1v80   Library: sky130_fd_sc_hd__tt_025C_1v80
Wire Load Model Mode: top

  Startpoint: REGC_reg (rising edge-triggered flip-flop clocked by MYCLK)
  Endpoint: OUT_Y (output port clocked by MYCLK)
  Path Group: MYCLK
  Path Type: max

  Point                                          Cap     Trans      Incr       Path
  ------------------------------------------------------------------------------------
  clock MYCLK (rise edge)                                           0.00       0.00
  clock network delay (ideal)                                       3.00       3.00
  REGC_reg/CLK (sky130_fd_sc_hd__dfrtp_1)                 0.00      0.00       3.00 r
  REGC_reg/Q (sky130_fd_sc_hd__dfrtp_1)         0.00      0.04      0.34       3.34 f
  U10/Y (sky130_fd_sc_hd__clkinv_1)             0.00      0.01      0.03       3.36 r
  OUT_Y (out)                                             0.01      0.00       3.36 r
  data arrival time                                                            3.36

  clock MYCLK (rise edge)                                          10.00      10.00
  clock network delay (ideal)                                       3.00      13.00
  clock uncertainty                                                -0.50      12.50
  output external delay                                            -5.00       7.50
  data required time                                                           7.50
  ------------------------------------------------------------------------------------
  data required time                                                           7.50
  data arrival time                                                           -3.36
  ------------------------------------------------------------------------------------
  slack (MET)                                                                  4.14
  
```

-	load

```
dc_shell> set_load -max 0.4 [get_ports OUT_Y]
1
dc_shell> report_timing -to OUT_Y -cap -trans
 
****************************************
Report : timing
        -path full
        -delay max
        -max_paths 1
        -transition_time
        -capacitance
Design : lab8_circuit
Version: P-2019.03-SP5-3
Date   : Fri Dec 23 22:14:49 2022
****************************************

Operating Conditions: tt_025C_1v80   Library: sky130_fd_sc_hd__tt_025C_1v80
Wire Load Model Mode: top

  Startpoint: REGC_reg (rising edge-triggered flip-flop clocked by MYCLK)
  Endpoint: OUT_Y (output port clocked by MYCLK)
  Path Group: MYCLK
  Path Type: max

  Point                                          Cap     Trans      Incr       Path
  ------------------------------------------------------------------------------------
  clock MYCLK (rise edge)                                           0.00       0.00
  clock network delay (ideal)                                       3.00       3.00
  REGC_reg/CLK (sky130_fd_sc_hd__dfrtp_1)                 0.00      0.00       3.00 r
  REGC_reg/Q (sky130_fd_sc_hd__dfrtp_1)         0.00      0.05      0.30       3.30 r
  U10/Y (sky130_fd_sc_hd__clkinv_1)             0.40      3.07      2.32       5.62 f
  OUT_Y (out)                                             3.07      0.00       5.62 f
  data arrival time                                                            5.62

  clock MYCLK (rise edge)                                          10.00      10.00
  clock network delay (ideal)                                       3.00      13.00
  clock uncertainty                                                -0.50      12.50
  output external delay                                            -5.00       7.50
  data required time                                                           7.50
  ------------------------------------------------------------------------------------
  data required time                                                           7.50
  data arrival time                                                           -5.62
  ------------------------------------------------------------------------------------
  slack (MET)                                                                  1.88

dc_shell> report_timing -to OUT_Y -cap -trans > out_load
dc_shell> sh gvim out_load &
36260

```

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/209350607-210c030b-c45b-45cc-b979-4400f8b5239e.png" height = "450"></p>

for min delay

```
dc_shell> report_timing -to OUT_Y -cap -trans -delay min
 
****************************************
Report : timing
        -path full
        -delay min
        -max_paths 1
        -transition_time
        -capacitance
Design : lab8_circuit
Version: P-2019.03-SP5-3
Date   : Fri Dec 23 22:20:46 2022
****************************************

Operating Conditions: tt_025C_1v80   Library: sky130_fd_sc_hd__tt_025C_1v80
Wire Load Model Mode: top

  Startpoint: REGC_reg (rising edge-triggered flip-flop clocked by MYCLK)
  Endpoint: OUT_Y (output port clocked by MYCLK)
  Path Group: MYCLK
  Path Type: min

  Point                                          Cap     Trans      Incr       Path
  ------------------------------------------------------------------------------------
  clock MYCLK (rise edge)                                           0.00       0.00
  clock network delay (ideal)                                       3.00       3.00
  REGC_reg/CLK (sky130_fd_sc_hd__dfrtp_1)                 0.00      0.00       3.00 r
  REGC_reg/Q (sky130_fd_sc_hd__dfrtp_1)         0.00      0.04      0.34       3.34 f
  U10/Y (sky130_fd_sc_hd__clkinv_1)             0.40      2.20      1.55       4.89 r
  OUT_Y (out)                                             2.20      0.00       4.89 r
  data arrival time                                                            4.89

  clock MYCLK (rise edge)                                           0.00       0.00
  clock network delay (ideal)                                       3.00       3.00
  clock uncertainty                                                 0.10       3.10
  output external delay                                            -1.00       2.10
  data required time                                                           2.10
  ------------------------------------------------------------------------------------
  data required time                                                           2.10
  data arrival time                                                           -4.89
  ------------------------------------------------------------------------------------
  slack (MET)                                                                  2.79
```

-	set other load for delay min

```
dc_shell> report_timing -to OUT_Y -cap -trans -delay min
 
****************************************
Report : timing
        -path full
        -delay min
        -max_paths 1
        -transition_time
        -capacitance
Design : lab8_circuit
Version: P-2019.03-SP5-3
Date   : Fri Dec 23 22:22:58 2022
****************************************

Operating Conditions: tt_025C_1v80   Library: sky130_fd_sc_hd__tt_025C_1v80
Wire Load Model Mode: top

  Startpoint: REGC_reg (rising edge-triggered flip-flop clocked by MYCLK)
  Endpoint: OUT_Y (output port clocked by MYCLK)
  Path Group: MYCLK
  Path Type: min

  Point                                          Cap     Trans      Incr       Path
  ------------------------------------------------------------------------------------
  clock MYCLK (rise edge)                                           0.00       0.00
  clock network delay (ideal)                                       3.00       3.00
  REGC_reg/CLK (sky130_fd_sc_hd__dfrtp_1)                 0.00      0.00       3.00 r
  REGC_reg/Q (sky130_fd_sc_hd__dfrtp_1)         0.00      0.04      0.34       3.34 f
  U10/Y (sky130_fd_sc_hd__clkinv_1)             0.10      0.56      0.41       3.75 r
  OUT_Y (out)                                             0.56      0.00       3.75 r
  data arrival time                                                            3.75

  clock MYCLK (rise edge)                                           0.00       0.00
  clock network delay (ideal)                                       3.00       3.00
  clock uncertainty                                                 0.10       3.10
  output external delay                                            -1.00       2.10
  data required time                                                           2.10
  ------------------------------------------------------------------------------------
  data required time                                                           2.10
  data arrival time                                                           -3.75
  ------------------------------------------------------------------------------------
  slack (MET)                                                                  1.65
```

### DC_D3SK3_L1 - Lecture9 - SDC Part3 generated_clk

**Interesting Note**

-	the Out_y is constrained with the clock leaving the module
-	logically it is the same as MY_CLK defined on port CLK
-	ist it physically same? NO. 

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/209415118-781a3a87-454d-4baf-b7ea-2177ca66f8d4.png" height = "250"><img src = "https://user-images.githubusercontent.com/118953932/209415157-9d965eb2-947b-4698-a38a-38f90fd1ba9e.png" height = "150"></p>

**Generated clock**
-	generated clocks are always created with respect to master clocks (clocks at clock source or primary IO pin)

```
create_generated_clock -name MY_GEN_CLK -master [get clocks MY_CLK] -source [get_ports CLK] -div 1 [get_ports OUT_CLK]
```
[get clocks MY_CLK] -source [get_ports CLK] = wrt to what the generated clock is created

-div =division value of generated clock (useful for clock dividers)

[get_ports OUT_CLK] = where the generated clock is created (generated definition point)

Out_Y need to be constrained with respect to the generated clock

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/209415684-176977de-079e-4210-b147-e66940e1785a.png" height = "350"></p>

**Constraining the design**
-	IN_DATA, IN_CLK has 2 functionalities
-	in one functionality the IN_DATA and IN_CLK gets the data and clock corresponding to A and in other functionality it gets data and clock corresponding to B
-	same for OUT_DATA, OUT_CLK (can get from A or from B)
-	how the clocks are propagated:
	-	once a clock is created on a pin/port, DC will propagate that clock downstream based on the timing arcs (all implementation tools)
	-	all the timing ars from the definition point will see the clock propagation by default
-	note:
	-	in the above design, while operating for "A", the clock and data from the input goes only towards A
	-	while operating for 'B', the clock and data from input goes only towards 'B'
	-	never to both places simultaneously! 

### DC_D3SK3_L2 - lab13 - generated_clocks

```
dc_shell> report_timing -to OUT_Y
```

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/209416240-d48af8f4-d26f-4323-a2c4-109a31ef6aa7.png" height = "500"></p>

**Create Generated Clock**

```
dc_shell> create_generated_clock -name MYGEN_CLK -master MYCLK -source [get_ports clk] -div 1 [get_ports out_clk]
1

dc_shell> report_clocks

dc_shell> get_attribute [get_clocks MYGEN_CLK] is_generated
true #generated clock

dc_shell> get_attribute [get_clocks MYCLK] is_generated
false #not generated clock (master clock)
```

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/209416493-8e57dc3f-d418-4a78-ab0a-d42f8a774e62.png" height = "300"></p>

**Model MYGEN_CLK**

```
dc_shell> set_clock_latency -max 1 [get_clocks MYGEN_CLK]
1

dc_shell> set_output_delay -max 5 [get_ports OUT_Y] -clock [get_clocks MYGEN_CLK]
1

dc_shell> set_output_delay -min 1 [get_ports OUT_Y] -clock [get_clocks MYGEN_CLK]
1

dc_shell> report_timing -to OUT_Y

```

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/209428165-4fac518e-f404-46e6-aa6c-061a4471453b.png" height = "400"></p>

**Modify lab8_circuit.v**

```
dc_shell> sh gvim lab8_circuit.v

(inside gvim)
:sp lab8_circuit_modified.v
```

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/209428279-5e5f7c23-5ff0-486b-b23a-b1451846cba6.png" height = "400"></p>

**Reset design**

```
dc_shell> reset_design
re1

dc_shell> read_verilog lab8_circuit_modified.v
Loading verilog file '/nfs/png/disks/png_mip_gen6p9ddr_0032/nurul/VLSI/sky130RTLDesignAndSynthesisWorkshop/DC_WORKSHOP/verilog_files/lab8_circuit_modified.v'
Detecting input file type automatically (-rtl or -netlist).
Warning: Overwriting design file '/nfs/png/disks/png_mip_gen6p9ddr_0032/nurul/VLSI/sky130RTLDesignAndSynthesisWorkshop/DC_WORKSHOP/verilog_files/lab8_circuit'. (DDB-24)
Reading with Presto HDL Compiler (equivalent to -rtl option).
Running PRESTO HDLC
Compiling source file /nfs/png/disks/png_mip_gen6p9ddr_0032/nurul/VLSI/sky130RTLDesignAndSynthesisWorkshop/DC_WORKSHOP/verilog_files/lab8_circuit_modified.v

Inferred memory devices in process
        in routine lab8_circuit line 5 in file
                '/nfs/png/disks/png_mip_gen6p9ddr_0032/nurul/VLSI/sky130RTLDesignAndSynthesisWorkshop/DC_WORKSHOP/verilog_files/lab8_circuit_modified.v'.
===============================================================================
|    Register Name    |   Type    | Width | Bus | MB | AR | AS | SR | SS | ST |
===============================================================================
|      REGC_reg       | Flip-flop |   1   |  N  | N  | Y  | N  | N  | N  | N  |
|   out_div_clk_reg   | Flip-flop |   1   |  N  | N  | Y  | N  | N  | N  | N  |
|      REGB_reg       | Flip-flop |   1   |  N  | N  | Y  | N  | N  | N  | N  |
|      REGA_reg       | Flip-flop |   1   |  N  | N  | Y  | N  | N  | N  | N  |
===============================================================================
Presto compilation completed successfully.
Current design is now '/nfs/png/disks/png_mip_gen6p9ddr_0032/nurul/VLSI/sky130RTLDesignAndSynthesisWorkshop/DC_WORKSHOP/verilog_files/lab8_circuit.db:lab8_circuit'
Loaded 1 design.
Current design is 'lab8_circuit'.
lab8_circuit

dc_shell> sh gvim lab8_cons.tcl &
21889
```

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/209428365-c12800ba-8f19-4900-b50f-29d24dd8368d.png" height = "400"></p>

need to set all of it again

**Source lab8_cons.tcl**

```
dc_shell> link

  Linking design 'lab8_circuit'
  Using the following designs and libraries:
  --------------------------------------------------------------------------
  lab8_circuit                /nfs/png/disks/png_mip_gen6p9ddr_0032/nurul/VLSI/sky130RTLDesignAndSynthesisWorkshop/DC_WORKSHOP/verilog_files/lab8_circuit.db
  sky130_fd_sc_hd__tt_025C_1v80 (library)
                              /nfs/png/disks/png_mip_gen6p9ddr_0032/nurul/VLSI/sky130RTLDesignAndSynthesisWorkshop/DC_WORKSHOP/lib/sky130_fd_sc_hd__tt_025C_1v80.db

1

dc_shell> source lab8_cons.tcl
1

dc_shell> report_clocks
Information: Updating graph... (UID-83)
 
****************************************
Report : clocks
Design : lab8_circuit
Version: P-2019.03-SP5-3
Date   : Sat Dec 24 17:02:15 2022
****************************************

Attributes:
    d - dont_touch_network
    f - fix_hold
    p - propagated_clock
    G - generated_clock
    g - lib_generated_clock

Clock          Period   Waveform            Attrs     Sources
--------------------------------------------------------------------------------
MYCLK           10.00   {0 5}                         {clk}
MYGEN_CLK       10.00   {0 5}               G         {out_clk}
MYGEN_DIV_CLK   20.00   {0 10}              G         {out_div_clk}
--------------------------------------------------------------------------------

Generated     Master         Generated      Master         Waveform
Clock         Source         Source         Clock          Modification
--------------------------------------------------------------------------------
MYGEN_CLK     clk            {out_clk}      MYCLK          divide_by(1)
MYGEN_DIV_CLK clk            {out_div_clk}  MYCLK          divide_by(2)
--------------------------------------------------------------------------------
1

dc_shell> get_generated_clocks
{MYGEN_CLK MYGEN_DIV_CLK}
```

**Report ports**

```
dc_shell> report_port -verbose
Information: Updating design information... (UID-85)
 
****************************************
Report : port
        -verbose
Design : lab8_circuit
Version: P-2019.03-SP5-3
Date   : Sat Dec 24 17:03:37 2022
****************************************



Attributes:
    c - port_is_clock_port

```

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/209428897-62169af5-9032-4410-962b-e35513f0784b.png" height = "500"></p>

**DESIGN COMPLETELY CONSTRAINED!!**

### DC_D3SK4_L1 - Lecture10 - SDC Part4 vclk, max_latency, rise_fall IODelays

**Input Delay**

-	max
```
create_clock -name MYCLK -per 10 [get_ports clk]
set_input_delay -max 3 -clock myclk [get_ports IN_A]
set_input_delay -max -3 -clock myclk [get_ports IN_A] #good
```
[clock period - uncertainty -i/p delay] = available time

Note: -ve delay for max is relaxing, +ve delay for max is tightening

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/209436711-b55b8518-31a7-4076-b8ad-c838b75fbacc.png" height = "200"><img src = "https://user-images.githubusercontent.com/118953932/209437462-16bc9729-1c9b-469e-8288-df436c611462.png" height = "200"></p>

-	min 

```
set_input_delay -min 1 -clock myclk [get_ports IN_A]
set_input_delay -min -1 -clock myclk [get_ports IN_A] #need to add delay to met hold time
```

positive delay = data comes after clk edge (ease in meeting hold time)

negative delay = data come before clk edge (clock relatively get push out wrt data)


Note: +ve delay for max is relaxing, -ve delay for max is tightening

**Output Delay**

-	max
```
create_clock -name MYCLK -per 10 [get_ports clk]
set_output_delay -max 3 -clock myclk [get_ports IN_A]  #7ns available
set_output_delay -max -3 -clock myclk [get_ports IN_A]  #13ns available
```

[clock period - external delay] = available time

-	min 

```
set_output_delay -min 1 -clock myclk [get_ports IN_A]
set_output_delay -min -1 -clock myclk [get_ports IN_A] #clock get pushed out
```

**IO Constraints**

-	to constraint the IN_C and IN_D (purely combo) path
```
set_max_latency 1.0 -from [get_ports IN_C] -to [get_ports OUT_Z] #allowed max latency =1.0
set_max_latency 1.0 -from [get_ports IN_D] -to [get_ports OUT_Z]
```

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/209438114-c907114e-db09-4f23-91b0-bf2c2aca2931.png" height = "250"></p>

-	overcome by using virtual clock

```
create_clock -name MY_VCLK -period 5 #no clock definition point (automatically inferred as virtual clock)
```

-	create the input and output delay for virtual clock

```
set_output_delay -max 2.5 -clock MY_VCLK [get_ports OUT_Z]
set_input_delay -max 1.5 -clock MY_VCLK [get_ports IN_C]
set_input_delay -max 1.5 -clock MY_VCLK [get_ports IN_D]
```

Note: for virtual clock there is no latency, no clock definition point 

input 

```
set_input_delay -max 2 -clock CLK [get_ports IN_A] #clock name CLK (outside module)

set_input_delay -max 3 -clock CLK -clock_fall -add [get_ports IN_A] #wrt the falling edge of the clock
```

-clock_fall = to specify the annotated delay is wrt to neg edge

-add = to specify that append this constraint to the already existing constraint

output

```
set_output_delay -max 2 -clock CLK [get_ports Out_Y] #clock name CLK 
set_output_delay -max 3 -clock CLK -clock_fall -add [get_ports Out_Y]
```

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/209438503-731ccca1-abd9-4a20-ac50-f74e2cd46a71.png" height = "250"><img src = "https://user-images.githubusercontent.com/118953932/209438585-04c260d7-27b4-4050-84a7-65222911a334.png" height = "250"></p>

**set_driving_cell**

```
set_input_transition -max 0.15 [get_ports IN_A] #fixed transition (mainly recommended for top level primary IOs
```

set_driving_cell more accurate and recommended for all internal parts

```
set_driving_cell -lib <lib_cell_name> <ports> #recomended to module level IOs (module to module)

eg:
set_driving_cell -lib sky130_fd_sc_hd__buf_1 [all_inputs]
```

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/209438869-70adeed6-4e25-470b-aef9-4cd1a9f3ff9e.png" height = "300"></p>

### DC_D3SK4_L2 - lab15 - part1 Set_Max_delay

**Previous design**


<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/209461755-c6bfff44-32f8-4a81-8011-9e49e641f438.png" height = "250"></p>

**lab14_circuit.v**

```
dc_shell> reset_design
1
dc_shell> sh gvim lab14_circuit.v
```

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/209462233-2c3fcd24-8947-44bf-93c8-4937aab807d3.png" height = "500"></p>

```
dc_shell> read_verilog lab14_circuit.v
Loading verilog file '/nfs/png/disks/png_mip_gen6p9ddr_0032/nurul/VLSI/sky130RTLDesignAndSynthesisWorkshop/DC_WORKSHOP/verilog_files/lab14_circuit.v'
Detecting input file type automatically (-rtl or -netlist).
Warning: Overwriting design file '/nfs/png/disks/png_mip_gen6p9ddr_0032/nurul/VLSI/sky130RTLDesignAndSynthesisWorkshop/DC_WORKSHOP/verilog_files/lab8_circuit'. (DDB-24)
Reading with Presto HDL Compiler (equivalent to -rtl option).
Running PRESTO HDLC
Compiling source file /nfs/png/disks/png_mip_gen6p9ddr_0032/nurul/VLSI/sky130RTLDesignAndSynthesisWorkshop/DC_WORKSHOP/verilog_files/lab14_circuit.v

Inferred memory devices in process
        in routine lab8_circuit line 6 in file
                '/nfs/png/disks/png_mip_gen6p9ddr_0032/nurul/VLSI/sky130RTLDesignAndSynthesisWorkshop/DC_WORKSHOP/verilog_files/lab14_circuit.v'.
===============================================================================
|    Register Name    |   Type    | Width | Bus | MB | AR | AS | SR | SS | ST |
===============================================================================
|      REGC_reg       | Flip-flop |   1   |  N  | N  | Y  | N  | N  | N  | N  |
|   out_div_clk_reg   | Flip-flop |   1   |  N  | N  | Y  | N  | N  | N  | N  |
|      REGB_reg       | Flip-flop |   1   |  N  | N  | Y  | N  | N  | N  | N  |
|      REGA_reg       | Flip-flop |   1   |  N  | N  | Y  | N  | N  | N  | N  |
===============================================================================
Presto compilation completed successfully.
Current design is now '/nfs/png/disks/png_mip_gen6p9ddr_0032/nurul/VLSI/sky130RTLDesignAndSynthesisWorkshop/DC_WORKSHOP/verilog_files/lab8_circuit.db:lab8_circuit'
Loaded 1 design.
Current design is 'lab8_circuit'.
lab8_circuit
```

```
dc_shell> source lab8_cons.tcl
1
dc_shell> report_clock
Information: Updating graph... (UID-83)
 
****************************************
Report : clocks
Design : lab8_circuit
Version: P-2019.03-SP5-3
Date   : Sun Dec 25 17:07:52 2022
****************************************

Attributes:
    d - dont_touch_network
    f - fix_hold
    p - propagated_clock
    G - generated_clock
    g - lib_generated_clock

Clock          Period   Waveform            Attrs     Sources
--------------------------------------------------------------------------------
MYCLK           10.00   {0 5}                         {clk}
MYGEN_CLK       10.00   {0 5}               G         {out_clk}
MYGEN_DIV_CLK   20.00   {0 10}              G         {out_div_clk}
--------------------------------------------------------------------------------

Generated     Master         Generated      Master         Waveform
Clock         Source         Source         Clock          Modification
--------------------------------------------------------------------------------
MYGEN_CLK     clk            {out_clk}      MYCLK          divide_by(1)
MYGEN_DIV_CLK clk            {out_div_clk}  MYCLK          divide_by(2)
--------------------------------------------------------------------------------
1
```

**Report timing (in terms of gtech cells)**

```
dc_shell> report_timing
```

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/209463443-8c209a58-89a0-42b7-a372-d7abf2acc316.png" height = "500"></p>

**Link the design**

```
dc_shell> link
dc_shell> compile_ultra
```

**Report timing**

```
dc_shell> report_timing
```

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/209463679-bb2e2b0d-b93b-45e2-8f34-0ca689259b5d.png" height = "500"></p>

**Check path constraint or not**

```
dc_shell> get_ports *
{rst clk IN_A IN_B OUT_Y out_clk out_div_clk IN_C IN_D OUT_Z}

dc_shell> report_timing -to OUT_Z

dc_shell> report_timing -from IN_C
```

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/209464206-86ab4c56-c0fe-4ad3-a98b-becfe896ddd3.png" height = "500"></p>

**Helpful commands**

```
all_inputs #listing all inputs

all_outputs #listing all outputs

all_clocks #listing all clocks

all_registers #listing all registers

all_registers -clock MYCLK #registers clocked by MYCLK

all_fanout -from IN_A #listing all the fanout of IN_A
{REGA_reg/D U12/Y REGB_reg/D U16/B1 U12/A U16/Y U15/Y U16/A2 U15/A IN_A}

dc_shell> all_fanout -flat -endpoints_only -from IN_A
{REGA_reg/D REGB_reg/D}

dc_shell> all_fanin -to REGA_reg/D
{IN_B IN_A U15/B U15/A U15/Y U12/A U12/Y REGA_reg/D}

dc_shell> all_fanin -flat -startpoints_only -to REGA_reg/D
{IN_B IN_A}
```
Note: ENDPOINTS of a timing path = D pin or out pin

**Constraining path to Z**

no path to OUT_Z yet

```
dc_shell> set_max_delay 0.1 -from [all_inputs] -to [get_port OUT_Z]
1
dc_shell> report_timing -to OUT_Z -sig 4
```

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/209465183-6fc0c9cf-96d9-4e51-a1dc-bcb5585363e1.png" height = "500"></p>

Note: path not constraint properly, DC to do not optimized to meet the path

**Optimized the delay**

```
dc_shell> compile_ultra
dc_shell> report_timing -to OUT_Z -sig 4
```

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/209465417-6bfea1cf-6404-496f-9553-cc768e5bd529.png" height = "500"></p>

**Design Vision**

```
dc_shell> write -f ddc -out lab14.ddc
Writing ddc file 'lab14.ddc'.
1

design_vision> reset_design
1

design_vision> read_ddc lab14.ddc
Reading ddc file '/nfs/png/disks/png_mip_gen6p9ddr_0032/nurul/VLSI/sky130RTLDesignAndSynthesisWorkshop/DC_WORKSHOP/verilog_files/lab14.ddc'.
Loaded 1 design.
Current design is 'lab8_circuit'.
lab8_circuit

design_vision> start_gui

design_vision> Current design is 'lab8_circuit'.
Current design is 'lab8_circuit'.
```

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/209465714-2fa1eeb3-8b84-4387-b5f8-bf8c36252876.png" height = "500"></p>

### DC_D3SK4_L3 - Lab15 - part2 - VCLK

**Using virtual clock**
-	first method used set_max_delay
-	second use virtual clock 
	-	a clock that is created without a definition point

```
dc_shell> reset_design

dc_shell> read_verilog lab14_circuit.v

dc_shell> link

dc_shell> source lab8_cons.tcl

dc_shell> compile_ultra

dc_shell> report_clocks
Information: Updating graph... (UID-83)
 
****************************************
Report : clocks
Design : lab8_circuit
Version: P-2019.03-SP5-3
Date   : Sun Dec 25 19:19:14 2022
****************************************

Attributes:
    d - dont_touch_network
    f - fix_hold
    p - propagated_clock
    G - generated_clock
    g - lib_generated_clock

Clock          Period   Waveform            Attrs     Sources
--------------------------------------------------------------------------------
MYCLK           10.00   {0 5}                         {clk}
MYGEN_CLK       10.00   {0 5}               G         {out_clk}
MYGEN_DIV_CLK   20.00   {0 10}              G         {out_div_clk}
--------------------------------------------------------------------------------

Generated     Master         Generated      Master         Waveform
Clock         Source         Source         Clock          Modification
--------------------------------------------------------------------------------
MYGEN_CLK     clk            {out_clk}      MYCLK          divide_by(1)
MYGEN_DIV_CLK clk            {out_div_clk}  MYCLK          divide_by(2)
--------------------------------------------------------------------------------
1

dc_shell> report_timing -to OUT_Z
```

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/209466046-ebc7673c-8cf7-4455-8233-7cc688f547ce.png" height = "500"></p>

```
dc_shell> create_clock -name MYVCLK -per 10
Warning: Creating virtual clock named 'MYVCLK' with no sources. (UID-348)
1

dc_shell> report_clocks
```

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/209466298-28a22219-fad1-4164-b46e-646eec1a0387.png" height = "500"></p>

**Annotate IO Delays**

```
dc_shell> set_input_delay -max 5 [get_ports IN_C] -clock [get_clocks MYVCLK]
1

dc_shell> set_input_delay -max 5 [get_ports IN_D] -clock [get_clocks MYVCLK]
1

dc_shell> set_output_delay -max 4.9 [get_ports OUT_Z] -clock [get_clocks MYVCLK]
1

#5ns input and 4.9ns in the output so only 100ps is left

dc_shell> report_timing

Information: Updating design information... (UID-85)
 
****************************************
Report : timing
        -path full
        -delay max
        -max_paths 1
Design : lab8_circuit
Version: P-2019.03-SP5-3
Date   : Sun Dec 25 19:35:29 2022
****************************************

Operating Conditions: tt_025C_1v80   Library: sky130_fd_sc_hd__tt_025C_1v80
Wire Load Model Mode: top

  Startpoint: IN_A (input port clocked by MYCLK)
  Endpoint: REGA_reg (rising edge-triggered flip-flop clocked by MYCLK)
  Path Group: MYCLK
  Path Type: max

  Point                                                   Incr       Path
  --------------------------------------------------------------------------
  clock MYCLK (rise edge)                                 0.00       0.00
  clock network delay (ideal)                             3.00       3.00
  input external delay                                    5.00       8.00 f
  IN_A (in)                                               0.00       8.00 f
  U15/Y (sky130_fd_sc_hd__nor2_1)                         0.25       8.25 r
  U12/Y (sky130_fd_sc_hd__clkinv_1)                       0.08       8.32 f
  REGA_reg/D (sky130_fd_sc_hd__dfrtp_1)                   0.00       8.32 f
  data arrival time                                                  8.32

  clock MYCLK (rise edge)                                10.00      10.00
  clock network delay (ideal)                             3.00      13.00
  clock uncertainty                                      -0.50      12.50
  REGA_reg/CLK (sky130_fd_sc_hd__dfrtp_1)                 0.00      12.50 r
  library setup time                                     -0.13      12.37
  data required time                                                12.37
  --------------------------------------------------------------------------
  data required time                                                12.37
  data arrival time                                                 -8.32
  --------------------------------------------------------------------------
  slack (MET)                                                        4.05


  Startpoint: REGC_reg (rising edge-triggered flip-flop clocked by MYCLK)
  Endpoint: OUT_Y (output port clocked by MYGEN_CLK)
  Path Group: MYGEN_CLK
  Path Type: max

  Point                                                   Incr       Path
  --------------------------------------------------------------------------
  clock MYCLK (rise edge)                                 0.00       0.00
  clock network delay (ideal)                             3.00       3.00
  REGC_reg/CLK (sky130_fd_sc_hd__dfrtp_1)                 0.00       3.00 r
  REGC_reg/Q (sky130_fd_sc_hd__dfrtp_1)                   0.37       3.37 f
  U13/Y (sky130_fd_sc_hd__inv_4)                          0.77       4.14 r
  OUT_Y (out)                                             0.00       4.14 r
  data arrival time                                                  4.14

  clock MYGEN_CLK (rise edge)                            10.00      10.00
  clock network delay (ideal)                             0.00      10.00
  output external delay                                  -5.00       5.00
  data required time                                                 5.00
  --------------------------------------------------------------------------
  data required time                                                 5.00
  data arrival time                                                 -4.14
  --------------------------------------------------------------------------
  slack (MET)                                                        0.86

```

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/209466453-af4e1945-a6b4-40b8-a7db-848407b4918a.png" height = "300"></p>

**Optimized**

```
dc_shell> compile_ultra

dc_shell> report_timing -to OUT_Z -sig 4
```

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/209466549-b53b36e3-1def-4319-969c-8bae80ebfb62.png" height = "450"></p>

Note: same optimization has done as previous strategy

```
dc_shell> report_port -verbose
```

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/209466606-2f024978-ccca-4828-bcee-01b00e21a5ae.png" height = "450"></p>

# Day-9 
## DC_D4SK1_L1 - Lecture11 - Optimizations Combinational Opt

**Optimization Goal** ✨
-	cost function based optimization
	-	optimization till the cost is met
	-	over optimization of one goal will harm other goals
	-	goals for synthesis
		-	meet timing (put faster cells ✔️ but power will go bad ✖️ , area will be wider ✖️)
			-	cost funtion IO Delay, clock period, max delay
		-	meet area (put smaller cells ✔️, power is good ✔️ but timing is bad ✖️)
		-	meet power 

**Combinational Logic Optimization**
-	squeezing the logic to get the most optimised design
	-	area and power savings
-	constant propagation
	-	direct optimization
-	boolean logic optitmization
	-	k-map
	-	Quine McKluskey

**Example: Constant Propagation** 🤔


<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/209769473-65337b0c-da8a-4e89-84e3-d200e30d400f.png" height = "300"></p>

**Example: Boolean Logic Optimization** 🤔

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/209771681-8d7ee661-d919-46a1-a892-bc2db708c656.png" height = "300"></p>

>	can have single xnor gate instead of 3 mux

**Example: Resource Sharing** 🤔


<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/209772543-340071cb-e382-4f39-8705-3af0157e080a.png" height = "350"></p>

**Example: Logic Sharing** 🤔

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/209773215-b5d6c7ce-5a00-4fb3-a13b-19b095e78a25.png" height = "350"></p>

**Example: Balanced vs Preferential Implementation** 🤔

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/209775820-a54c0fb3-f2bf-49cc-b3f8-747c8f1cba06.png" height = "350"></p>

>	Tool will pick based on constraints to get the best optimize design

## DC_D4SK1_L2 - Lecture12 Sequential Optimizations 

**Sequential Logic optimizations**
-	Basic
	-	sequential constant propagation
	-	retiming
	-	unused flop removal
	-	clock gating
-	Advanced
	-	state optimization
	-	sequential logic cloning (floorplan aware synthesis)

**Example: Constant Propagation** 🤔

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/209778746-2537dcfa-ddd3-4e3f-8da2-46d2fae9b435.png" height = "300"></p>

>	optimized

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/209779007-9e0780c3-54f5-46c9-b746-331c7338f401.png" height = "300"><img src = "https://user-images.githubusercontent.com/118953932/209779592-861d4b44-7015-42bf-b683-aed1354d76ce.png" height = "300"></p>

>	not optimized


<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/209780518-5159d294-e2cf-426c-8655-410c2af72391.png" height = "400"></p>

>	set and D = 1 is sequential constant \
>	optimized 

**Example: Optimization of unloaded outputs** 🤔

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/209783125-e7d52e3b-4086-4386-bb2e-c2755f58aea2.png" height = "300"></p>

>	optimized

**Controlling Sequential Optimizations in DC** 🤔

Commands used (Boolean variables so can set true or false)

```
compile_seqmap_propagate_constants 
#set to true = will propagate sequential constant. circuit will remain the same. need not have to bring the logic back (it will retained)


compile_delete_unloaded_sequential_cells 
#set to false = will not remove the cells


compile_register_replication 
#floorplan aware synthesis (optimum routing delay or cloning registers)
```

>	can prevent the optimization happening so that all the flops and logics are preserved (incase we want to use it later)

## DC_D4SK2_L1 - Lab16 - part1 Combinational_optimizations

```
dc_shell> sh gvim opt_check*.v -o
```

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/209790298-b36713ad-060c-4444-af87-21d54ae77e3e.png" height = "500"></p>

**opt_check.v**

Expected output:

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/209790166-26192087-5bff-44f3-87b9-dc3027bbb3e0.png" height = "350"></p>

```
dc_shell> read_verilog opt_check.v
```

>	Loading verilog file '/nfs/png/disks/png_mip_gen6p9ddr_0032/nurul/VLSI/sky130RTLDesignAndSynthesisWorkshop/DC_WORKSHOP/verilog_files/opt_check.v'\
Detecting input file type automatically (-rtl or -netlist).\
Reading with Presto HDL Compiler (equivalent to -rtl option).\
Running PRESTO HDLC\
Compiling source file /nfs/png/disks/png_mip_gen6p9ddr_0032/nurul/VLSI/sky130RTLDesignAndSynthesisWorkshop/DC_WORKSHOP/verilog_files/opt_check.v\
Presto compilation completed successfully.\
Current design is now '/nfs/png/disks/png_mip_gen6p9ddr_0032/nurul/VLSI/sky130RTLDesignAndSynthesisWorkshop/DC_WORKSHOP/verilog_files/opt_check.db:opt_check'\
Loaded 1 design.\
Current design is 'opt_check'.\
opt_check\


```
dc_shell> report_timing
```

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/209791150-4e3c4fae-b700-42a0-8769-b7223f0dd2e4.png" height = "300"></p>

```
dc_shell> link

dc_shell> compile

dc_shell> report_timing
```

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/209791488-6ab903e7-7259-4a1f-a7fb-1dd5995969b4.png" height = "300"></p>

```
dc_shell> get_cells *
{U4 U5} 
#only 2 cells in the design
```

```
dc_shell> report_timing -to y2
```

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/209791774-baf88f5e-6047-49a4-adbe-29158a0b4fcd.png" height = "300"></p>

```
dc_shell> report_timing -to y1
```


<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/209792168-a0271eca-628c-4c3f-9d0a-381dba18ba1f.png" height = "300"></p>

```
dc_shell> write -f ddc -out opt_check.ddc
Writing ddc file 'opt_check.ddc'.
1
```

```
#launch design vision

csh

design_vision

design_vision> read_ddc opt_check.ddc
```

As Expected:

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/209792645-f676315b-2e70-4e3a-9b86-a6b896982af0.png" height = "450"></p>

```
design_vision> reset_deisgn

dc_shell> reset_design

```

**Load other files**

Expected output:

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/209793774-ceb1e01b-2f0a-47d6-97bb-3dbbe66d78c4.png" height = "250"><img src = "https://user-images.githubusercontent.com/118953932/209794428-5c684faa-a99a-4a7d-ac22-514b7e67eb74.png" height = "250"><img src = "https://user-images.githubusercontent.com/118953932/209794938-4fb0ac0d-1b9e-4e15-a3b8-f3574b3a7401.png" height = "300"></p>

**opt_check2.v**

```
dc_shell> read_verilog opt_check2.v

dc_shell> link

dc_shell> compile

dc_shell> write -f ddc -out opt_check2.ddc

design_vision> read_ddc opt_check2.ddc
```

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/209796100-c0b708e3-722b-4d49-a37e-4b380c091f57.png" height = "450"></p>

**opt_check3.v**

```
dc_shell> read_verilog opt_check3.v

dc_shell> link

dc_shell> compile

dc_shell> write -f ddc -out opt_check3.ddc

design_vision> read_ddc opt_check3.ddc
```

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/209796380-9bc0dcd3-3bcc-450f-b8b9-ee0ae4eb0eca.png" height = "450"></p>

**opt_check4.v**

```
dc_shell> read_verilog opt_check4.v

dc_shell> link

dc_shell> compile

dc_shell> write -f ddc -out opt_check4.ddc

design_vision> read_ddc opt_check4.ddc
```

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/209796693-4eb0adbb-6008-45a3-9ec1-c7cc12096564.png" height = "450"></p>

>	b is unused

```
dc_shell> report_timing
```


<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/209797093-158ea240-8f58-4d82-85a7-1a23c5ad15ab.png" height = "300"></p>

```
dc_shell> set_max_delay 0.06 -from [all_inputs] -to [get_ports y]
1

dc_shell> report_timing -to y -sig 4
Information: Updating design information... (UID-85)
 
****************************************
Report : timing
        -path full
        -delay max
        -max_paths 1
Design : opt_check4
Version: P-2019.03-SP5-3
Date   : Wed Dec 28 18:23:11 2022
****************************************

Operating Conditions: tt_025C_1v80   Library: sky130_fd_sc_hd__tt_025C_1v80
Wire Load Model Mode: top

  Startpoint: a (input port)
  Endpoint: y (output port)
  Path Group: default
  Path Type: max

  Point                                    Incr       Path
  -----------------------------------------------------------
  input external delay                   0.0000     0.0000 f
  a (in)                                 0.0000     0.0000 f
  U2/Y (sky130_fd_sc_hd__xnor2_1)        0.0830     0.0830 f
  y (out)                                0.0000     0.0830 f
  data arrival time                                 0.0830

  max_delay                              0.0600     0.0600
  output external delay                  0.0000     0.0600
  data required time                                0.0600
  -----------------------------------------------------------
  data required time                                0.0600
  data arrival time                                -0.0830
  -----------------------------------------------------------
  slack (VIOLATED)                                 -0.0230


1

dc_shell> compile_ultra

dc_shell> report_timing
```

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/209798137-e33c3fd0-f474-4826-90f3-f8eb30a43613.png" height = "350"></p>

```
#Upsize cell

dc_shell> get_lib_cells */sky130_fd_sc_hd__xnor2*
{sky130_fd_sc_hd__tt_025C_1v80/sky130_fd_sc_hd__xnor2_1 sky130_fd_sc_hd__tt_025C_1v80/sky130_fd_sc_hd__xnor2_2 sky130_fd_sc_hd__tt_025C_1v80/sky130_fd_sc_hd__xnor2_4}

dc_shell> size_cell U3 sky130_fd_sc_hd__tt_025C_1v80/sky130_fd_sc_hd__xnor2_4
{U3}

dc_shell> report_timing
```

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/209799837-8f2a7288-194f-401e-96da-23965072518d.png" height = "350"></p>

```
#do the compile_ultra back

dc_shell> compile_ultra

dc_shell> report_timing
```

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/209800129-2d74923b-5fe4-40c3-bbd7-1af6d47611f9.png" height = "350"></p>

>	pick the best implementation given the constraints


## DC_D4SK2_L2 - Lab16 - part2 resource sharing optimizations

Note to self make sure target and lib as below 
```
dc_shell> echo $target_library
/nfs/png/disks/png_mip_gen6p9ddr_0032/nurul/VLSI/sky130RTLDesignAndSynthesisWorkshop/DC_WORKSHOP/lib/sky130_fd_sc_hd__tt_025C_1v80.db

dc_shell> echo $link_library
* /nfs/png/disks/png_mip_gen6p9ddr_0032/nurul/VLSI/sky130RTLDesignAndSynthesisWorkshop/DC_WORKSHOP/lib/sky130_fd_sc_hd__tt_025C_1v80.db
```

Open file
```
design_vision> sh gvim resource_sharing_mult_check.v &
```


<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/209887684-815501c8-a5fb-4037-b667-ccaa858c1cd8.png" height = "250"><img src = "https://user-images.githubusercontent.com/118953932/209887610-c98d3a0e-01e7-4219-a698-a1b77a1b8d51.png" height = "250"></p>

```
design_vision> read_verilog resource_sharing_mult_check.v

design_vision> link

design_vision> compile_ultra
```

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/209888638-78868a03-3b35-4a44-a344-2596bc7b7e1f.png" height = "500"></p>

>	expected the select go towards the output but it's implementing the select towards the input

```
design_vision> report_area #to know the area of the design
```

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/209889002-7c36c3c7-345e-4d69-a84b-bf1a3ac21dab.png" height = "350"><img src = "https://user-images.githubusercontent.com/118953932/209888882-cf35509a-dd13-404a-86a4-783bc285a34e.png" height = "350"></p>


<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/209889753-8eae73f4-59c1-4847-9659-1b470430b887.png" height = "350"><img src = "https://user-images.githubusercontent.com/118953932/209889771-4a8d1f29-7d0e-4a2c-9da5-04a280937abc.png" height = "350"><img src = "https://user-images.githubusercontent.com/118953932/209889811-0fb3068a-cf8c-4d47-a5f1-81f7a2b3092c.png" height = "250"></p>

```
design_vision> set_max_delay  -from [all_inputs] -to [all_outputs] 2.5
1

design_vision> report_timing
```

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/209890057-48a5a183-d2fa-4948-9628-33aea5968d4a.png" height = "350"></p>

```
design_vision> compile_ultra

design_vision> report_timing

design_vision> report_area
```


<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/209890311-d624deca-ddfd-44ea-aaeb-663f38e35e36.png" height = "350"><img src = "https://user-images.githubusercontent.com/118953932/209890337-b4470a68-2db1-4032-9c66-ad79897ff24a.png" height = "350"><img src = "https://user-images.githubusercontent.com/118953932/209890384-7e858e87-7d2d-4d4f-938a-aab978bb16ea.png" height = "250"></p>

>	2 ports decreases, area also decreases

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/209890716-f95ffeeb-0825-4445-b4ec-f591449ff8dc.png" height = "350"></p>

```
design_vision> set_max_delay 0.1  -from sel -to [all_outputs]
1


design_vision> report_timing
Information: Updating design information... (UID-85)
 
****************************************
Report : timing
        -path full
        -delay max
        -max_paths 1
Design : resource_sharing_mult_check
Version: P-2019.03-SP5-3
Date   : Thu Dec 29 09:09:56 2022
****************************************

Operating Conditions: tt_025C_1v80   Library: sky130_fd_sc_hd__tt_025C_1v80
Wire Load Model Mode: top

  Startpoint: sel (input port)
  Endpoint: y[6] (output port)
  Path Group: default
  Path Type: max

  Point                                                   Incr       Path
  --------------------------------------------------------------------------
  input external delay                                    0.00       0.00 r
  sel (in)                                                0.00       0.00 r
  U53/Y (sky130_fd_sc_hd__inv_2)                          0.04       0.04 f
  U54/Y (sky130_fd_sc_hd__o22ai_1)                        0.22       0.26 r
  U56/Y (sky130_fd_sc_hd__nor2_1)                         0.08       0.34 f
  DP_OP_9J1_122_9283/U13/SUM (sky130_fd_sc_hd__ha_1)      0.30       0.65 f
  DP_OP_9J1_122_9283/U6/COUT (sky130_fd_sc_hd__fa_1)      0.38       1.03 f
  DP_OP_9J1_122_9283/U5/COUT (sky130_fd_sc_hd__fa_1)      0.41       1.44 f
  DP_OP_9J1_122_9283/U4/COUT (sky130_fd_sc_hd__fa_1)      0.38       1.82 f
  DP_OP_9J1_122_9283/U3/COUT (sky130_fd_sc_hd__fa_1)      0.36       2.18 f
  U27/SUM (sky130_fd_sc_hd__fah_1)                        0.26       2.44 r
  y[6] (out)                                              0.00       2.44 r
  data arrival time                                                  2.44

  max_delay                                               0.10       0.10
  output external delay                                   0.00       0.10
  data required time                                                 0.10
  --------------------------------------------------------------------------
  data required time                                                 0.10
  data arrival time                                                 -2.44
  --------------------------------------------------------------------------
  slack (VIOLATED)                                                  -2.34


1

design_vision> compile_ultra

design_vision> report_area
```


<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/209891205-ed9a5835-138b-47d1-b68a-64aa2380642e.png" height = "350"><img src = "https://user-images.githubusercontent.com/118953932/209891018-5cde92ae-2c28-4269-a44d-55c010bd54f9.png" height = "350"></p>

```
design_vision> report_timing
```

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/209891496-41990dff-ad74-4870-895e-53ed03d959c1.png" height = "350"></p>

Constraint area

```
design_vision> set_max_area 800
1

design_vision> compile_ultra

design_vision> report_timing -sig 4

design_vision> report_area
```

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/209891615-23c6e000-c173-4376-8c4b-0bdade9de851.png" height = "350"><img src = "https://user-images.githubusercontent.com/118953932/209891812-a2cb9e80-1606-49ee-bdcc-6306b69e7884.png" height = "350"><img src = "https://user-images.githubusercontent.com/118953932/209891923-0815a162-5428-4cc0-afeb-868485ef1d32.png" height = "350"></p>

>	area cannot go below 800 maybe because timing constraints too tight

## DC_D4SK2_L3 - lab17 - seq optimizations

```
pglc00014> gvim dff_const* -o
5 files to edit
```

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/209893213-87e0d535-af1c-4f45-88fa-d536e03d2e8e.png" height = "350"></p>

```
dc_shell> reset_design
1

dc_shell> read_verilog dff_const1.v

dc_shell> link

dc_shell> compile

dc_shell> get_cells
{q_reg U4 U5}

dc_shell> foreach_in_collection my_cell [get_cells *] {
set cell_name [get_object_name $my_cell];
echo $cell_name; 
}
q_reg
U4
U5

dc_shell> foreach_in_collection my_cell [get_cells *] {
set cell_name [get_object_name $my_cell];
set rn [get_attribute [get_cells $cell_name] ref_name];  
echo $cell_name $rn; 
}
q_reg sky130_fd_sc_hd__dfrtp_1
U4 sky130_fd_sc_hd__conb_1
U5 sky130_fd_sc_hd__clkinv_1
```

**dff_const.v**

```
pglc00014> csh
pglc00014> design_vision

design_vision> read_verilog dff_const1.v

design_vision> link

design_vision> compile
```

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/209895577-e3bac260-a8bf-4871-8304-c1680eec078f.png" height = "350"><img src = "https://user-images.githubusercontent.com/118953932/209898785-c1dececa-311f-4244-a97e-38dc898fa61e.png" height = "200"></p>

>	gate terminal of CMOS is very sensitive "gate oxide". so we should never allow gate terminal of CMOS to see any surges (so use tie cells for driving 1'b1 or 1'b0. that why not connected directly)

>	Tie cell is a standard cell, designed specially to provide the high or low signal to the input (gate terminal) of any logic gate. The high/low signal can not be applied directly to the gate of any transistors because of some limitations of transistors, especially in the lower node

**dff_const2.v**

```
design_vision> reset_design
1
design_vision> read_verilog dff_const2.v

design_vision> link

design_vision> compile
```

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/209899035-c3723bc2-17a2-4bca-b8b4-b20508b00d3b.png" height = "350"></p>


Set dff_const2.v to sequential constant = false

```
design_vision> reset_design
1
design_vision> read_verilog dff_const2.v

design_vision> set compile_seqmap_propagate_constants false
false

design_vision> link

design_vision> compile
```

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/209902171-fa50a7ff-4d60-4348-9dec-f21d19f033ba.png" height = "350"></p>

**dff_const3.v**

```
design_vision> reset_design
1
design_vision> read_verilog dff_const3.v

design_vision> link

design_vision> compile
```

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/209901411-c71b77f8-de39-4975-bb75-b52e7abb5441.png" height = "350"><img src = "https://user-images.githubusercontent.com/118953932/209901451-2a4da5ff-5c87-47b7-90cf-9cc3d7664b39.png" height = "450"></p>


**dff_const4.v**

```
design_vision> reset_design
1
design_vision> read_verilog dff_const4.v

design_vision> link

design_vision> set compile_seqmap_propagate_constants true
true

design_vision> compile_ultra
```

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/209903776-5cf37bef-51d1-41bf-adf1-b7c019df1d00.png" height = "300"><img src = "https://user-images.githubusercontent.com/118953932/209904058-4ea68176-b4e6-4f14-8345-2b6ff98619bb.png" height = "300"></p>

**dff_const5.v**

```
design_vision> reset_design
1
design_vision> read_verilog dff_const5.v

design_vision> link

design_vision> compile
```

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/209905007-6579d844-2d97-40aa-9669-8d6a49671fd3.png" height = "300"><img src = "https://user-images.githubusercontent.com/118953932/209904522-6e0b02c3-5da4-435b-990a-28e40e1d9885.png" height = "300"></p>

## DC_D4SK3_L1 - Lecture13 special optimizations

**Register Retiming**

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/209915226-ad465c29-856e-4cd0-b468-c836e2edf2c8.png" height = "270"><img src = "https://user-images.githubusercontent.com/118953932/209915294-37409f26-b41b-4e2d-ba6c-5d4a4edc64e6.png" height = "300"></p>

>	break the combo logic. critical path delay decreases but functional DV may have issue

Note: need to be careful with this optimization. need to consider the repercussions of enabling or disable it ❗

**Boundary Optimization**

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/209924300-7f183ec5-570d-4dc5-bdfc-a3194f0a977e.png" height = "350"></p>

>	boundary will not be retained in the netlist but functional DV may have issue. hierarchy not preserved. not able to find the signal in the netlist but get most optimal logic

Note: need to see the benefit first ❗

Commands:

```
set boundary_optimization <design> <true/false>

#set boundary_optimization module_sub false
```

**Multicycle Path**


<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/209927086-e5ea6f5d-5986-4f15-b98d-9af2fab755f0.png" height = "350"></p>

>	data will only sample once in 2 cycles (need not optimize path in single cycle path)

Tell tool not to optimize this to single cycle path:

```
set multicycle_path -setup 2 -to prod_reg[*]/D -through [all_inputs]
```
Note: be very careful when using this. should have been thorough understanding of design ❗

**False Paths**
-	paths that are not valid for STA
	-	set false_path -from <> to <>
	-	set false_path -through <>

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/209929012-ae82a99b-474f-46a2-a68f-59d44df950ac.png" height = "350"></p>

Are always path between 2 different clocks async?
>	No. They are async only if 2 clocks are not related

**External Load vs Internal Load**

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/209929826-ced27bd0-0f93-4df4-b8a2-7507c99a4376.png" height = "350"></p>

What to do:
```
set isolate_ports -type buffer [get_ports Out_y]
```


<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/209930535-1d0ea710-13c9-40e3-bfe4-d569cc95e66b.png" height = "200"></p>

>	Internal path will not see the external load, the load is seen by the buffer


## DC_D4SK3_L2 - Lecure14 - How Paths are timed MCP?

**Single Cycle Path**

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/209938168-a7393285-9091-4799-b3fe-d4cc0554e31c.png" height = "350"></p> 

>	Hold is always checked at edge BEFORE setup

**Half Cycle Path**

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/209939284-2974e791-8f3c-4c92-a92e-e1dd59b858a1.png" height = "350"></p> 

>	Hold will happen at 1 edge before. Setup is very tight to meet because half of the cycle from launch to capture flop. Hold got sufficient margin

**Multi Cycle Path**

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/209942995-f936297c-e247-42e8-ac1a-c8a65599894c.png" height = "350"></p> 

>	Prod_reg is loaded once in every 2 cycles only


Can put this constraint:

```
set multicycle_path -setup 2 -from [all_inputs] -to prod_reg[*]/D 
```

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/209943734-6e97dcf8-5264-40d1-94f5-53641c236e3c.png" height = "200"></p> 

>	very bad for hold. So whenever apply for MCP for setup so we should apply for hold also

```
#also put this!

set multicycle_path -hold 1 -from [all_inputs] -to prod_reg[*]/D 

#so that launch edge will move forward
```

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/209944437-82b1c6b0-2129-4229-9a43-ab28537bbe3a.png" height = "200"></p> 

## DC_D4SK4_L1 - Lab18 - Boundary Optimization

```
dc_shell> sh gvim check_boundary.v &
```

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/209956910-4a2971bd-cf1e-4a12-927b-740c77ca52fd.png" height = "450"></p> 

```
dc_shell> read_verilog check_boundary.v

dc_shell> link

dc_shell> compile_ultra

dc_shell> write -f ddc -out boundary.ddc
```


<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/209957620-5ca4fe50-ae6e-440e-bb3d-19c9ce0b7d98.png" height = "250"><img src = "https://user-images.githubusercontent.com/118953932/209960735-b3fa7f2d-a2fc-45ff-8c5a-a7279f057d84.png" height = "450"</p> 

>	nothing call internal module. no hierarchy

```
design_vision> reset_design
1
design_vision> read_verilog check_boundary.v

design_vision> link
	
design_vision> get_cells
{u_im val_out_reg[3] val_out_reg[2] val_out_reg[1] val_out_reg[0] U1}
	
design_vision> get_pins u_im/*

design_vision> set_boundary_optimization u_im false
	
design_vision> compile_ultra
```

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/209962899-659c7f91-ea8c-47fe-a1a9-9a3d587d6b5d.png" height = "450"></p>

>	design hierarchy are maintained so if there any ECO, can quickly search for the bug. let tool not optimized fully

## DC_D4SK4_L2 - Lab19 - Register Retiming

```
design_vision> design_vision> reset_design
1
design_vision> sh gvim check_reg_retime.v &
11483
```

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/209965520-3becf04d-19a5-4def-a194-b49aea638e61.png" height = "450"></p>

```
design_vision> read_verilog check_reg_retime.v

design_vision> link

design_vision> compile
```

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/209965852-63726be8-41b5-4c12-9564-20e86935cbf4.png" height = "200"><img src = "https://user-images.githubusercontent.com/118953932/209966816-31f887bf-0cab-4fd3-8b7c-ae674b3c686b.png" height = "350"></p>

```
design_vision> report_timing
Information: Updating design information... (UID-85)
 
****************************************
Report : timing
        -path full
        -delay max
        -max_paths 1
Design : check_reg_retime
Version: P-2019.03-SP5-3
Date   : Thu Dec 29 22:17:34 2022
****************************************

Operating Conditions: tt_025C_1v80   Library: sky130_fd_sc_hd__tt_025C_1v80
Wire Load Model Mode: top

  Startpoint: q3_reg[7] (rising edge-triggered flip-flop)
  Endpoint: c[7] (output port)
  Path Group: (none)
  Path Type: max

  Point                                                   Incr       Path
  --------------------------------------------------------------------------
  q3_reg[7]/CLK (sky130_fd_sc_hd__dfrtp_1)                0.00       0.00 r
  q3_reg[7]/Q (sky130_fd_sc_hd__dfrtp_1)                  0.31       0.31 f
  c[7] (out)                                              0.00       0.31 f
  data arrival time                                                  0.31
  --------------------------------------------------------------------------
  (Path is unconstrained)


1
```

```
#set the constraints
design_vision> sh gvim reg_retime_cons.tcl

design_vision> source reg_retime_cons.tcl
1
```

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/209967968-b84788af-ab72-4e43-8e46-c891b81b374b.png" height = "350"></p>

```
design_vision> report_clock
Information: Updating graph... (UID-83)
 
****************************************
Report : clocks
Design : check_reg_retime
Version: P-2019.03-SP5-3
Date   : Thu Dec 29 22:35:09 2022
****************************************

Attributes:
    d - dont_touch_network
    f - fix_hold
    p - propagated_clock
    G - generated_clock
    g - lib_generated_clock

Clock          Period   Waveform            Attrs     Sources
--------------------------------------------------------------------------------
myclk            2.00   {0 1}                         {clk}
--------------------------------------------------------------------------------
1

design_vision> report_timing
Information: Updating design information... (UID-85)
 
****************************************
Report : timing
        -path full
        -delay max
        -max_paths 1
Design : check_reg_retime
Version: P-2019.03-SP5-3
Date   : Thu Dec 29 22:35:15 2022
****************************************

Operating Conditions: tt_025C_1v80   Library: sky130_fd_sc_hd__tt_025C_1v80
Wire Load Model Mode: top

  Startpoint: b[2] (input port clocked by myclk)
  Endpoint: q1_reg[7] (rising edge-triggered flip-flop clocked by myclk)
  Path Group: myclk
  Path Type: max

  Point                                                   Incr       Path
  --------------------------------------------------------------------------
  clock myclk (rise edge)                                 0.00       0.00
  clock network delay (ideal)                             0.00       0.00
  input external delay                                    1.20       1.20 f
  b[2] (in)                                               0.00       1.20 f
  mult_4/B[2] (check_reg_retime_DW02_mult_0)              0.00       1.20 f
  mult_4/U17/Y (sky130_fd_sc_hd__inv_2)                   0.12       1.32 r
  mult_4/U43/Y (sky130_fd_sc_hd__nor2_1)                  0.06       1.38 f
  mult_4/U3/X (sky130_fd_sc_hd__and2_1)                   0.16       1.55 f
  mult_4/S3_2_2/COUT (sky130_fd_sc_hd__fa_1)              0.41       1.95 f
  mult_4/S5_2/SUM (sky130_fd_sc_hd__fa_1)                 0.48       2.44 f
  mult_4/U7/X (sky130_fd_sc_hd__and2_1)                   0.18       2.61 f
  mult_4/U30/Y (sky130_fd_sc_hd__nor2_1)                  0.15       2.76 r
  mult_4/U9/Y (sky130_fd_sc_hd__inv_2)                    0.04       2.80 f
  mult_4/U33/Y (sky130_fd_sc_hd__a21oi_1)                 0.16       2.95 r
  mult_4/U10/Y (sky130_fd_sc_hd__xnor2_1)                 0.12       3.08 r
  mult_4/PRODUCT[7] (check_reg_retime_DW02_mult_0)        0.00       3.08 r
  q1_reg[7]/D (sky130_fd_sc_hd__dfrtp_1)                  0.00       3.08 r
  data arrival time                                                  3.08

  clock myclk (rise edge)                                 2.00       2.00
  clock network delay (ideal)                             0.00       2.00
  clock uncertainty                                      -0.30       1.70
  q1_reg[7]/CLK (sky130_fd_sc_hd__dfrtp_1)                0.00       1.70 r
  library setup time                                     -0.08       1.62
  data required time                                                 1.62
  --------------------------------------------------------------------------
  data required time                                                 1.62
  data arrival time                                                 -3.08
  --------------------------------------------------------------------------
  slack (VIOLATED)                                                  -1.46


1

```

```
design_vision> compile_ultra -retime
```


<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/209968764-079af7cb-1372-425b-9487-21207040c18a.png" height = "450"></p>

>	sliced the multiplier and split the logic into partition and nicely optimized it. as in the picture, there are logics between 2 registers

```
design_vision> report_timing
Information: Updating design information... (UID-85)
 
****************************************
Report : timing
        -path full
        -delay max
        -max_paths 1
Design : check_reg_retime
Version: P-2019.03-SP5-3
Date   : Thu Dec 29 22:41:10 2022
****************************************

Operating Conditions: tt_025C_1v80   Library: sky130_fd_sc_hd__tt_025C_1v80
Wire Load Model Mode: top

  Startpoint: q3_reg[0] (rising edge-triggered flip-flop clocked by myclk)
  Endpoint: c[0] (output port clocked by myclk)
  Path Group: myclk
  Path Type: max

  Point                                                   Incr       Path
  --------------------------------------------------------------------------
  clock myclk (rise edge)                                 0.00       0.00
  clock network delay (ideal)                             0.00       0.00
  q3_reg[0]/CLK (sky130_fd_sc_hd__dfrtp_1)                0.00       0.00 r
  q3_reg[0]/Q (sky130_fd_sc_hd__dfrtp_1)                  0.37       0.37 f
  U57/Y (sky130_fd_sc_hd__inv_4)                          0.11       0.48 r
  U58/Y (sky130_fd_sc_hd__inv_16)                         0.10       0.58 f
  c[0] (out)                                              0.00       0.58 f
  data arrival time                                                  0.58

  clock myclk (rise edge)                                 2.00       2.00
  clock network delay (ideal)                             0.00       2.00
  clock uncertainty                                      -0.30       1.70
  output external delay                                  -1.20       0.50
  data required time                                                 0.50
  --------------------------------------------------------------------------
  data required time                                                 0.50
  data arrival time                                                 -0.58
  --------------------------------------------------------------------------
  slack (VIOLATED)                                                  -0.08


1
```

```
design_vision> compile_ultra

design_vision> report_timing -from [all_inputs] -trans -cap -nosplit -sig 4
```


<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/209970856-c2b92428-13c6-481d-87b8-a1c9bf62b415.png" height = "450"></p>

## DC_D4SK4_L3 - Lab20 - Isolating output ports

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/210025171-60548d42-a1af-4f59-80d1-20808f8f950c.png" height = "250"></p>

>	we dont want internal path to fail because of external load. hence, that's why we isolate the output port


```
design_vision> sh gvim check_boundary.v &
23733

#same as lab previous (boundary optimization)
```

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/210025348-4579716c-8d87-4d50-aa87-2073deabcff4.png" height = "300"></p>

```
design_vision> read_verilog check_boundary.v

design_vision> link

design_vision> compile_ultra
```

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/210025625-0e5ac602-65be-4314-aff0-e15daf43a3d7.png" height = "350"></p>

>	it drives the output load as well as the internal logic. not good!!


**Isolate Port**

```
design_vision> set_isolate_ports -type buffer [all_outputs]

design_vision> compile_ultra
```


<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/210026026-bf6f72a9-7385-4774-9228-5006b1c2a27a.png" height = "450"></p>

>	the internal load are driven by the flop, outputs are driven by the buffer. Flop delay remain constant, only buffers see variation


**Report Timing before isolate port (reg to IO path)**

```
#dc_shell

reset_design
read_verilog check_boundary.v
link
compile_ultra
create_clock -per 5 -name myclk [get_ports clk]
set_input_delay -max 2 [all_inputs] -clock myclk
set_output_delay -max 2 [all_outputs] -clock myclk
set_load -max 0.3 [all_outputs]
report_timing -nosplit -inp -cap -trans -sig 4
```

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/210026412-be8811f9-8666-4f2d-8140-c676d0c74305.png" height = "350"></p>

**Report Timing before isolate portr (reg to reg path)**

```
dc_shell> report_timing -to val_out_reg[0]/D -inp -trans -nosplit -cap -sig 4
```


<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/210026588-e64cd63a-285f-44a9-8296-b81fb54b3cc6.png" height = "350"></p>


**Report Timing after isolate port (both paths)**

```
dc_shell> set_isolate_ports -type buffer [all_outputs]

dc_shell> compile_ultra

dc_shell> report_timing -nosplit -inp -cap -trans -sig 4

dc_shell> report_timing -from val_out_reg[0]/CLK -to val_out_reg[0]/D -nosplit -inp -cap -trans -sig 4
```

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/210026812-e5805897-9427-466e-a25f-279450769e47.png" height = "350"><img src = "https://user-images.githubusercontent.com/118953932/210027164-fc6f4ddf-4c9b-43fa-9d61-0736714dad53.png" height = "350"></p>

## DC_D4SK4_L4 - Lab21 - MultiCycle path

```
dc_shell> sh gvim mcp_check.v
```

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/210028790-7957e953-2945-4afa-b38e-33e439e1dc79.png" height = "350"></p>

```
dc_shell> read_verilog mcp_check.v

dc_shell> link

dc_shell> compile_ultra

dc_shell> sh gvim mcp_check_cons.tcl &  #reading the constraints written
```

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/210028845-cc6475c9-1c0e-41cb-b212-1ba07f030299.png" height = "300"><img src = "https://user-images.githubusercontent.com/118953932/210028994-6e6845e7-ffc2-4c64-933b-a369f4388f65.png" height = "300"></p>

```
dc_shell> source mcp_check_cons.tcl

dc_shell> report_timing
```

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/210029151-5aed5b64-bee2-462e-b303-a3568bd68d79.png" height = "350"></p>

```
dc_shell> compile_ultra

dc_shell> report_timing
```

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/210029286-043305fa-dac4-4662-8c30-c694a7698f98.png" height = "350"></p>

>	from the design, input to prod_reg path can be 2 cycles delay because only when en_int coming


```
dc_shell> set_multicycle_path -setup 2 -to prod_reg[*]/D -from [all_inputs] 
#have to put all_inputs
```

>	valid to prod_reg is a single cycle path. if did not put [all_inputs] it will mcp the valid to prod_reg path also (CRIMINAL MISTAKE!!)

```
dc_shell> report_timing -to prod_reg[*]/D -from valid_reg/CLK

dc_shell> report_clock *
```

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/210030206-258dd684-4810-4f44-a2b2-e95fb874b6a4.png" height = "350"><img src = "https://user-images.githubusercontent.com/118953932/210030288-789b2e30-052f-4a12-9785-73937d67c191.png" height = "250"</p>

**This is where MCP is applied**

```
dc_shell> report_timing -to prod_reg[*]/D -from [all_inputs]
```

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/210030514-a191aaee-2d6b-46d7-a204-6f3cd1c5a93a.png" height = "400"></p>

**Hold**

```
dc_shell> report_timing -delay min
```

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/210030769-d5f278f2-7f91-4ffd-95b1-aed1db1bf147.png" height = "350"></p>

>	need to apply hold MCP also

**Apply MCP for hold**

```
dc_shell> set_multicycle_path -hold 1 -from [all_inputs] -to prod_reg[*]/D

dc_shell> report_timing -delay min  -to prod_reg[*]/D -from [all_inputs]
```

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/210030957-a11569d7-83a7-47ff-b8bd-1c2e1dd0c416.png" height = "350"></p>

>	launch at zero capture at zero 🙂👍

**Port isolated report timing**

```
#do the previous"s lab method to isolate the port

dc_shell> report_timing -nosplit -inp -cap -trans -sig 4
```

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/210031189-3ab31491-0a53-40a5-a66d-35381fa48014.png" height = "350"></p>

>	if dont isolate then will get timing violation

# Day-10
## DC_D5SK1_L1 - Lecture Report timing

**Generating Timing Report**

Example Commands:

```
report_timing -from DDF_A/clk

report_timing -from DDF_A/clk -to DDF_A/d

report_timing -fall_from DDF_A/clk

report_timing -rise_from DDF_b/clk

report_timing -delay_type min -to DDF_C/d

report_timing -delay_type min -through INV/a

report_timing -delay_type max -through AND/b

report_timing -rise_from DDF_b/clk -delay_type max -nets -cap -trans -sig 4

#default is delay_type max (if didnt specify the delay type)
```

**Propagation Delay**

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/210036279-d9408cbd-b7d7-48a1-a78e-776d03b19c68.png" height = "350"></p>

>	For inv. If A rises, Y will fall and NMOS circuit will enable, PMOS circuit will disable. Vice versa

>	current sinking path (to GND) and current sourcing path (to Y) are different. mobility is different. DELAYS ARE NOT SAME ❗ Load on A and load on B are different too

**Timing Paths** 


<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/210037874-1f4dcc72-1087-48d2-9d01-f68a6ea4e685.png" height = "350"></p>

>	2 different timing path and tool will calculate rise delay and fall delay 


>	when doing report_timing -delay min to DFFC/D (Min Delay to C) -> lowest delay which is from DFFB/D (1.0ns) ❗


>	when doing report_timing -delay max to DFFC/D (Max Delay to C) -> highest delay which is from DFFA/D (1.65ns) ❗


>	report_timing -delay_type max -rise_to DFFC/D (max rise delay) -> from DFFA to DFF_C(r) (1.5ns) ❗


>	report_timing -delay_type max -fall_to DFFC/D (max fall delay) -> from DFFA to DFF_C(f) (1.65ns) ❗

>	report_timing -delay_type min -rise_to DFFC/D (min rise delay) -> from DFFB to DFF_C(r) (1.15ns) ❗

>	report_timing -delay_type min -fall_to DFFC/D (min fall delay) -> from DFFB to DFF_C(f) (1.0ns) ❗


**Timing Path Part 2**


<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/210040203-714e74f9-85d2-4a68-a6de-aa5940e313bd.png" height = "350"></p>


>	setup = before that the data shoulde stable

>	hold = after that should be stable

Note: KNOW THE DIFFERENCE OF SLACK CALCULATION BETWEEEN THE TWO ❗


**Max_Paths and Nworst**

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/210041980-8cf44b64-a9c8-4aab-8cb8-4b1193888ae9.png" height = "350"></p>


## DC_D5SK1_L2 - Lab Report timing

```
dc_shell> sh gvim lab8_circuit_modified.v 

(inside gvim)

:sp la8_cons_modified.tcl #to look at the constraint of the design
```

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/210043683-b25c60dc-437b-4b8d-9871-f6f467cf5d37.png" height = "450"><img src = "https://user-images.githubusercontent.com/118953932/210043896-01c357af-a3b2-4088-a6e8-7af356c6e61e.png" height = "250"></p>


```
dc_shell> read_verilog lab8_circuit_modified.v 

dc_shell> link

dc_shell> source lab8_cons_modified.tcl

dc_shell> compile_ultra

dc_shell> report_timing -sig 4 -nosplit -trans -cap -input_pins -from IN_A > t1.rpt

dc_shell> sh gvim t1.rpt
```

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/210045580-747424c7-e443-40a1-a09b-a74bb6010d5d.png" height = "450"></p>

>	Setup!!!

```
dc_shell> report_timing -rise_from IN_A -sig 4 -transition_time -capacitance -input_pins > t2.rpt
```

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/210046581-b54b086d-f7a9-4bd2-a39f-b1057cc2855a.png" height = "500"></p>

```
dc_shell> report_timing -rise_from IN_A -sig 4 -transition_time -capacitance -input_pins -to REGA_reg/D > t3.rpt

dc_shell> sh gvim t1.rpt -O t3.rpt &
```

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/210047453-12a60b99-b042-46fc-9c15-aab95d3045f1.png" height = "400"></p>


**Hold Check**

```
dc_shell> report_timing -delay min -from  IN_A
```

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/210048106-37258ed0-e36f-46bf-9e43-4bda33e0b34b.png" height = "350"></p>

**Report timing through U15/Y**

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/210048228-8452fd36-2ca9-4bf3-b9ef-6055201dce80.png" height = "350"><img src = "https://user-images.githubusercontent.com/118953932/210048385-4ff22735-7dd9-4eb1-9dd4-dba893aad9ee.png" height = "350"></p>

>	delay U15 does not matter. It does not look at the contribution of the cell ❗ It look at the overall path delay ❗ Overall max path is 7.03 while overall min path is 4.07. Hence the report of the report timing.

## DC_D5SK1_L3 - Lab Check_timing, Check_design, Set_max_capacitance, HFN

```
dc_shell> read_verilog lab8_circuit_modified.v

dc_shell> link

dc_shell> check_design
```

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/210050969-baeb5568-006c-466e-8027-ddb3b70faa47.png" height = "150"></p>

**Before sourcing constraints**

```
dc_shell> compile_ultra

dc_shell> check_timing #check whether design is constraint properly or not

dc_shell> report_constraints #default constraints loaded in the tool memory
```

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/210051257-a1383495-105d-4eea-9206-83780b10bdc6.png" height = "300"><img src = "https://user-images.githubusercontent.com/118953932/210051897-19ecd081-7d33-44fa-bc22-f845428bec46.png" height = "200"></p>

**Sourcing constraints**

```
dc_shell> source lab8_cons_modified.tcl 

dc_shell> check_timing

```

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/210052179-e5164b77-d09e-4cb0-b66c-1d4dd24e5ce4.png" height = "300"></p>

>	clk created that's why reg to reg path are constraints. input delay and output delay are also annotated. That two clock ports that are unconstraint are fine to leave as unconstraint.


```
dc_shell> report_timing

dc_shell> report_constraints
```

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/210053094-d219925a-3769-4a97-83b2-9283208e9a2f.png" height = "300"><img src = "https://user-images.githubusercontent.com/118953932/210053189-79ae89f8-fe83-45e0-863c-e1d3d352b0b3.png" height = "200"></p>

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/210053294-1d95f1be-baf2-4d79-b0ba-10384dcf99f6.png" height = "400"></p>

**New Design**

```
dc_shell> reset_design

dc_shell> sh gvim mux_generate.v 

(inside gvim)
:sp mux_generate_128_1.v
```

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/210054734-32b6c74a-d792-4800-a5e3-4f28abd1fed5.png" height = "500"></p>

```
dc_shell> read_verilog mux_generate_128_1.v 

dc_shell> link

dc_shell> compile_ultra

dc_shell> write -f verilog -out mux_generate_128_1_net.v

dc_shell> sh gvim mux_generate_128_1_net.v &
```

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/210054944-9cd43c65-6d37-4b35-b95b-22a6071fe57a.png" height = "220"><img src = "https://user-images.githubusercontent.com/118953932/210055453-78f4b281-bb97-4acf-9e11-3e565dce4159.png" height = "350"></p>

```
dc_shell> get_cells * -hier -filter "is_sequential == true"

dc_shell> get_cells * -hier -filter "is_sequential == false"
{U516 U517 U518 U519 U520 U521 U522 U523 U524 U525 U526 U527 U528 U529 U530 U531 U532 U533 U534 U535 U536 U537 U538 U539 U540 U541 U542 U543 U544 U545 U546 U547 U548 U549 U550 U551 U552 U553 U554 U555 U556 U557 U558 U559 U560 U561 U562 U563 U564 U565 U566 U567 U568 U569 U570 U571 U572 U573 U574 U575 U576 U577 U578 U579 U580 U581 U582 U583 U584 U585 U586 U587 U588 U589 U590 U591 U592 U593 U594 U595 U596 U597 U598 U599 U600 U601 U602 U603 U604 U605 U606 U607 U608 U609 U610 U611 U612 U613 U614 U615 ...}
```

>	it says it is a latch because we use "always"


```
dc_shell> report_timing -net -cap -sig 4

dc_shell> check_timing
```

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/210056158-61499240-b8ee-46d7-b963-4cc15d14ff16.png" height = "400"><img src = "https://user-images.githubusercontent.com/118953932/210056364-e349578f-ff6e-4d70-ac30-ae1cac67b436.png" height = "200"></p>

```
#set constraints

dc_shell> set_max_delay -from [all_inputs] -to [all_outputs] 3.5
1
dc_shell> report_timing
```

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/210057429-99136cb2-3481-4530-a116-7ef13b33edd7.png" height = "300"></p>

```
dc_shell> set_max_capacitance 0.025 [current_design]
Current design is 'mux_generate'.
1

dc_shell> report_constraint -all_violators
```

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/210057842-2429806d-f205-45cc-b19e-35f0ec6533ad.png" height = "300"></p>

```
dc_shell> compile_ultra

dc_shell> check_timing 
Information: Updating design information... (UID-85)

Information: Checking generated_clocks...

Information: Checking loops...

Information: Checking no_input_delay...

Information: Checking unconstrained_endpoints...

Information: Checking pulse_clock_cell_type...

Information: Checking no_driving_cell...

Information: Checking partial_input_delay...
1

dc_shell> report_constraints

dc_shell> report_timing

dc_shell> report_timing -net -cap -sig 4
```

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/210058079-1f04cb1f-7674-4428-9da1-1ba75bd0b195.png" height = "300"><img src = "https://user-images.githubusercontent.com/118953932/210058219-f67eece1-96c8-4df1-93fb-c2c51d3fe9ac.png" height = "500"><img src = "https://user-images.githubusercontent.com/118953932/210058649-4bbc91df-7235-41a9-aeb5-1f2b0cf4b74e.png" height = "500"></p>

>	Optimized!! Max capacitance less than 25 fF and fanout got split, nets got buffered

>	So whenever we are doing synthesis we should limit the capacitance so that high fanout net are buffered properly ❗

>	HFN = high fanout net

**New design**

```
dc_shell> sh gvim en_128.v
```

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/210059729-a3d7d368-962b-4d29-8bf8-e86fc864f735.png" height = "200"></p>

```
dc_shell> reset_design 

dc_shell> read_verilog en_128.v

dc_shell> link

dc_shell> compile_ultra

dc_shell> report_timing -from en -inp -nets -cap
```

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/210060027-0020fad8-470f-415b-8ab6-01c3490b780d.png" height = "350"></p>

```
dc_shell> set_max_capacitance 0.03 [current_design]

dc_shell> report_constraints

```

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/210060370-e1799579-0c82-4410-9e25-a65f003ec4aa.png" height = "200"></p>

```
dc_shell> compile_ultra 

dc_shell> report_timing -from en -inp -nets -cap -sig 4
```

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/210060716-dfa7f383-5c13-41a7-b51e-ac525650966f.png" height = "350"></p>

>	enable driving 17 buffers and buffers drive the other buffers and so on

```
dc_shell> write -f ddc -out  en_128.ddc

design_vision> read_ddc en_128.ddc
```

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/210062899-24c96cf1-4e23-4700-9fd1-68792b73498c.png" height = "300"><img src = "https://user-images.githubusercontent.com/118953932/210063442-0ba38b3d-63b7-4aa6-8dfd-585fa5c3a069.png" height = "350"></p>

>	buffer driving only few bits of nets. few AND gates (selected bold white lines) single pin is not having burden of driving such a huge heavily loaded net

**Note: set_max_cap is mainly for breaking or buffering the high fanout net ❗**

**set_max_transition**

```
dc_shell> report_timing -from en  -nets -cap -sig 4 -trans
```

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/210064023-8f8717d0-0d26-4857-8c90-c9d7226e868e.png" height = "350"></p>

```
dc_shell> set_max_transition 0.150 [current_design]

dc_shell> report_constraints

dc_shell> report_constraint -all_violators
```

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/210064217-42881f4e-e78e-47f2-9103-94896c9214bd.png" height = "200"><img src = "https://user-images.githubusercontent.com/118953932/210064563-baf1dfd3-132a-4320-853d-f2d106327585.png" height = "350"></p>

>	dc will optimize the high cost
	

	
```
dc_shell> compile_ultra
	
dc_shell> report_constraint -all_violators

dc_shell> report_timing -inp -nets -cap -trans -sig 4 -nosplit

```

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/210068625-c9acbaf0-9617-4e03-a03f-215340c8ad0c.png" height = "200"><img src = "https://user-images.githubusercontent.com/118953932/210068798-e033d647-32db-465b-ad26-440bf0e82e9b.png" height = "300"></p> 

>	transtion not violated anymore. nothing beyond 0.150. it splits the nets and upsize the buffer


```
dc_shell> report_timing -inp -nets -cap -trans -sig 4 -nosplit -from en -to y[116]
```

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/210069098-a2e6c8b4-ca3b-45d1-bbd2-2d0416a707e5.png" height = "350"></p>

>	broke the net and adjust the net such as the transition is not that bad. bad transition will resulted in bad delay

**Note: set_max_transition can be use for breaking or buffering the high fanout net ❗ use it correctly**

Conclusion:

1.	**check_design** is to ensure that the quality of the design is proper. if the design is proper or not. if there are any missing things in the design
2.	**check_timing** will ensure all the proper constraints are in place
3.	**report_constraints** to check what are the constraints we are checking. if there is any violation, it will report
4.	**set_max_capacitance** and **set_max_transition** will check if there are any high fanout net and broken and buffered properly so that there are no transition issues


<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/210071598-17c689f3-1428-4cad-96f2-3488252eb06c.png" height = "350"></p>

**What is QTM and ETM?**

Timing Models

**ETM** = Extracted Timing Models .lib format for cell-based reusable IP and physical design flow

-	an abstraction of the block using sequential and
combinational timing arcs. NLDM lookup tables are extracted for each of the timing arcs whose
delay is a function of input transitions and output loads, which makes the **ETM usable with
different input transition times and different output loads**.
Using ETMs to abstract the timing model of a complex block or IP hides the detailed design
implementation information. This usage model is ideal for IP providers.

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/210073020-b2a24e4a-a227-4b1d-b6c1-97333355442a.png" height = "200"></p>

<p align="center">source from Mantra VLSI</p>

**QTM** = Quick Timing Models for top-down design

-	In the early stages of the design cycle, if a block does not yet have a netlist, you can use a **quick
timing model** to describe its initial timing. Later in the cycle, you can **replace each quick timing
model with a netlist block** to obtain more accurate timing.

# Day-11
## Introduction to BabySoC

<details><summary>What and Why SoC</summary>

-	SoC or system-on-chip is an integrated circuit or IC that combines many elements of a computer system (integrates all the components) into a single chip
	
-	it is a single die chip that has some different IP core on it. these IP's could vary from digital to analog
	
-	The design usually includes CPU (central unit processing), system memory, I/O ports, secondary storage devices and peripheral interfaces
	
-	It can also consists of a digital or analog signal processing system or a floating-point unit (depends upon the requirement)
	
-	PPA = increased performance, reduced power comsuption and smaller semiconductor die area
	
-	The use of SoC makes computers smaller, faster, cheaper and less power consumption.	
		
</details>

<details><summary>Typical Structure of a snapdragon SoC</summary>
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/210313923-0ca4b4bc-5b94-4d08-8717-f5b1fd5ee8ae.png" height = "350"></p>
	
<p align="center">Taken from Lecture's Note</p>
	
</details>

<details><summary>Types of SoC</summary>
	
-	built around a microcontroller
	
-	built around a microprocessor (often found in phones)
	
-	designed for specific applications (speacialized application-specified integrated circuit SoCs)
	
	-	 examples: IoT, Industrial IoT, and Artificial Intelligence (AI)
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/210314620-8211bd61-1eb9-423a-b528-5e615e927a14.png" height = "400"></p>	

<p align="center">Credit: Wikipedia</p>
	
</details>	
	
<details><summary>SoC Structure</summary>	
	
-	consists of hardware functional units, icluding microprocessors that run software code, as well as a communications subsystem to connect, control, direct and interface between these functional modules
	
-	Functional components: Processor Cores, Memory, Interfaces, Digital Signal Processor and others
	
	-	Processor Cores: usually SoC contains at least one or more than one coprocessor. It can be a microcontroller, microprocessor, or DSP. Most of the time DSP is used in every SoC as a processor
	
	-	Memory: for the purpose of storage. May be a volatile or non-volatile memory. Volatile memory includes RAM there are two types of RAM one is SRAM and another is DRAM. The non-volatile memory includes ROM
	
	-	DSP: to perform signal processing operations such as data collection, data processing, etc. it is also used for the purpose of decoding the images
	
	-	Peripheral devices: externally connected devices/interfaces such as USB, HDMI, Wi-Fi, and Bluetooth are included in peripheral devices
	
	-	UART: Universal Asynchronous Receiver Transmitter is included in SoC which is used to transmit or receive serial data
	
-	Intermodule communications: Bus-Based Communication, Network on a chip
	
	-	Bus-based communication: communicating between components in a system-on-a-chip (SoC) design
	
	-	Network on a chip: a router-based packet switching network between SoC modules

</details>

<details><summary>SoC Design Flow</summary>
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/210319070-e06a5a96-e768-463c-b078-b1f153bfbad5.png" height = "400"></p>
		
</details>

<details><summary>How Are Microchips Made</summary>
	
1.	It is made out of silicon (silicon rich sand) because silicon is a semiconductor (between insulator and pure conductor). Its properties such as its conductivity can be altered by adding impurities or doping to meet the needs of different electronic devices which also allows us to control electrical signals that pass through
	
2.	Silicon is also abundant (common elements found on earth). But, mostly, silicon found is bound to oxygen. Hence, they must be seperated by combining the sand with carbon to produce carbon monoxide and 99% pure silicon
	
3.	Ultra pure silicon is produced after futher processing
	
4.	Seed crystal is placed in contact with molten silicon. Seed crystal is pulled away and silicon atoms are deposited on the bottom surface. The result is a large cylindrical boule or a single crystal ingot of pure silicon
	
5.	Boule is then thinly sliced into wafers (bigger wafers able to yield more microchips)
	
6.	Microchips are made in extremely sterile conditions free from contaminants such as dust
	
7.	First step: Deposition
	
	-	a thin non-conducting layer of silicon dioxide is grown or deposited on the surface of the wafer
	
8.	Silicon wafer went through **Litography**:
	
	-	coats with photosensitive and light resistance materials
	
9.	Critical step: Exposure
	
	-	exposed to UV light passed through a reticle containing the chip's blueprint (the area exposed are harden while unexposed are etched away by hot gases to leave a 3D microchip)
	
>	Note: the electrical conductivity of different part of the chipcan also be altered by doping them with chemicals under heat and pressure
	
10.	To create a conducting paths between the components, a thin layer of metal such as aluminium is overlaid onto the chip (etching process is used to remove everything except the thin conducting pathways)
	
11.	Severals layers of conductors seperated by glass insulators can be laid down
	
12.	Each of the wafers is tested for performance before seperated from other chips on the wafer by a saw
	
>	Note: Microchips have a basic set of components such as **capacitors** (temporarily store an electrical charge), **resistors** (control the electrical current), **transistors** (can either amplify or switch the electrical signals passing through)
	
</details>

<details><summary>Introduction To BabySoC</summary>
	
-	small mixed-signal SoC
	
-	based on RVMYTH (a RISCV-based processor)
	
-	will leverage a PLL as its clock generator and controller and a 10-bit DAC
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/210322480-9909e3fe-337e-49be-870e-d774a8b91fa7.png" height = "350"></p>

<p align="center">Credit: VLSI System Design (from lecture)</p>
	
</details>

<details><summary>BabySoC Components</summary>
	
-	**RVMYTH**: **RVMYTH** core is a simple **RISCV-based CPU**
	-	**RISC-V** is  an instruction set architecture (ISA) rooted in reduced instruction set computer (RISC) principles
	-	Reason why based on **RISC-V** : 
		-	it simplifies the instructions given to the processor to accomplish tasks and provides the flexibility to create thousands of possible custom processors (enables companies to get their designs to market faster)
		-	it is a common, free, open-source ISA to which software can be ported, hardware can be developed, and processors can be built to support it
	
>	Instruction Set Architecture (ISA) is basically the portion of the machine that is visible to the assembly level programmer or the compiler writer. ISA is where software meets hardware. ISA defines the commands/ instructions that can natively be understood by a machine and its micro-architecture, and it also defines how the instructions are to be stored, accessed, and implemented
	
-	PLL (Phase Locked Loop) 
	-	a control system that generates an output signal whose phase is related to the phase of an input signal. 
	-	widely used for synchronization purposes, including clock generation and distribution
	-	used for clock retiming and recovery, as a frequency synthesizer, and as a tunable oscillator
	-	generally used in multimedia, communication and in many other applications
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/210328722-8144692a-d20c-4b8d-9b83-a747d4d3ff27.png" height = "250"></p>

<p align="center">Credit: DigiKey</p>
	
-	DAC: (Digital-to-Analog Converter) a system that converts a digital signal (consists of a number of binary inputs) into an analog signal (single output such as voltage or current) which they are widely used in modern communication systems enabling the generation of digitally-defined transmission signals

	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/210332915-fe97ee46-b42b-4dd8-84b7-854a8d716c77.png" height = "250"></p>

<p align="center">Credit: electricaltechnology</p>
	
</details>

<details><summary>Introduction To Modelling</summary>
	
-	Some initial input signals will be fed into BabySoC module that make the pll start generating the proper CLK for the circuit
-	The clock signal will make the rvmyth to execute instructions in its imem. As a result, the register r17 will be filled with some values cycle by cycle 
-	These values are used by dac core to provide the final output signal named OUT
-	So, we have got3 main elements (IPcores) and a wrapper as an SoC and of-course there would be also a test bench module out there	
	
</details>

# Day-12
## VSDBabySoC Modelling

<details><summary>What does modelling mean?</summary>

-	Modeling and simulation is the use of a physical or logical representation of a given system to generate data and help determine decisions or make predictions about the system.
	
-	Models can aid in defining, analyzing, and communicating a set of concepts
	
-	Purpose of modelling:
	
	-	support analysis, specification
	
	-	design
	
	-	verification
	
	-	validation of a system
	
	-	communicate certain information
	
	
</details>

<details><summary>What we modelling?</summary>
	
M&S **VSDBabySoC**:	
	
1.	initial input signals will be fed into vsdbabysoc module
	
2.	which will get the pll start generating the proper CLK for the circuit
	
3.	clock signal will make the rvmyth to execute instructions and some values are generated, these values are used by DAC core to provide the final output signal named OUT

3 main elements (IP cores) and a wrapper as an SoC (there would be also a testbench module):

-	RVMYTH modelling
-	PLL modelling
-	DAC modelling 
	
</details>

<details><summary>RVMYTH - Risc-V based MYTH (Microprocessor for You in Thirty Hours)</summary>
	
-	RISC stands for Reduced instruction set computer 
	
-	RISC-V (pronounced “risk-five”) ISA is defined as a base integer ISA, which must be present in any implementation, plus optional extensions to the base ISA
	
-	Each base integer instruction set is characterized by the width of the integer registers and the corresponding size of the address space and by the number of integer registers. There are two primary base integer variants, RV32I and RV64
	
</details>

<details><summary>Phase Locked Loop</summary>

-	an electronic circuit with a voltage or voltage-driven oscillator that constantlyadjusts to match the frequency of an input signal
	
-	used to generate, stabilize, modulate, demodulate etc
	
</details>

<details><summary>Digital-to-Analog Converter</summary>
	
-	converts a digital input signal into an analog output signal
	
-	digital signal = binary code (combination of bits 0 and 1)
	
-	consists of a number of binary inputs and a single output
	
-	In general, the number of binary inputs of a DAC will be a power of two
	
-	There are two types of DACs :
	
	-	Weighted Resistor DAC
	
		-	produces an analog output (digital (binary) input by using binary weighted resistors in the inverting adder circuit) 
	
	-	R-2R Ladder DAC
	
		-	overcomes the disadvantages of a binary weighted resistor DAC
	
		-	produces an analog output, which is almost equal to the digital (binary) input by using a R-2R ladder network in the inverting adder circuit
	
</details>

**For modelling RVMYTH (RISC-V)**

```
git clone https://github.com/kunalg123/rvmyth/

cd rvmyth

csh

vcs mythcore_test.v tb_mythcore_test.v #need to debug first

./simv

dve  -full64 &
```

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/210694741-6ab4335f-0f19-4e15-891d-431d3da82f07.png" height = "400"><img src = "https://user-images.githubusercontent.com/118953932/210694926-438c2a27-2cc7-408d-8153-005bcbd7126a.png" height = "300"></p>

**For modelling DAC**

```
git clone https://github.com/vsdip/rvmyth_avsdpll_interface

cd Pre Synthesis #pwd = /nfs/png/disks/png_mip_gen6p9ddr_0032/nurul/VLSI/sky130RTLDesignAndSynthesisWorkshop/DC_WORKSHOP/verilog_files/rvmyth/rvmyth_avsddac_interface/iverilog/Pre-synthesis 

csh 

vcs -sverilog avsddac.v avsddac_tb_test.v #need to debug first

./simv

dve  -full64 &
```
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/210907990-e69c8b34-f728-4fec-9b8d-f6a18a4294c2.png" height = "450"><img src = "https://user-images.githubusercontent.com/118953932/210722577-122aa0fd-dea8-4a3d-83ca-28c1e30f0dfd.png" height = "300"></p>

**For modelling PLL**

```
cd verilog #/nfs/png/disks/png_mip_gen6p9ddr_0032/nurul/VLSI/sky130RTLDesignAndSynthesisWorkshop/DC_WORKSHOP/verilog_files/rvmyth/rvmyth_avsdpll_interface/verilog

csh

vcs avsd_pll_1v8.v pll_tb.v #need to debug first

./simv

dve  -full64 &
```

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/210907786-92f1f1d3-6f77-46d1-a778-2fd8514dec48.png" height = "450"><img src = "https://user-images.githubusercontent.com/118953932/210726134-831016ca-e2bf-457d-bc18-daa73da9a8e4.png" height = "300"></p>


**Interface Blocks Together**

```
#risc_v and pll

cd verilog #/nfs/png/disks/png_mip_gen6p9ddr_0032/nurul/VLSI/sky130RTLDesignAndSynthesisWorkshop/DC_WORKSHOP/verilog_files/rvmyth/rvmyth_avsdpll_interface/verilog

csh

vcs -sverilog rvmyth_pll.v rvmyth_pll_tb.v #need to debug first

./simv

dve  -full64 &
```
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/210734266-4b8a048f-895d-4bd1-828f-0621abd49ad5.png" height = "450"><img src = "https://user-images.githubusercontent.com/118953932/210734026-8a7c9f72-e7db-42fa-a0e3-25564a02a7f0.png" height = "450"></p>

```
#DAC and RVMYTH

cd Pre-synthesis #/nfs/png/disks/png_mip_gen6p9ddr_0032/nurul/VLSI/sky130RTLDesignAndSynthesisWorkshop/DC_WORKSHOP/verilog_files/rvmyth/rvmyth_avsddac_interface/iverilog/Pre-synthesis 

csh

vcs -sverilog rvmyth_avsddac.v rvmyth_avsddac_TB.v #need to debug first

./simv

dve  -full64 &
```

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/210731566-f027ab69-3226-4c40-af9c-e35cd5f73fa6.png" height = "450"><img src = "https://user-images.githubusercontent.com/118953932/210731421-f25e62d4-e214-4c7b-bfc4-9814debacb2f.png" height = "450"></p>

**VSDBabySoC**

```
cd rvmyth #/nfs/png/disks/png_mip_gen6p9ddr_0032/nurul/VLSI/sky130RTLDesignAndSynthesisWorkshop/DC_WORKSHOP/verilog_files/rvmyth 
# make sure to copy the files needed in the directory

csh

vcs -sverilog vsdbabysoc.v testbench.v #need to debug first

./simv

dve  -full64 &
```

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/210907337-8e8e80a5-8093-434d-beae-db3f4b31ee9c.png" height = "450"><img src = "https://user-images.githubusercontent.com/118953932/210907449-b09f5f88-4d2c-4543-99b6-3a8a02e15791.png" height = "450"></p>

**Differences between all the modes in interactive mode**

| Debug Mode | Description |
| --- | --- |
| debug_access | Enables dumping to FSDB/VPD, and limited read/callback capability |
| debug_access+class | testbench debug |
| debug_access+all | for all debug capabilities |
| debug_region | region control |
| debug_pp | enables dumping to FSDB/VPD, and use of UCLI, VERDI and DVE |
| debug | same as debug_pp but also includes 'force' capability |
| debug_all | enables all debug and dumping capability |


**4x1 Mux**

```
cd new #/nfs/png/disks/png_mip_gen6p9ddr_0032/nurul/VLSI/sky130RTLDesignAndSynthesisWorkshop/DC_WORKSHOP/verilog_files/rvmyth/new

vcs -sverilog mux_generate.v tb_mux_generate.v

./simv

dve -full64
```
Expected:

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/210914097-0eb79c4a-00da-4abb-8247-d0cf42c09e17.png" height = "250"></p>

Result:

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/210913307-82bee9f9-b1d6-4697-8a15-be594ae43566.png" height = "450"><img src = "https://user-images.githubusercontent.com/118953932/210913015-7bea9c25-dc86-4a3f-b966-1d059723689b.png" height = "450"></p>

>	the waveform obtained is same as predicted/expected
