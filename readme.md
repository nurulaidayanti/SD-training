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

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/210917949-c28e8613-6862-4393-8c90-e6d8c7a14134.png" height = "250"></p>

Result:

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/210931164-03ccdda9-7ca8-4c5a-a864-7dda313a0f74.png" height = "450"><img src = "https://user-images.githubusercontent.com/118953932/210913015-7bea9c25-dc86-4a3f-b966-1d059723689b.png" height = "450"></p>

>	the waveform obtained is same as predicted/expected

**VSDBabySoC**

```
cd rvmyth #/nfs/png/disks/png_mip_gen6p9ddr_0032/nurul/VLSI/sky130RTLDesignAndSynthesisWorkshop/DC_WORKSHOP/verilog_files/rvmyth 
# make sure to copy the files needed in the directory

csh

vcs -sverilog vsdbabysoc.v testbench.v #need to debug first

./simv

dve  -full64 &
```

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/210907337-8e8e80a5-8093-434d-beae-db3f4b31ee9c.png" height = "450"><img src = "https://user-images.githubusercontent.com/118953932/210916145-aae0de4c-23ad-45b5-8729-94b38d4532a9.png" height = "450"></p>

# Day-13
## Post Synthesis Simulation

<details><summary>Theory 📝🤔</summary>

**What did we do in pre-synthesis?**
	
>	modelled and simulated the IP cores in VSDBabySoC(for checking its functionality) 
	

**Synthesizable and non-synthesizable constructs in verilog**
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/211314710-3dbb812a-820e-48f1-8771-ada46022e992.png" height = "450"></p>
	
**Why do pre-synthesis? Why not just do post-synthesis?**
	
-	Pre-synthesis simulation is done according to the logic you have designed for and written -> only functionality.
	
-	Post synthesis simulation / ‘gate level simulation’ is done after synthesisconsidering each and every gate delays into account. reports the violations in both functionality and timing. 
	
-	This also show’s the mismatches we are likely to get due to wrong usage of operators and inference of latches.
	
-	For ex: using ‘X’(simulator terms/ synthesizer terms) - ‘Unknown’/“Don’t care”.
	
**GLS: a brief introduction**
	
-	The term "gate level" refers to the netlist view of a circuit, usually produced by logic synthesis.
	
-	So while RTL simulation is pre-synthesis, GLS is post-synthesis. 
	
-	The netlist view is a complete connection list consisting of gates and IP models with full functional and timing behavior. 
	
-	RTL simulation is a zero delay environment and events generally occur on the active clock edge. GLS can be zero delay also, but is more often used in unit delay or full timing mode. 
	
>	Gate level simulation is used to boost the confidence regarding implementation of a design and can help verify dynamic circuit behaviour, which cannot be verified accurately by static methods. It is a significant step in the verification process.
	
**What are we going to synthesize the netlist with?**
	
Design Compiler® (dc_shell) RTL synthesis solution enables users to meet today's design challenges with concurrent optimization of timing, area, power and test.
	
</details>

<details><summary>Lab 💻🖱️</summary>

**Invoke lc_shell**
```
#create new VNC

cd /nfs/site/disks/zsc11_mip_xmphy_0021/users/nurul

git config --global http.proxy  http://proxy-dmz.intel.com:912

git clone https://github.com/manili/VSDBabySoC

#source UE setup

lc_shell
```

**Convert .lib to .db (avsddac)**
```
lc_shell> read_lib avsddac.lib #make sure in same directory or can use read_lib /nfs/site/disks/zsc11_mip_xmphy_0021/users/nurul/VSDBabySoC/src/lib/avsddac.lib

lc_shell> write_lib avsddac -format db -output avsddac.db #move to png
```
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/211263965-a1d01b21-b8b6-49b0-856e-2714fb7c6032.png" height = "500"></p>

**Convert .lib to .db (avsdpll)**
```
#debug avsdpll.lib first

lc_shell> read_lib avsdpll.lib #make sure in same directory or can use read_lib /nfs/site/disks/zsc11_mip_xmphy_0021/users/nurul/VSDBabySoC/src/lib/avsdpll.lib

lc_shell> write_lib avsdpll -format db -output avsdpll.db #move to png
```
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/211263499-11dfde38-f209-45a9-a9b1-1ef80ab4e8fc.png" height = "500"></p>
	
**Synthsize using DC**

-	rvmyth_avsddac
	
```
dc_shell> set target_library {/nfs/png/disks/png_mip_gen6p9ddr_0032/nurul/VLSI/sky130RTLDesignAndSynthesisWorkshop/DC_WORKSHOP/verilog_files/rvmyth/avsddac.db /nfs/png/disks/png_mip_gen6p9ddr_0032/nurul/VLSI/sky130RTLDesignAndSynthesisWorkshop/DC_WORKSHOP/verilog_files/rvmyth/sky130_fd_sc_hd__tt_025C_1v80.db}

dc_shell> set link_library {* /nfs/png/disks/png_mip_gen6p9ddr_0032/nurul/VLSI/sky130RTLDesignAndSynthesisWorkshop/DC_WORKSHOP/verilog_files/rvmyth/avsddac.db /nfs/png/disks/png_mip_gen6p9ddr_0032/nurul/VLSI/sky130RTLDesignAndSynthesisWorkshop/DC_WORKSHOP/verilog_files/rvmyth/sky130_fd_sc_hd__tt_025C_1v80.db}
	
dc_shell> read_verilog rvmyth_avsddac.v #need to debug avsddac and rvmyth_avsddac
	
dc_shell> read_file {rvmyth_avsddac.v avsddac.v mythcore_test.v clk_gate.v} -autoread -format verilog -top rvmyth_avsddac #to set rvmyth_avsddac as top module

dc_shell> current_design #check if rvmyth_avsddac is the top module (previous is clk_gate)

dc_shell> link
	
dc_shell> compile
	
dc_shell> write -f verilog -out rvmyth_avsddac_net.v
```
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/211520981-d0c9a04d-ccc0-404d-874d-afe6daac844a.png" height = "450"><img src = "https://user-images.githubusercontent.com/118953932/211521122-9bb4d889-9db0-4f7d-a705-d6c1f4e631f7.png" height = "300"><img src = "https://user-images.githubusercontent.com/118953932/211521262-3aca1a42-81cd-49dc-99e9-82cbee9d5047.png" height = "300"><img src = "https://user-images.githubusercontent.com/118953932/211523824-7c5d3d4b-046a-4fb7-bdfa-733501c2db44.png" height = "250"></p>
	
-	rvmyth_avsdpll
	
```
dc_shell> set target_library {/nfs/png/disks/png_mip_gen6p9ddr_0032/nurul/VLSI/sky130RTLDesignAndSynthesisWorkshop/DC_WORKSHOP/verilog_files/rvmyth/avsdpll.db /nfs/png/disks/png_mip_gen6p9ddr_0032/nurul/VLSI/sky130RTLDesignAndSynthesisWorkshop/DC_WORKSHOP/verilog_files/rvmyth/sky130_fd_sc_hd__tt_025C_1v80.db}

dc_shell> set link_library {* /nfs/png/disks/png_mip_gen6p9ddr_0032/nurul/VLSI/sky130RTLDesignAndSynthesisWorkshop/DC_WORKSHOP/verilog_files/rvmyth/avsdpll.db /nfs/png/disks/png_mip_gen6p9ddr_0032/nurul/VLSI/sky130RTLDesignAndSynthesisWorkshop/DC_WORKSHOP/verilog_files/rvmyth/sky130_fd_sc_hd__tt_025C_1v80.db}
	
dc_shell> read_file {avsd_pll_1v8.v mythcore_test.v clk_gate.v rvmyth_pll.v} -autoread -format verilog -top rvmyth_pll_interface #to set as top module

dc_shell> current_design 

dc_shell> link
	
dc_shell> compile
	
dc_shell> write -f verilog -out rvmyth_avsdpll_net.v
```
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/211700919-bedacae8-4229-4db7-bf6b-3fb6c29ba5fe.png" height = "400"><img src = "https://user-images.githubusercontent.com/118953932/211701082-9163aeee-31cb-4853-b42f-33116c13d626.png" height = "150"><img src = "https://user-images.githubusercontent.com/118953932/211701142-40a6f031-84aa-4c0b-b1a9-c7e5e6fe02af.png" height = "400"></p>
	
-	vsdbabysoc
	
```
dc_shell> set target_library {nfs/png/disks/png_mip_gen6p9ddr_0032/nurul/VLSI/sky130RTLDesignAndSynthesisWorkshop/DC_WORKSHOP/verilog_files/rvmyth/avsdpll.db /nfs/png/disks/png_mip_gen6p9ddr_0032/nurul/VLSI/sky130RTLDesignAndSynthesisWorkshop/DC_WORKSHOP/verilog_files/rvmyth/sky130_fd_sc_hd__tt_025C_1v80.db /nfs/png/disks/png_mip_gen6p9ddr_0032/nurul/VLSI/sky130RTLDesignAndSynthesisWorkshop/DC_WORKSHOP/verilog_files/rvmyth/avsddac.db}
	
dc_shell> set link_library {* nfs/png/disks/png_mip_gen6p9ddr_0032/nurul/VLSI/sky130RTLDesignAndSynthesisWorkshop/DC_WORKSHOP/verilog_files/rvmyth/avsdpll.db /nfs/png/disks/png_mip_gen6p9ddr_0032/nurul/VLSI/sky130RTLDesignAndSynthesisWorkshop/DC_WORKSHOP/verilog_files/rvmyth/sky130_fd_sc_hd__tt_025C_1v80.db /nfs/png/disks/png_mip_gen6p9ddr_0032/nurul/VLSI/sky130RTLDesignAndSynthesisWorkshop/DC_WORKSHOP/verilog_files/rvmyth/avsddac.db}
	
dc_shell> read_file {mythcore_test.v avsd_pll_1v8.v avsddac.v clk_gate.v vsdbabysoc.v} -autoread -format verilog -top vsdbabysoc
	
dc_shell> link
	
dc_shell> compile
	
dc_shell> write -f verilog -out vsdbabysoc_net.v
```
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/211742484-74a56f4a-c0f9-472e-aded-cd0b14023aea.png" height = "350"><img src = "https://user-images.githubusercontent.com/118953932/211742668-ce245479-c80b-43e5-b2e6-4d4fd5ce303f.png" height = "300"><img src = "https://user-images.githubusercontent.com/118953932/211742771-74d0b70e-a248-45ba-9657-42a6a340ecf6.png" height = "400"></p>
	
	
</details>


# Day-14
## Sypnosys DC and Timing Analysis

<details><summary>Theory 📝🤔</summary>

**Corners of PVT (Process, Voltage and Temperature)**

-	Integrated circuits are designed in such a way that they can function in a wide variety of temperatures and voltages, rather than a single temperature and voltage.
-	In order to make our chip to work after fabrication in all the possible conditions, we simulate it at different corners of process, voltage, and temperature.
-	These conditions are called corners. All these three parameters directly affect the delay of the cell.

**Understanding PVT**

-	Process: There are millions of transistors on the single-chip as we are going to lower nodes and all the transistors in a chip cannot have the same properties. Process variation is the deviation in parameters of the transistor during the fabrication.
-	Voltage : As we are going to the lower nodes the supply voltage for a chip is also going to less. Let’s say the chip is operating at 1.2V. So,there are chances that at certain instances of time this voltage may vary.
-	Temperature: When a chip is operating, the temperature can vary throughout the chip. This is due to the power dissipation in the MOS-transistors.

**PVT Graphs**

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/211749332-4aa65ec6-9e69-43fa-935e-4cb148721fc7.png" height = "300"></p>
	
>	we can know which is the best case scenario and worst case scenario based on the graphs

</details>

<details><summary>Lab 💻🖱️</summary>

**Change .lib to .db**
	
-	use lc_shell
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/211970269-df7ac5ca-81a0-4913-aa57-aa9ea9c66bd6.png" height = "250"><img src = "https://user-images.githubusercontent.com/118953932/211970378-fb7c0374-e5a6-41e5-aa4e-0e9bb6ff8109.png" height = "300"></p>

**.db file created**
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/211970088-820f8b73-53d7-41c8-a2e2-1ce3859f5da7.png" height = "100"></p>
	
**Timing libs for different PVT corners**
	
```
#dc_shell
	
read_file {mythcore_test.v avsd_pll_1v8.v avsddac.v clk_gate.v vsdbabysoc.v} -autoread -format verilog -top vsdbabysoc

set target_library {/nfs/png/disks/png_mip_gen6p9ddr_0032/nurul/VLSI/sky130RTLDesignAndSynthesisWorkshop/DC_WORKSHOP/verilog_files/rvmyth/timing_libs/sky130_fd_sc_hd__ff_100C_1v65.db /nfs/png/disks/png_mip_gen6p9ddr_0032/nurul/VLSI/sky130RTLDesignAndSynthesisWorkshop/DC_WORKSHOP/verilog_files/rvmyth/avsddac.db /nfs/png/disks/png_mip_gen6p9ddr_0032/nurul/VLSI/sky130RTLDesignAndSynthesisWorkshop/DC_WORKSHOP/verilog_files/rvmyth/avsdpll.db}
	#change target and link library
	
set link_library {* /nfs/png/disks/png_mip_gen6p9ddr_0032/nurul/VLSI/sky130RTLDesignAndSynthesisWorkshop/DC_WORKSHOP/verilog_files/rvmyth/timing_libs/sky130_fd_sc_hd__ff_100C_1v65.db /nfs/png/disks/png_mip_gen6p9ddr_0032/nurul/VLSI/sky130RTLDesignAndSynthesisWorkshop/DC_WORKSHOP/verilog_files/rvmyth/avsddac.db /nfs/png/disks/png_mip_gen6p9ddr_0032/nurul/VLSI/sky130RTLDesignAndSynthesisWorkshop/DC_WORKSHOP/verilog_files/rvmyth/avsdpll.db}

get_clocks #to check if clock exist

source cons.tcl #constraints

report_clocks #check clock

link

compile

report_timing #to look at the slack

report_qor #to get the WNS WHS THS

```

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/211953192-6071abb0-4ea2-4ec1-a627-84d34e2e92dc.png" height = "350"><img src = "https://user-images.githubusercontent.com/118953932/211953405-8f3902e6-db7c-4ab9-b350-50d47000d2aa.png" height = "220"><img src = "https://user-images.githubusercontent.com/118953932/211953485-03aa30de-7029-460c-922e-8eca4af98c80.png" height = "300"><img src = "https://user-images.githubusercontent.com/118953932/211976292-dc65205c-c5ac-4905-b63d-038037291aa2.png" height = "400"></p>
	
**Results**
	
| PVT Corners | WNS | WHS | THS |
| --- | --- | --- | --- |
| ff_100C_1v65 | 0.10 | 0.15 | 87.96 |
| ff_100C_1v95 | 0.00 | 0.20 | 222.95 |
| ff_n40C_1v56 | 0.47 | 0.11 | 12.00 |
| ff_n40C_1v65 | 0.17 | 0.14 | 64.88 |
| ff_n40C_1v76 | 0.02 | 0.18 | 141.85 |
| ss_100C_1v40 | 4.40 | 0.00 | 0.00 | 
| ss_100C_1v60 | 2.64 | 0.00 | 0.00 |
| ss_n40C_1v28 | 12.54 | 0.00 | 0.00 |
| ss_n40C_1v35 | 8.10 | 0.00 | 0.00 |
| ss_n40C_1v40 | 6.73 | 0.00 | 0.00 |
| ss_n40C_1v44 | 5.79 | 0.00 | 0.00 |
| ss_n40C_1v76 | 1.93 | 0.00 | 0.00 |
| tt_025C_1v80 | 0.64 | 0.09 | 9.07 |

>	WNS is worst negative slack of timing path (difference between the clock period and the delay between a pair of registers) where TNS is the total negative slack, which is the sum of all WNS in design. THS is total hold slack which is sum of negative hold path slack in design.
	
</details>

# Day-15
## Sky130 Day 1 - Inception of open-source EDA, OpenLANE and Sky130 PDK
<details><summary>SKY130_D1_SK1 - How to talk to computers</summary>

**SKY_L1 - Introduction to QFN-48 Package, chip, pads, core, die and IPs**
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/212085331-25e1be1f-51c1-4b61-954c-243a7ff03f6d.png" height = "450"></p>

-	Wire bonds = connect pins to the boundary of the chip which makes it able to transfer all the signal from the outside to the interior of the chip (interconnections of the IC (die) to its packaging)


-	Pads = can send the signal from inside the chip to the outside (vice versa)

-	Core = where the digital logics are placed

-	Package = container that holds the semiconductor die. It protects the die from potential damage and connects the chip to a board or other chips.
	
-	Foundry IP's = cell with more specific functionality and the design was patent/owned by a company. all Intellectual Property, whether Background IP or Foreground IP, regardless of when or for what purpose it is developed, pertaining to genetic components, pathways, and strains; and methods and tools for design, genetic engineering, testing and/or small-scale fermentation of microbial strains (need to continuously communicate with it)
	
-	Macros = pure digital logic (a simple core/cell with simple functionality and can be easily found online)
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/212085681-a2a5d750-5e5b-4bec-a17d-7556b5ac101b.png" height = "350"><img src = "https://user-images.githubusercontent.com/118953932/212087538-d3642818-9766-4dec-8009-e343f3878e57.png" height = "350"></p>
	
<p align="center">**IMAGES ARE TAKEN FROM LECTURES**</p>
	
**SKY_L2 - Introduction to RISC-V**
	
-	way to talk to the computer (want to pass informations to the hardware in certain terms)
	
-	C program compile in RISC-V assembly language program. This assembly program is then converted into machine language program (binary language program which means that the program need to converted into binary format) then bits get executed in the layout.
	
-	need to create or implement the risc-v specification using RTL. from RTL to layout
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/212093419-f6726a10-4fdf-45d4-ba3d-c4269fad4b75.png" height = "350"></p>

<p align="center">**IMAGE ARE TAKEN FROM LECTURES**</p>
	
>	RISC-V -> RTL -> Layout
	
**SKY_L3 - From Software Applications to Hardware**
	
Apps -> System Software -> Hardware
	
-	OS

Take apps and convert it into respective assembly language program and to binary language program
	
-	Compiler
	
High Level language taken by compiler and convert into respective language or instructions (instructions are based on what the hardware is)
	
-	Assembler
	
Take the instruction and convert into binary numbers (machine language program) Binary language will then be fed to the hardware
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/212099712-a52d4c4a-96c7-4125-9d68-c9b16201691b.png" height = "310"><img src = "https://user-images.githubusercontent.com/118953932/212100305-1249a36a-0471-4a69-a8b4-f1d5bdb37697.png" height = "310"></p>
	
<p align="center">**IMAGES ARE TAKEN FROM LECTURES**</p>
	
>	RTL (spesification or instruction) -> Synthesize Netlist (gate level) -> Hardware (physical design implementation of the netlist)
	
</details>

<details><summary>SKY130_D1_SK2 - SoC design and OpenLANE</summary>
	
**SKY_L1 - Introduction to all components of open-source digital asic design**

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/212212766-53ffaa75-1153-4aeb-870b-d0e9b69961f3.png" height = "350"></p>
	
RTL IP'S
-	Hardware description language (function that want to be implement)_
	
EDA TOOLS
-	Electronic design automation
	
PDK (Process Design Kit)
-	The interface between the FAB and the designers
-	Collection of files used to model a fabrication process for the EDA tools used to design an IC
	-	Process Design Rules: DRC, LVS, PEX
	-	Device Models
	-	Digital Standard Cell Libraries
	-	I/O Libraries

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/212212966-4be46e5a-f87f-4343-ab65-f36bcca1c52a.png" height = "300"></p>
	
<p align="center">**IMAGE IS TAKEN FROM LECTURE'S**</p>
	
>	several application do not need the advance performance. Hence why 130nm is still used. it is also cheaper
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/212215158-ad267574-e61e-4a3b-950a-04d1cd4bb334.png" height = "350"></p>
	
<p align="center">**IMAGE IS TAKEN FROM LECTURE'S**</p>

*ASIC Design Flow*
	
-	ASIC Flow Objective: RTL to GDSII (take design from resistor transfer level to GDSII format for the final layout)
	-	also called as Automated PnR and/or Physical Implementation

**SKY_L2 - Simplified RTL2GDS flow**
	
*Simplified RTL to GDSII Flow*
-	Synthesis
-	Floor/Power Planing
-	Placement
-	Clock Tree Synthesis
-	Routing
-	Sign off
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/212217452-55c99d98-a1c7-4e12-8cc0-4f07aa970751.png" height = "300"></p>
	
*Synthesis*
-	converts RTL to a circuit out of components from the standard cell library (SCL) 
-	result of circuit is described in HDL or gate level netlist
-	"standard cells" have regular layout	
	-	each cells has different views/models
		-	Electrical, HDL, SPICE
		-	Layout (Abstract and Detailed)

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/212217125-9b8c423f-d407-40ef-b806-374f9077d34f.png" height = "250"></p>
	
*Floor and power planing*
	
-	objective is to plan the silicon area and create robust distribution to power the circuit
	
-	chip floor-planning: partition the chip die between different system builing blocks and place the I/O Pads
	
-	macro floor-planning: dimensions, pin locations, rows definition
	
-	power planning: power net is constructed
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/212225350-99de632a-8340-406a-bf74-ed85031338fe.png" height = "250"></p>
	
*Placement*
-	place the cells on the floorplan rows, aligned with the sites 
-	usually done in 2 steps:
	-	global = try to find optimal positions for all cells but such placement are not necessarily legal which means some cells may overlapped
	-	detailed = position obtained from global placement are minimally altered to be legal
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/212226224-d8afae2e-96dc-4f83-9485-99c06eef665a.png" height = "250"></p>
	
*Clock Tree Synthesis*
-	create a clock distribution network (routing the clock)
	-	to deliver the clock to all sequential elements (eg: FF)
	-	with minimum skew 
	-	all in good shape
	-	usually a Tree (H, X, ...)
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/212228414-54f71fab-87ce-4127-8175-1dd687ea51eb.png" height = "150"></p>

_Routing (signal routing)_
	
-	implement the interconnect using available metal layers (implement nets to connect the cells together) 
-	metal tracks from a routing grid
-	routing grid is huge
-	divide and conquer
	-	global routing = generates routing guides
	-	detailed routing = uses the routing guides to implement the actual wiring
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/212228909-c40c0c04-c19f-4ab1-9a94-fbc7063b932b.png" height = "200"></p>
	
_Sign Off_
-	physical verifications
	-	design rules checking (DRC) - make sure the final layout follows the design rule
	-	layout vs schematic (LVS) - make sure the final layout matches the gate level netlist that was sourced with
-	timing verification
	-	static timing analysis (STA) - make sure all time constraints are met and circuit will run at degsinated clock frequency
	
**SKY_L3 - Introduction to OpenLANE and Strive chipsets**

OpenLANE
-	started as an Open-Source Flow for a True Open Source Tape-out Experiment
-	striVe is a family of open everything SoCs
	-	Open PDK, Open EDA, Open RTL
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/212252178-d6e148be-e961-4a02-b74b-5aea0aecfad1.png" height = "180"><img src = "https://user-images.githubusercontent.com/118953932/212252441-db8c1f90-5a8a-453a-9cb2-792a41c9b254.png" height = "250"></p>
	
-	Main Goal:
	-	Produce a clean GDSII with no human intervention (no-human-in-the-loop)
	-	Clean means:
		-	no LVS violations
		-	no DRC violations
		-	no Timing Violations
-	Tuned for SkyWater130nm Open PDK
	-	also, supports XFAB180 and GF130G
-	Containerized
	-	functional out of the box
	-	instructions to build and run natively will follow
-	can be used to harden (generate GDSII on the final layout) Macros and Chips
-	2 modes of operations:
	-	Autonomous = push button flow 
	-	Interactive = run commands and steps one by one (can do experimentation and check results)
-	Design Space Exploration:
	-	find the best set of flow configurations
-	Large number of design examples
	-	43 designs with their best configurations
	-	more designs will be added soon

**SKY_L4 - Introduction to OpenLANE detailed ASIC design flow**
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/212255084-e2bb8575-01e8-4ff6-858b-ee0e3abdb15b.png" height = "350"><img src = "https://user-images.githubusercontent.com/118953932/212257431-4c589999-7ad7-49fa-b0e5-c7637afe752b.png" height = "200"></p>

>	from RTL to GDSII format using PDK
	

	
1)	RTL Synthesis = RTL is fed to Yosys with the design constraints. Yosys translate the RTL into logic circuits component. Optimized and then mapped using abc. 
	
2)	Synthesis Exploration = used to generate reports that shows how the design delay and area (can pick the best strategy based on this)
	
3)	DFT (optional) 
	-	Scan Insertion
	-	Automatic Test Pattern Generation (ATPG)
	-	Test Patterns Compaction
	-	Fault Coverage
	-	Fault Simulation
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/212259252-6fc089cb-00ec-4055-81e6-2bb1ea337a90.png" height = "250"></p>
	
4)	Design Exploration = generates the design configuration (useful for finding the best design configuration)
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/212258044-769d8c11-9792-42b4-bb46-279fb9fac552.png" height = "300"></p>
	
_OpenLANE Regression Testing_
	
-	the design exploration utility is also used for regression testing (CI)
	
-	run OpenLANE on ~70 designs and compare the results to the best known ones
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/212258795-f4a34086-1770-42f8-b263-9775869a8481.png" height = "300"></p>
	
>	report shows the number of violations and compared to best known results
	
5)	Physical Implementation (PnR = place and route) -> used OpenROAD app
	-	Floor/Power Planning
	-	End Decoupling Capacitors and Tap cells insertion
	-	Placement: Global and Detailed
	-	Post placement optimization
	-	Clock Tree Synthesis (CTS)
	-	Routing: Global and Detailed
	-	"Special step" = fake anntena diode insertion 
	
6)	LEC (logic equivalent checking) -> yosys
	-	everytime the netlist is modified, verification must be performed
		-	CTS modifies the netlist
		-	Post Placement optimizations modifies the netlist
	-	LEC is used to formally confirm that the function did not change after the modifying the netlist
	
7)	Antenna Rule Violations
	-	when a metal wire segment is fabricated, it can act as an antenna
		-	reactive ion etching causes charge to accumulate on the wire
		-	transistor gates can be damaged during fabrication
	-	2 solutions:
		-	Bridging attaches a higher layer intermediately
			-	requires Router awareness
		-	Add antenna diode cell to leak away charges 
			-	Antenna diodes are provided by SCL
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/212274809-2045b3cc-b274-425a-b430-a211ea899f37.png" height = "300"></p>
	
-	preventive approach
	-	add a Fake Antenna Diode next to every cell input after placement
	-	run Antenna Checker (Magic) on the routed layout
	-	if the checker reports a violation on the cell input pin, replace the Fake Diode cell by a real one (automatically inserting antenna diode when needed)
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/212277071-8075e901-9aba-41f2-bf1a-054212ac6eef.png" height = "250"></p>
	
8)	STA, DRC & LVS
	
-	RC Extraction: DEF2SPEF
-	STA: OpenSTA (OpenROAD) 
-	Magic is used for DRC and SPICE Extraction from Layout
-	Magic and Netgen are used for LVS
	-	Extracted SPICE by Magic vs. Verilog netlist
	
	
</details>

<details><summary>SKY130_D1_SK3 - Get familiar to open-source EDA tools</summary>

**SKY_L1 - OpenLANE Directory structure in detail**
	
_Change directory_
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/212283476-343ef436-21ee-414d-bf3d-36173c56ea81.png" height = "250"></p>
	
>	pdk = process design kit (will be using skywater130nm pdk)
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/212285860-bf86f753-af92-4366-b128-59fcb50c8518.png" height = "200"></p>
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/212288816-93fa4c9d-f7a5-42c4-9096-26733a8f920c.png" height = "350"></p>
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/212290670-b199462f-b1b9-4f27-bec0-196be14afec2.png" height = "200"><img src = "https://user-images.githubusercontent.com/118953932/212291601-d920bd0c-bf07-4084-995d-1cff8aa0acfa.png" height = "250"></p>
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/212291943-fff7c9bb-d1a2-4bba-97eb-9e077df639a7.png" height = "200"></p>
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/212292455-7403f423-15bc-4770-9251-c73f8b719065.png" ></p>
	
>	make sure to always work in this directory!! 
	
**SKY_L2 - Design Preparation Step**	
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/212322272-63db55d7-2f96-4d67-adf1-1ff9caf2e301.png" height = "270"><img src = "https://user-images.githubusercontent.com/118953932/212323540-5673f429-4589-4d76-bd12-9aca48a2b9ac.png" height = "270"></p>

How openLANE takes the value:
	
1.	default (already set in openlane)
	
2.	config.tcl
	
3.	sky130A....config.tcl (highest priority)
	
>	it will overwrite the configuration. eg: the clock period of all those 3 are different so the sky130..config.tcl will overwrite it
	

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/212324462-36c40957-3b5c-496d-af96-0322c5b1ce70.png" height = "150"></p>
	
_To invoke OpenLANE_
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/212332695-de7d04f0-2356-438a-b2ad-117380cf9ccd.png" height = "300"></p>

<p align="center">source: https://github.com/nickson-jose/openlane_build_script</p>

>	make mount
	
	
**SKY_L3 - Review files after design prep and run synthesis**
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/212335664-3245c29f-5465-4d4a-8885-6d689758543f.png" height = "350"></p>
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/212337620-4cb39cb6-9316-47de-9e18-26b7c3fdd2d1.png" height = "350"><img src = "https://user-images.githubusercontent.com/118953932/212338066-423999a0-3214-4bed-a1ed-ccca1efab297.png" height = "300"></p>
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/212341589-7d318dc6-9712-4e95-bf49-b5b090a1fe82.png" height = "250"></p>

open_lane

```
run_synthesis #yosys as well as abc
```
	
**SKY_L4 - OpenLANE Project Git Link Description**
	
To know more about OpenLANE and all the informations -> https://github.com/efabless/OpenLane
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/212342781-776a359a-db80-4108-a28f-9af26facdc14.png" height = "300"></p>
	
```
git clone #copy the repository to local
```
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/212344204-b2edbcc9-48c1-4ca3-8f26-4187214cc3d3.png" height = "350"></p>
	
1.	Synthesis
	-	yosys - Performs RTL synthesis
	-	abc - Performs technology mapping
	-	OpenSTA - Performs static timing analysis on the resulting netlist to generate timing reports
2.	Floorplan and PDN
	-	init_fp - Defines the core area for the macro as well as the rows (used for placement) and the tracks (used for routing)
	-	ioplacer - Places the macro input and output ports
	-	pdn - Generates the power distribution network
	-	tapcell - Inserts welltap and decap cells in the floorplan
3.	Placement
	-	RePLace - Performs global placement
	-	Resizer - Performs optional optimizations on the design
	-	OpenDP - Perfroms detailed placement to legalize the globally placed components
4.	CTS
	-	TritonCTS - Synthesizes the clock distribution network (the clock tree)
5.	Routing
	-	FastRoute - Performs global routing to generate a guide file for the detailed router
	-	CU-GR - Another option for performing global routing.
	-	TritonRoute - Performs detailed routing
	-	SPEF-Extractor - Performs SPEF extraction
6.	GDSII Generation
	-	Magic - Streams out the final GDSII layout file from the routed def
	-	Klayout - Streams out the final GDSII layout file from the routed def as a back-up
7.	Checks
	-	Magic - Performs DRC Checks & Antenna Checks
	-	Klayout - Performs DRC Checks
	-	Netgen - Performs LVS Checks
	-	CVC - Performs Circuit Validity Checks
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/212345392-3afa0e57-3f33-4623-bf30-5b619c891761.png" height = "400"></p>
	
<p align="center">**MOST IMAGES ARE TAKEN FROM GITHUB efabless**</p>
	
>	MUST RUN THE COMMANDS BE IN ORDER!!
	
**SKY_L5 - Steps to characterize synthesis results**
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/212351285-07b8a8bf-3fbe-4f4b-a140-851e052ef2ae.png" height = "400"></p>

>	flop ratio = number of D flip flop divide by total of cells -> 0.1084
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/212349055-ca818e6a-077f-4d27-a81e-2e6a054b8ca3.png" height = "400"></p>
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/212351083-05b29dde-3aa2-4805-bb9d-696fd5c8100d.png" height = "400"></p>
	
</details>

# Day-16
## Good floorplan vs bad floorplan and introduction to library cells

<details><summary>Chip Floor planning considerations</summary>
	
##### Table of Contents  
-	[Utilization factor and aspect ratio](#utilization-factor-and-aspect-ratio)
-	[Concept of pre-placed cells](#concept-of-pre-placed-cells)  
-	[De-coupling capacitors](#de-coupling-capacitors)
-	[Power planning](#power-planning)
-	[Pin placement and logical cell placement blockage](#pin-placement-and-logical-cell-placement-blockage)
-	[Review floorplan files and steps to view floorplan ⌨️🤔](#review-floorplan-files-and-steps-to-view-floorplan-%EF%B8%8F)
-	[Review floorplan layout in Magic ⌨️🤔](#steps-to-run-floorplan-using-openlane-%EF%B8%8F)


### Utilization factor and aspect ratio

Objective: to understand how to define the Width and Height core and die

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/212697249-e32f5a87-f7c7-4330-b9b5-4461223182fd.png" height = "300"></p>

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/212700298-778af0ae-7f7c-449a-85ac-31c973bdc6b4.png" height = "300"><img src = "https://user-images.githubusercontent.com/118953932/212700815-a9e69adc-5e77-4ec8-bb1e-267b4c775bcd.png" height = "300"></p>	

>	convert the logics into physical dimension (want to find out dimension of the standard cells)
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/212702647-fe8ffb8d-c4e7-4549-88e2-62e1777da471.png" height = "350"></p>
	
>	assume both standard cell and flip flop has the area of 1 sq. unit. So the total area (length and width) is going to be 4 sq.unit [(length = 1+1) x (width = 1+1)] This is the minimum area occupied by the netlist.
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/212914263-45ee84d1-111b-4331-a30b-764c7a061e8c.png" height = "300"></p>
	
>	the logics/circuit are placed in the core (which will not exceed) and the die capsulated the core. The die is imprinted multiple time in the silicon wafer.
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/212914958-0c60da9f-b787-4e6f-9b6d-1425407e17cd.png" height = "250"></p>
	
1.	The netlist occupied the area of the core completely (100% ultilization) 
2.	Utilization factor = (area occupied by netlist) / (total area of the core) so no extra cell is allowed!!! 
3.	In practical scenario we go for 50-60% utilization.
4.	Aspect Ratio = Height (core) / Width (core) (if it's =1, it means the chip is a square shape. If not then are still some spaces for other cells)
	
>	Utilization Factor & Aspect Ratio!!
	
### Concept of pre-placed cells
	
**Another example on calculating utilization factor and aspect ratio**
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/212920464-8e773141-9062-4ce1-94de-34478465ac4d.png" height = "350"></p>
	
>	the space available can be use for routing and add on other cells
	
**Prepaced Cells**
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/212927885-4f7bef0e-e76e-423d-b467-fae04524e21b.png" height = "400"></p>
	
>	Blocks will be implemented separately. The advantage is when user want to use it multiple times on the netlist to perform some function,  we can just give the block (black box) to some user. Dont need to implement multiple times, can just reuse (instantiated multiple times onto the netlist)
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/212929444-81abe615-2d41-480b-8f08-6296e413302c.png" height = "200"></p>
	
-	the arrangement of these IP's in a chip is referred as Floorplanning
-	these IP's/blocks have user-defined locations, and hence are placed in chip before automated placement-and-routing and are called as pre-placed cells
-	automated placement and routing tools places the remaining logical cells in the design onto chip
	
**Location of Preplaced Cells**
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/213053207-6f0ead8f-2f2a-46f2-907d-9a98da5c0cfb.png" height = "300"></p>
	
>	know the blocks are communicating with what pins (input or output?) and placed them near the pins. Once they are placed, the location cant be moved. That's why the location of the preplaced cell have to be well define

### De-coupling capacitors
	
**Surround preplaced cell with Decoupling Capacitor**
	
_Decoupling Capacitor_
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/213056086-3feb83fb-5b50-43dd-91f2-514eb77a4f6a.png" height = "230"><img src = "https://user-images.githubusercontent.com/118953932/213056247-1b7be2c0-dbbc-41c4-a8f7-2c8826b89589.png" height = "230"></p>
	
>	the transition need to be within noise margin range
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/213056788-21d20ecb-bcf0-4bc4-bcca-830b0b09c2ae.png" height = "300"></p>
	
>	the undefined region is a dangerous case as it can go to either logic 0 to 1 (cant guarantee we will get the logic that we want)
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/213063146-59f39176-74e8-4acf-8791-eeac95e4a45d.png" height = "300"></p>
	
>	Decoupling capacitor = huge capacitor which fills with charge (supply the same voltage as the power supply)
	
-	the circuit will get the current from the decoupling capacitance and there will be hardly any voltage drop as they are close to each other
	
-	whenever there is a switching activity, the Cd will loses some amount of charge to the circuit. It will stores it owns charge (gets from the main supply) when there is no switching activity
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/213064528-bfaf7576-3e8c-4d5d-8efd-ca14e6abcafa.png" height = "300"></p>
	
>	the blocks will behave as it should be. The local communication has been taken care of.
	
### Power planning
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/213071968-46e9db96-dab2-4df4-baad-a65bfe26d3ed.png" height = "300"></p>
	
>	orange path need to maintain the signal. It is supply by the power supply because there's no decoupling capacitor. Hence, there is possibilty there will be a voltage drop. 
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/213073298-1a4e8362-abe0-4e0c-bb8e-2cfbc328d8e8.png" height = "300"></p>
	
>	logic 1 = capacitor being charge to VDD, logic 0 = capacitor discharge to ground
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/213074303-fc1ed832-8a1a-4162-bd72-74702a2e2fbe.png" height = "230"><img src = "https://user-images.githubusercontent.com/118953932/213074491-38f9ade2-5e86-42ed-9d60-3cf25ef6a3a7.png" height = "230"></p>
	
>	if the size of ground bounds/ voltage drop exceed the noise margin level, it might enter the undefined state. The problem is the supply is only at one point (single source).
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/213075119-edc337ba-928a-4411-aa2e-9a8b35bb62bd.png" height = "300"></p>
	
>	solution: multiple power supplies. so it will take the current from the nearest power supply or drop the current to the nearest ground
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/213075499-84d9dbc7-1f97-48bc-8e3c-c39beaadea88.png" height = "300"></p>
	
>	power meshes
	
### Pin placement and logical cell placement blockage
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/213078787-de697c53-44e5-4cab-a98f-4d4c6246db72.png" height = "230"><img src = "https://user-images.githubusercontent.com/118953932/213078977-50c6bb0c-948c-4c77-a04e-ae37da26cd95.png" height = "230"><img src = "https://user-images.githubusercontent.com/118953932/213079178-68c3660d-689f-4ee4-a5be-2897c803f5b4.png" height = "230"></p>
	
>	can merged the clock ports as the 2 sets of circuits are using the same port

	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/213079694-e018c853-64d2-4d75-bd08-63a87bd959e6.png" height = "300"></p>

-	the pins placement is done 
	
>	the size of the clock ports are bigger than the data ports because the clock ports continuosly sending signals to all the flip flops in the design (drives the ff to the complete chip). Hence, they need the least resistance path for the clock (the bigger the size, the least the resistance)
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/213080895-6ce36bab-6fcd-481c-9aad-37cbef6e9b09.png" height = "300"></p>
	
-	make sure none of the automated placement or routing tool doesnt cells in the area between core and die (the pins)
	
>	the area should be block for any placement and routing tool using some blockage

### Steps to run floorplan using OpenLANE ⌨️🤔
	
```
pwd

#/home/nurul.aidayanti.muhammad.saleh/Desktop/work/tools/openlane_working_dir/openlane/configuration
	
less README.MD
```
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/213086128-58455da8-ee78-4d69-9e76-6f5da7114077.png" height = "250"></p>

>	can see each variable which are required for each stage. it need to be set
	
```
pwd
	
##/home/nurul.aidayanti.muhammad.saleh/Desktop/work/tools/openlane_working_dir/openlane/
	
less floorplan.tcl
```
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/213099964-f0893fd4-3202-4b06-9c7c-03116210c485.png" height = "230"><img src = "https://user-images.githubusercontent.com/118953932/213100135-2bdda134-0071-4422-b487-c8e1269c48a0.png" height = "230"></p>
	
>	system default settings
	
-	the lowest priority: system default (floorplan.tcl)
-	second priority: config.tcl (in openlane/designs/picorv32a) (will overwrite the system default)
-	first: sky130A.....config.tcl (in openlane/designs/picorv32a) (overwrite the others)
	
```
#in the openlane
	
run_floorplan
```
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/213102089-409542cc-4693-4122-803b-649d5aec89c8.png" height = "300"></p>
	
>	run successful
	
### Review floorplan files and steps to view floorplan ⌨️🤔
	
```
pwd

#/home/nurul.aidayanti.muhammad.saleh/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs
	
less config.tcl #configuration of the current flow/run
	
cd /home/nurul.aidayanti.muhammad.saleh/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/<current date and time>/results/floorplan
	
less picorv32a.floorplan.def #def file
```
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/213105042-72692fc2-eb17-4075-a02a-d0495ffef0af.png" height = "300"></p>
	
### Review floorplan layout in Magic ⌨️🤔
	
```
magic -T /home/nurul.aidayanti.muhammad.saleh/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.floorplan.def &
	
press s to select and v to fit the layout on the screen
```
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/213110778-fcec14ab-29e5-4e70-9cd4-ebd0cd1f6da0.png" height = "300"></p>
	
```
left click then right click (create a box of the area) then z to zoom in
	
move cursor to the wanted cell/others and press s
	
#tkcon
% what
```
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/213111995-7527898c-6bbd-4951-a083-43b1802d640e.png" height = "300"></p>
	
>	metal layer 3 (which we set for the horizontal)
	
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/213113231-c3367ec2-31e5-4c14-bfec-93e06b426089.png" height = "300"></p>
	
>	vertical
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/213114129-dee8b6b5-9fb2-4b68-b57d-0ff17525e1d1.png" height = "230"><img src = "https://user-images.githubusercontent.com/118953932/213114395-e28be675-58d5-491d-9b4e-ae020f764bdf.png" height = "230"></p>
	
>	tap cells (left) - the distance of the tap cells are set & end cap cells (right)
	
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/213115464-2ee7a0f4-f56b-4f6b-858b-43cc7d9dc1c9.png" height = "300"></p>
	
>	standard cells that are not placed yet and will be placed during placement stage
	
	
</details>
	
<details><summary>Library Binding and Placement</summary>
	
##### Table of Contents  
-	[Netlist binding and initial place design](#netlist-binding-and-initial-place-design)
-	[Optimize placement using estimated wire-length and capacitance](#optimize-placement-using-estimated-wire-length-and-capacitance)
-	[Need for libraries and characterization](#need-for-libraries-and-characterization)  
-	[Congestion aware placement using RePlAce ⌨️🤔](#congestion-aware-placement-using-replace-%EF%B8%8F)

	
### Netlist binding and initial place design
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/213121230-b5ced5a7-6523-4fe7-bbc3-f370b0b84f18.png" height = "230"><img src = "https://user-images.githubusercontent.com/118953932/213120745-9835a020-1be3-4bd2-8789-5a65470b1df5.png" height = "230"></p>
	
>	in reality it shapes like a box. physical dimension (width and height)
	
-	all of the informations of the components are available in the library. various flavour in the library (width, height, condition, etc.)
	
-	the bigger the cell size, the faster it is (lesser delay)

	
### Optimize placement using estimated wire-length and capacitance
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/213152965-db9a747d-675c-4f26-a7ef-f4edc61c2602.png" height = "300"></p>
	
>	placement (need to think about the huge delay when placing the cells. so, put nearer to the pin) (minimum delay for the one that is placed near)	

	
**Optimize placement**
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/213154954-ed824cd6-e514-45b8-b7a6-50eda2c87f68.png" height = "300"></p>
	
>	capacitance sufficient enough for the signal to maintain integrity (signal between 2 components). Hence, no need repeaters
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/213154633-23df1655-b42f-4ffd-b026-803c78222b2a.png" height = "300"></p>
	
>	in order to reproduce the signal Din2 has send, repeaters (buffer) inserted due to the distance between Din2 and the flip flop is quite large which can cause delay. Hence, it will now have minimum delay after inserted repeaters
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/213159233-412f10bd-6122-43cf-9197-72f068d83b66.png" height = "300"></p>
	
>	repeaters added to maintain signal integrity
	
<p align="center"><img src = "" height = "300"></p>
	
>	in different layers (the signal connection from 1 to 2 will be on seperate layer)
	
Check if it's correct or not
-	check the data path (considering the clock is ideal)
-	based setup timing analysis (specification), we will know the placement is reasonable or not

### Need for libraries and characterization

**Library characterization and modelling**

1.	Logic synthesis  
	
	-	convert the functionality (in the form of RTL) into a legal hardware
	-	output: arrangement of gate that will represent the original funtionality that was describe using RTL
	
2.	Floorplanning
	
	-	import the output of the logic synthesis (netlist) and decide the size of the core and the die. the size is dependent on the amount of gate and shape and sizes of the gates present output of the logic synthesis.
	
3.	Placement
	
	-	the logic cells placed on the chip.
	
4.	CTS (clock tree synthesis)
	
	-	flip flops received the clock at the same time
	-	take care of the clock signal reaching at each and every clock end points
	-	the buffers take care the clock signal has equal rise and fall time
	
5.	Routing
	
	-	certain properties of the cells needs to be take care while routing from one point to another point
	
6. Static Timing Analysis (sign off timing analysis)
	
	-	want to see setup time, hold time, data arrival time/data required time

### Congestion aware placement using RePlAce ⌨️🤔
	
**There are 2 plcaments which are global placement and detail placement**
	
-	global
	-	no legalization happening
	-	reducing wire length
	
-	detail
	-	legalization occurs (more on timing point of view)
		-	standard cells are placed inside the rows and no overlaps
	
```
#in openlane

run_placement 
	
#in pwd 

cd /home/nurul.aidayanti.muhammad.saleh/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/<current date and time>/results/placement
	
magic -T /home/nurul.aidayanti.muhammad.saleh/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.placement.def &
```
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/213190869-10495ef7-06bd-4ba7-b0ba-dd4a85c131bb.png" height = "250"><img src = "https://user-images.githubusercontent.com/118953932/213191576-f46690d4-b716-4b22-a258-20fae11d1b6b.png" height = "250"></p>
	
>	placement of the standard cell

</details>
	
<details><summary>Cell design and characterization flows</summary>
	
##### Table of Contents 
-	[Inputs for cell design flow](#inputs-for-cell-design-flow)
-	[Circuit design step](#circuit-design-step)
-	[Typical characterization flow](#typical-characterization-flow)
	
### Inputs for cell design flow	

Library is a place where all the standard cells are kept

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/213193251-55c08736-0f2a-4036-bdc5-7dde0a7ee112.png" height = "300"></p>
	
>	in the library there are different cells with different functionality and also different sizes (drive strength), variety of threshold voltage (Vt)

Inputs in the system	

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/213197863-2b266333-b191-4770-902a-99ca349021ff.png" height = "300"></p>
	
>	the design rule (input gets from the foundry = DRC & LVS rules)
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/213198714-7fb8b1f9-4d27-4893-b81e-fecb3f94204c.png" height = "300"></p>
	
>	Spice models file (foundry parameter) for example parameter for nmos, pmos
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/213200317-28b27cd5-b5fa-4d7b-b36b-5df0f7410db7.png" height = "300"></p>
	
>	library & user-defined specs = cell height, supply voltage, metal layer, pin location, drawn gate-length
 
### Circuit design step
		
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/213201094-8d2d9b19-428c-44e6-afc1-d4b6d8cc4e2d.png" height = "300"></p>

1.	implement the function
2.	model PMOS and NMOS transistors in order to meet the library requirement
3.	once have the values of W/L of the mos, the values in the layout will be implement 
4.	typical output obtain from circuit design is the CDL (circuit description language)
	
>	Circuit design

Layout design step
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/213202295-9548be43-6cc7-4130-9977-87bf8b5d1004.png" height = "250"><img src = "https://user-images.githubusercontent.com/118953932/213204050-90ecb6d0-d501-4bd9-b267-cc1c5c3a530a.png" height = "250"></p>
	
1.	function implemented through a mos transistor (pmos and nmos)
	
2.	get the pmos and nmos network graphs (derive)
	
	
3.	obtain the euler’s path (path being traced only once)
	
4.	draw a stick diagram based on the euler's path
	
5.	convert stick diagram into a layout (based on from the input that we got (from the foundry))
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/213205187-98746166-e52e-4f6a-9cd2-dd532d513116.png" height = "200"></p>
	
>	layout

6.	extract the parasitics of this layout and characterize it in terms of timing
	
	-	characterization can help get the timing, noise and power information
	
	-	outputs of the cell design flow will be the CDL (circuit description langauge), GDSII, LEF, extracted spice netlist (.cir) , timing, noise, power .libs, function
	
### Typical characterization flow   
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/213209713-eb91ce86-6c8f-4835-9a74-36705db9a1cb.png" height = "250"><img src = "https://user-images.githubusercontent.com/118953932/213209550-360f8507-6085-4079-ab93-481cf3082b00.png" height = "250"></p>
	
1.	read in the models and the tech file from the layout
	
2.	read in the extracted spice netlist
	
3.	define or recognize the behaviour of the buffer
	
4.	read in the subcircuit of the inverter
	
5.	attach the necessary power sources
	
6.	apply the stimulus

7.	provide the necessary the output load capacitance
	
8.	provide the necessary simulation command
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/213210226-b83375b9-4999-4789-a7be-cdd84e7c37a1.png" height = "200"></p>
	
>	feed all the inputs in a form of configuration file through the characterization software called as GUNA
	
</details>
	
<details><summary>General timing characterization parameters</summary>
	
##### Table of Contents 
-	[Timing threshold definitions](#timing-threshold-definitions)
-	[Propagation delay and transition time](#propagation-delay-and-transition-time)

### Timing threshold definitions   
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/213327576-e57b0501-bfc3-4f88-bd85-f788a76bde97.png" height = "300"></p>
	
Slew low rise threshold - taken waveform from the output of the first inverter which being given the input for the second inverter
-	need to define the value (points towards the lowest of the power supply and typical value is 20% or 30%)
	
>	red = input of the second inverter | blue = output of the first inverter
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/213328182-f11c7e57-a2bb-4a09-9138-ed70a17a1d76.png" height = "300"></p>
	
Slew high rise threshold - 20% from the bottom power supply and 20% from the top. then identify the time difference
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/213328418-3a9c7b1a-d884-4c20-9643-6e244aaac171.png" height = "230"><img src = "https://user-images.githubusercontent.com/118953932/213328296-a3b24299-2969-4fb7-bb32-07faeaf4836e.png" height = "230"></p>
	
>	Slew low fall threshold (left) Slew high fall threshold (right)
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/213328728-2070d8f0-2f09-413e-9244-0b2851e805b1.png" height = "230"><img src = "https://user-images.githubusercontent.com/118953932/213328944-3ac49915-43d5-4056-a0ff-036e1153b7c7.png" height = "230"></p>
	
in rise threshold - threshold for the delay (50% of the slew waveform on the ideal waveform and a point in the output waveform to calculate the delay)
	
out rise threshold - the output rising waveform (point where can calculate the delay = 50%)
	
>	red = ideal (the one we are applying) | blue = output of the buffer
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/213329495-1492679d-6b51-4430-ac81-78354b17f56e.png" height = "230"><img src = "https://user-images.githubusercontent.com/118953932/213329589-24b1f4cc-8c6b-4064-a1e8-007c8dbbf2b9.png" height = "230"></p>
	
in fall threshold = same as in rise but falling waveform
	
out fall threshold = same as in rise but out fall
	
### Propagation delay and transition time

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/213329998-ffd75471-35da-488b-ad04-a2a992843608.png" height = "300"></p>
	
>	to calculate the delay, only need to subtract out minus in
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/213330174-c96afa5f-dce3-4dd2-ab24-16eca1474c41.png" height = "300"></p>
	
>	example for calculating delay
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/213330374-b39b7c39-e331-4ee3-b0e5-cebb66c7ff7c.png" height = "300"></p>
	
>	If the threshold moves, there will be a problem which is output comes before of input (poor choice of threshold point)
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/213330678-7bf2e0b9-6db9-4460-abfd-0ea16b44d24b.png" height = "230"><img src = "https://user-images.githubusercontent.com/118953932/213330864-3ca22c9e-419b-44e1-9786-e2a9f7c2615e.png" height = "230"></p>
	
>	from the waveform, the delays on the input wires are quite high. it is due to the design (thats why circuit design is important)
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/213331356-ff8b8c7b-f2d0-4c7c-8c49-4dd09e76f931.png" height = "300"></p>
	
>	for transition time, the time of slew high rise thr need to subtract the time of slew low rise thr for rise waveform (also applies for the fall waveform, using the slew low and high for fall)

Note: always high minus low

</details>
	
# Day-17
## Design library cell using Magic Layout and ngspice characterization

<details><summary>Labs for CMOS inverter ngspice simulations</summary>
	
##### Table of Contents 
	
-	[IO placer revision](#io-placer-revision)
-	[SPICE deck creation for CMOS inverter](#spice-deck-creation-for-cmos-inverter)
-	[SPICE simulation lab for CMOS inverter](#spice-simulation-lab-for-cmos-inverter)	
-	[Switching Threshold Vm](#switching-threshold-vm)
-	[Static and dynamic simulation of CMOS inverter](#static-and-dynamic-simulation-of-cmos-inverter)
-	[Lab steps to git clone vsdstdcelldesign](#lab-steps-to-git-clone-vsdstdcelldesign)


	
### IO placer revision
	
**Change on openlane flow**
	
```
pwd
#/home/nurul.aidayanti.muhammad.saleh/Desktop/work/tools/openlane_working_dir/openlane/configuration
	
less floorplan.tcl #read the configuration = currently IO mode is set to 1
```
	
```
#openlane
	
set ::env(FP_IO_mode) 2 #set IO mode to 2
	
run_floorplan
```
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/213392105-f6b8debc-de4e-4eab-b0da-a01f3a6a922d.png" height = "300"></p>
	
>	change the IO mode
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/213392322-8e9b7adc-c87c-468f-b689-b27dd13da970.png" height = "300"></p>
	
### SPICE deck creation for CMOS inverter
	
**SPICE deck**
	
-	Connectivity information about the netlist
	
1.	create SPICE deck (for the complete netlist)
	-	need to define the connectivity of substrate (potential component/pin of transistor)
	-	the value of the output load capacitance decided by the input capacitances of the circuit which is connected at the cload point
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/213395961-c2e32555-9a5a-47ee-8d1c-c79450c3d788.png" height = "250"></p>
	
>	substrate terminal of PMOS and NMOS

	
-	Component value
	
1.	define the value of channel length and load capacitance
		
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/213400117-615c566c-ea06-41ae-82b9-288d337706de.png" height = "250"></p>

>	channel length = read (ideally PMOS should be twice or thrice bigger than NMOS) and output load = blue
	
2.	define value of input and supply voltage
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/213401772-72f7bc17-ed69-4035-af6e-beb8ab094879.png" height = "250"></p>
	
>	2.5 V because the channel length is 2.5nm
	
-	Identify 'nodes'
	
	-	nodes = two points which there are components (eg; the component lies between 2 nodes)
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/213402642-e6e46575-f216-47ca-9eaf-a70dfb3d5c70.png" height = "250"><img src = "https://user-images.githubusercontent.com/118953932/213402975-83a399ee-5bfb-4728-a94b-cf0a38c38cec.png" height = "250"></p>
	
>	eg: M1 transistor lies between 3 nodes (in, vdd, out). Hence, very easy to define the transistor
	
**Writing SPICE deck**
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/213409308-8bb26400-00c8-4cc2-ac86-7926d6b09f53.png" height = "270"></p>
	
>	describe M1 and M2 (D G S S Widtg and Length)
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/213435963-c0ef7797-63df-4b87-aaac-4d94b2aec1e1.png" height = "300"></p>
	
>	description of output load capacitor, Vdd and Vin
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/213437146-98d5019a-c8fd-4972-8152-c64c578150bc.png" height = "230"></p>
	
>	red line - sweep the gate input voltage from 0 to 2.5 at steps of 0.05 (to calculate voltage at the output waveform while we sweep the input voltage)
	
>	yellow dotted line - describe the model file (all parameters (attribute) are describe in this)
	
### SPICE simulation lab for CMOS inverter

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/213438656-bb6a7a58-d322-4abe-9336-ff31a58d823e.png" height = "300"></p>

>	channel length and width (NMOS and PMOS) are constant. Spice window shown
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/213438070-14a37013-ab95-4b83-969f-74f01c22e095.png" height = "300"><img src = "https://user-images.githubusercontent.com/118953932/213438258-2e08a73e-ba95-481f-a8e3-7a5e8472504b.png" height = "300"></p>

>	left - model file (parameters) | right - netlist

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/213439188-8e99c732-baa2-430f-8951-c64645af1cc9.png" height = "250"></p>
	
>	spice simulation
	
```
cd #change directory

source <the file> #circuit will present int the simulator
	
run #execute circuit
	
setplot #shows which plot is currently present in the simulator
	
dc1
	
display #the current voltages
	
plot out vs in #in = voltage which are sweeping and out = output
```
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/213439781-839d2a79-e35e-4e1b-9520-3d857aee4704.png" height = "300"></p>
	
>	waveform obtained (slightly to the left)
		
**Increase the width of PMOS**
	
-	new width for PMOS = 0.9375u | Wp/Lp =3.75
-	do the same steps as before for the simulation but change dc1 to dc2
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/213440994-ac7d4249-9492-43fd-8b81-914aff5c41c8.png" height = "300"></p>
	
>	waveform obtained for the new width (2.5 times the NMOS) of PMOS. The waveform is centered
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/213442740-1e089afe-198b-4fec-9bae-e8ed50202eaa.png" height = "300"></p>
	
>	compare the two waveform (the shapes remains the same)
	
Note: due to the characteristic or robustness, CMOS is widely used for building logic gates
	
### Switching Threshold Vm
	
-	Vm = point where Vin is equal to Vout

-	area where PMOS and NMOS are in saturation region (where both are turn on). this os where there is high chances of leakage current
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/213443360-d078d8bb-af88-4230-9849-22458698c037.png" height = "300"></p>
	
>	left = ~0.9 | right = ~1.2
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/213445077-b0e0de43-24a5-41bd-80bd-6c188024e39a.png" height = "300"></p>
	
>	where it kinda turn on (threshold region). same value, different direction
	
### Static and dynamic simulation of CMOS inverter
	
-	identify/calculate the value of rise and fall delay
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/213453598-3f52ab2f-9ecc-4fb2-9c66-9e04304b0cb4.png" height = "400"></p>
	
>	change to pulse and trans
	
```
source #the file
	
run
	
setplot
	
tran2
	
display
	
plot out vs time in
```
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/213454309-b2145650-67c6-4ae1-babc-495b4e4d62ef.png" height = "150"><img src = "https://user-images.githubusercontent.com/118953932/213454734-8d52b307-3120-4233-b2d8-b42ebcf81258.png" height = "300"></p>
	
>	50% of the waveform (rise)
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/213455939-9f325e81-6edf-4fa4-8b10-52146179a6a5.png" height = "300"></p>
	
>	calculate rise delay (red = falling edge | green = rising edge)
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/213456571-ddb3dc72-fed0-487c-bafa-6f8a42eb59fa.png" height = "300"></p>
	
>	calculate fall delay
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/213456700-b1214f31-e9a5-48f7-b180-fc5cf4d47d04.png" height = "300"></p>
	
### Lab steps to git clone vsdstdcelldesign
	
github link: https://github.com/nickson-jose/vsdstdcelldesign
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/213465450-9cfd402f-4e04-4f6e-870a-97978936c360.png" height = "300"></p>
	
>	copy the link and git clone it in /openlane_working_dir/openlane
	
```
cd /home/nurul.aidayanti.muhammad.saleh/Desktop/work/tools/openlane_working_dir/openlane
	
git clone https://github.com/nickson-jose/vsdstdcelldesign.git
	
cd vsdstdcelldesign
```
	
```
cd /home/nurul.aidayanti.muhammad.saleh/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic
	
cp sky130A.tech /home/nurul.aidayanti.muhammad.saleh/Desktop/work/tools/openlane_working_dir/openlane
```
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/213470927-cb6d2f93-11ce-4075-9ca6-3cddee6f35d6.png" height = "300"></p>
	
>	copy files from other directory to current directory
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/213472225-2ced1e8d-00d6-4163-8216-f7d62df17999.png" height = "300"></p>
	
>	inverter layout
	
</details>
	
<details><summary>Inception of Layout Â CMOS fabrication process</summary>
	
##### Table of Contents 
	
-	[Create Active regions](#create-active-regions)
-	[Formation of N-well and P-well](#create-active-regions)
-	[Formation of gate terminal](#formation-of-gate-terminal)	
-	[Lightly doped drain (LDD) formation](#lightly-doped-drain-ldd-formation)
-	[Source Â drain formation](#source-â-drain-formation)
-	[Local interconnect formation](#local-interconnect-formation)
-	[Higher level metal formation](#higher-level-metal-formation)
-	[Lab introduction to Sky130 basic layers layout and LEF using inverter](#lab-introduction-to-sky130-basic-layers-layout-and-lef-using-inverter)
-	[Lab steps to create std cell layout and extract spice netlist](#lab-steps-to-create-std-cell-layout-and-extract-spice-netlist)
	
### Create Active regions
	
**16-mask CMOS process**
	
1.	selecting a substrate
	
	-	P-type, high resistivity (5~50ohms), doping level (10^15cm-3), orientation (100)
		-	doping = process of adding impurity into p type substrate
		-	substrate doping should be less than 'well' doping
	
2.	creating active region for transistors
	-	create isolation between each and every pockets
		-	~40nm of SiO2 (very good insulator)
		-	deposit a layer of ~80nm Si3N4
		-	~1um photoresist
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/213596444-af585b5b-76db-47cc-a8ef-3b32a6a0f1e4.png" height = "200"><img src = "https://user-images.githubusercontent.com/118953932/213596648-2aab2dc6-c64a-47b6-8575-4852aef2198e.png" height = "200"></p>
	
>	Mask1 = protect area from getting exposed. the other area of photoresist will be washed out
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/213597083-253ad11a-753c-4da1-bb6c-efa1af6d0cff.png" height = "200"><img src = "https://user-images.githubusercontent.com/118953932/213597240-892df108-e0d0-41df-9c3a-c2362b147597.png" height = "200"></p>
	
>	mask removed and area of Si3N4 that was not protected will be etched off. photoresist will then be removed
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/213597328-9313f241-b1e5-4e0e-a7b9-06a7f952fb38.png" height = "170"><img src = "https://user-images.githubusercontent.com/118953932/213597501-7fae8819-b832-41dc-9100-6cff7a577c49.png" height = "170"></p>
	
>	grow first level silicon dioxide (left) and second level (right). blue arrows are isolation region (the transistor will not communicate with each other due to it)
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/213597782-9cdf2521-61d2-4c93-bb6a-2b18389d469e.png" height = "200"><img src = "https://user-images.githubusercontent.com/118953932/213597853-251e2820-a89c-4640-8c08-624941d8ac7c.png" height = "200"></p>
	
>	Si3N4 stripped
	
### Formation of N-well and P-well
	
3.	N-well and P-well formation
	-	N-well for PMOS fabrication and P-well is for NMOS fabrication (need to protect one area while fabricate)
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/213598636-582fda52-85e0-492f-bbe7-119c730678bc.png" height = "200"><img src = "https://user-images.githubusercontent.com/118953932/213598806-6fa4f483-603c-419c-b3a4-573ef3145d25.png" height = "200"></p>
	
>	Mask2 to protect the layer of photo resist (left = cross section). Right photo = top view

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/213599267-77402d20-abaf-493d-9878-291d0ce2cfe2.png" height = "200"><img src = "https://user-images.githubusercontent.com/118953932/213599551-42afb83b-9768-405a-9bbb-0c5fcb147fdd.png" height = "200"></p>
	
>	exposed to UV light and washed out. mask removed. P-well created (energy needed to create is ~200keV to make Boron penetrate to the oxide layer and enter into the active area)
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/213602628-ae1f0e26-3b6c-4bc1-ad67-c4efe4af819c.png" height = "200"><img src = "https://user-images.githubusercontent.com/118953932/213602833-7912c53d-486e-44cd-bbf3-a0d800d49ce8.png" height = "200"></p>
	
>	N-well. mask the Pwell side and implant phosphorous (heavier than boron). energy = ~400keV
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/213603809-40933d14-1e01-4c1a-b7d3-de4bf1f4d4c0.png" height = "200"><img src = "https://user-images.githubusercontent.com/118953932/213603877-7a0446c9-2fdc-4c74-a0f8-e41e985ba085.png" height = "200"></p>
	
>	put it in driving furnace so that it will diffuse the boron and phosphorus into the P type substrate
	
### Formation of gate terminal
	
4.	formation of gate
	-	control the threshold voltage
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/213609996-a806b9aa-c8f5-4083-8b58-86bc25b7ef0f.png" height = "250"></p>
	
>	threshold voltage equation (Na and Cox are 2 important terms as they control Vt)
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/213610297-6f6a4464-b345-415f-abb8-1d820e2674aa.png" height = "200"><img src = "https://user-images.githubusercontent.com/118953932/213610627-0180a7f6-319d-47b4-be82-14f964609596.png" height = "200"></p>
	
>	repeated step (mask) to expose the P-well (NMOS). implement boron but with low energy because want it to be just at the surface (modify doping concentration). do it the same for N-well but with phosphorus or arsenic
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/213610782-0494fd5f-4305-47ff-a935-46904a1f3159.png" height = "200"><img src = "https://user-images.githubusercontent.com/118953932/213611043-bf2eea19-43c2-4d46-ada1-be76674f260c.png" height = "200"></p>
	
>	remove the oxide and regrown again. then deposit polysilicon layer (~0.4um) and doped it with impurity (implant on the polysilicon layer)
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/213611153-94bcc004-676e-4ae3-bb5c-fbdd5fca06c5.png" height = "200"><img src = "https://user-images.githubusercontent.com/118953932/213611244-cdfe1aa1-c62e-4634-b12b-ddb1ee679058.png" height = "200"></p>
	
>	mask again (Mask6 = polysilicon mask) cross section and top view
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/213611369-f3061420-2dfb-470b-8ea5-5b0b28130918.png" height = "200"><img src = "https://user-images.githubusercontent.com/118953932/213611518-4b6a42aa-1bbd-4d3b-947f-32716bd1c070.png" height = "200"></p>
	
>	mask remove and remaining area is etched. Then, remove the resist. This is the formation of gate
	
### Lightly doped drain (LDD) formation
	
5.	Lightly doped drain (LDD) formation
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/213626030-b0d9ec29-ed48-46b5-b909-9700e51fe814.png" height = "250"></p>
	
>	source and drain are both P-type (PMOS) and source and drain are both N-type (NMOS). want to form the P- and N-

-	2 reasons for this:
	-	hot electron effect
		-	electric field E=V/d
		-	high energy carriers break Si-Si bonds
		-	3.2eV barrier b/w Si conduction band
		-	SiO2 conduction band
	-	short channel efect
		-	for short channels, drain field penetrates channel
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/213626805-d205d123-a455-4782-a7ac-c70b820d1b26.png" height = "200"><img src = "https://user-images.githubusercontent.com/118953932/213627028-58c0646d-55d2-4714-a03c-82479cd61595.png" height = "200"></p>

>	mask7.	fabricate NMOS (implement phosphorus but the doses are carefully chosen so that it wont penetrate too deep = lightly doped) create N- implant
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/213627216-724973e5-3359-40d3-92f5-3a4f67e9d51f.png" height = "200"><img src = "https://user-images.githubusercontent.com/118953932/213627493-bfb223ac-5c54-4347-b04f-3735b4ede5b8.png" height = "200"></p>

>	do the same step for PMOS but with boron. create P- implant	
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/213627847-9ff3a9cb-f5ec-470d-9248-07a6b31dd0ee.png" height = "200"><img src = "https://user-images.githubusercontent.com/118953932/213628088-d91b5e7b-5316-4785-b8a4-dd728f49c430.png" height = "200"></p>
	
>	deposit a layer ofSi3N4 or SiO2 (green) and do etching to prevent the layer from etched of it. the side-wall spacer helps to maintain the N-implant/P-implant
	
### Source Â drain formation
	
6.	source and drain formation
	-	add thin layer of screen oxide to prevent from channeling during implants (ion might go deep inside the P-substrate)
	-	do mask again
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/213628870-c04f1360-9862-4283-a021-007bdd4b1a93.png" height = "200"><img src = "https://user-images.githubusercontent.com/118953932/213629172-b8a23f2c-0f18-455c-be68-f0be6727789e.png" height = "200"></p>
	
>	implement arsenic. N- implant present
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/213629391-5a0ce468-7a6e-4a9e-a3fa-fc3e6f643087.png" height = "200"><img src = "https://user-images.githubusercontent.com/118953932/213629485-198a700b-a1fe-4761-82c3-513407056a2f.png" height = "200"></p>
	
>	same process as before
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/213629589-515dc37e-f7c0-4187-b88a-db7edad0e47b.png" height = "200"><img src = "https://user-images.githubusercontent.com/118953932/213629760-3481a967-b65c-48ae-87b5-3c619604bc1e.png" height = "200"></p>
	
>	high temperature furnace. they will penetrate more in the N-well and P-well	

### Local interconnect formation
	
7.	steps to form contacts and interconnects (local)
	-	user can control the electrical characterisic of the PMOS and NMOS
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/213631815-a4c008b1-47b9-4c9e-8935-e94aeebfd08a.png" height = "200"><img src = "https://user-images.githubusercontent.com/118953932/213632653-3ceb41cf-f7f7-4c6d-affa-fca3b59abbd7.png" height = "230"></p>
	
>	remove the thin oxide. then deposit titanium on wafer surface using sputtering (titanium was hit with Argon gas and it will sputter out (emit out titanium metal) and will be deposited to substrate)
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/213632975-091d9a89-dd6f-4054-a2c4-796be867fa71.png" height = "200"><img src = "https://user-images.githubusercontent.com/118953932/213633438-67b61a2d-608b-4850-bceb-8b3b03c07e4c.png" height = "200"></p>
	
>	heated at a very high temp and form TiSi2 and TiN
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/213633739-9a4a529b-8670-4b14-9a3d-a1aaeea0c8a7.png" height = "200"><img src = "https://user-images.githubusercontent.com/118953932/213634049-adfc3192-9bd2-4284-abef-0d85336f5a58.png" height = "200"></p>

	>	mask level and remove it and etched of the TiN using RCA cleaning (solution)
	
### Higher level metal formation

8.	Higher level metal formation

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/213636906-5e057559-34b6-4ebf-a2c0-4035f3bbe36b.png" height = "200"><img src = "https://user-images.githubusercontent.com/118953932/213641360-49ac206d-df54-4918-82e2-1664d41a1d6d.png" height = "200"></p>
	
>	deposit a thick layer of SiO2 and polish to get a flat surface using chemical mechanical polishing (CMP) technique for planarizing water surface. Then, create contact tools. mask it (Mask12) and remove it and etch of where we want to drill the contact layer. remove photoresist
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/213641552-811787da-d095-4a33-b7f8-dd5cfc675001.png" height = "200"><img src = "https://user-images.githubusercontent.com/118953932/213641823-140b9064-71f2-4583-9ba2-61979cb20790.png" height = "200"></p>
	
>	deposit thin layer of TiN and deposit blanket tungsten (W) layer deposition. Then CMP again
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/213642104-66d74f1c-bc14-43a3-820f-03c9080d354c.png" height = "200"><img src = "https://user-images.githubusercontent.com/118953932/213642250-a5fdfc33-175b-434f-b95e-b5f882cf35f8.png" height = "200"></p>
	
>	deposit aluminium layer and mask again (Mask13). Al is plasma etched. Remove resist
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/213642528-164c72bb-49a9-46d5-803c-bed56bc4ce5b.png" height = "200"><img src = "https://user-images.githubusercontent.com/118953932/213642753-f51e70f4-46aa-43d2-86a5-107505d925e6.png" height = "200"></p>
	
>	aluminium interconnect and deposit oxide
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/213642894-6eb01b5c-17ca-4124-8bd5-bd7e48b6446e.png" height = "200"><img src = "https://user-images.githubusercontent.com/118953932/213643133-970880f2-c0a3-40e6-bd17-4d7998a98de7.png" height = "200"></p>
	
 >	pattern the same thing and do the mask step again (Mask14). deposit TiN again. deposit tungsten making the contact holes
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/213644039-60595754-3ca3-45a9-a87c-6f457b24b2ec.png" height = "230"><img src = "https://user-images.githubusercontent.com/118953932/213644242-c31ad211-acb0-4d23-b7fb-892e173667e7.png" height = "230"></p>
	
>	third level of interconnection (Mask15) and deposit Si3N4 to protect the chip
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/213644506-faf69b76-3e3d-493a-864b-dddccf6f038d.png" height = "230"><img src = "https://user-images.githubusercontent.com/118953932/213644733-18cfa058-d04e-4b0e-bec1-d9c15eac3e1b.png" height = "230"></p>
	
>	final mask (Mask16). source, gate and drain fabricated
	
### Lab introduction to Sky130 basic layers layout and LEF using inverter
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/213649949-5e58ddfd-a442-4bd5-90e0-f19cc7b91346.png" height = "250"></p>
	
>	layout of inverter
	
-	local  = blue
-	metal 1 = purple
-	metal 2 = pinkish
-	N-Well = black dash line
-	ndiffusion = green 
-	pdiffusion = brown 
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/213652392-34bd5fa4-c65a-47f9-b4d7-2a7ac182a32f.png" height = "250"><img src = "https://user-images.githubusercontent.com/118953932/213652795-1f526f30-3dd3-4986-93b4-c72b55a5ae3c.png" height = "250"></p>
	
>	cursor go to the green one and press S to see what the higlighted is
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/213653224-68cebd69-83c8-48da-969d-b4cac4e08206.png" height = "250"><img src = "https://user-images.githubusercontent.com/118953932/213653807-cc0ad2f4-c9de-4d53-834c-e488d72919f3.png" height = "250"><img src = "https://user-images.githubusercontent.com/118953932/213653925-b4fae882-4471-42f7-b436-4a6147309247.png" height = "250"></p>

>	move the cursor and press S twice. the highlighted (left) means the drains are connected to the output. source of PMOS connected to vdd (middle) and source of NMOS connected to ground (right)
	
Link on detailed explaination: https://github.com/nickson-jose/vsdstdcelldesign
	
### Lab steps to create std cell layout and extract spice netlist
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/213655965-1082962c-a937-4f55-8db9-c34585a9ce8b.png" height = "300"></p>

>	PMOS = N-well. nsubstrate contact between N-well and locali. licon contact between locali and metal 1. NMOS = no well 

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/213657383-58406347-4880-4ff4-b875-2e7d8fac7a96.png" height = "250"><img src = "https://user-images.githubusercontent.com/118953932/213657813-e57062cf-46b0-4981-a425-cef86752afcf.png" height = "150"></p>

>	white dotted line is the error and to know the error just click DRC tab and click DRC find next error. To know the error, look at the tkcon. To fix it select the area (left click right click) and click the layer on the right. Lastly, ensure the final design needs to be DRC clean.
	
```
#in tkcon
	
pwd
	
extract all #extract the inverter
	
ext2spice cthresh 0 rthresh 0 #extract parasitic capacitance
	
ext2spice
```
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/213659753-a99e1a76-e94d-4d35-926d-0b524a53a46d.png" height = "300"></p>
	
>	the .ext file and .spice created
	
</details>
	
<details><summary>Sky130 Tech File Labs</summary>
	
##### Table of Contents 
	
-	[Lab steps to create final SPICE deck using Sky130 tech](#lab-steps-to-create-final-spice-deck-using-sky130-tech)
-	[Lab steps to characterize inverter using sky130 model files](#lab-steps-to-characterize-inverter-using-sky130-model-files)
-	[Lab introduction to Magic tool options and DRC rules](#lab-introduction-to-magic-tool-options-and-drc-rules)	
-	[Lab introduction to Sky130 pdk's and steps to download labs](#lab-introduction-to-sky130-pdks-and-steps-to-download-labs)
-	[Lab introduction to Magic and steps to load Sky130 tech-rules](#lab-introduction-to-magic-and-steps-to-load-sky130-tech-rules)
-	[Lab exercise to fix poly.9 error in Sky130 tech-file](#lab-exercise-to-fix-poly9-error-in-sky130-tech-file)
-	[Lab exercise to implement poly resistor spacing to diff and tap](#lab-exercise-to-implement-poly-resistor-spacing-to-diff-and-tap)
-	[Lab challenge exercise to describe DRC error as geometrical construct](#lab-challenge-exercise-to-describe-drc-error-as-geometrical-construct)
-	[Lab challenge to find missing or incorrect rules and fix them](#lab-challenge-to-find-missing-or-incorrect-rules-and-fix-them)
	
### Lab steps to create final SPICE deck using Sky130 tech
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/213673186-a30d8135-fe9c-424d-8892-a74cc6be3fb4.png" height = "300"></p>
	
>	PMOS and NMOS characterization and connections details
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/213681004-41888b0b-5ad1-492d-a118-59e6957ddd9c.png" height = "300"><img src = "https://user-images.githubusercontent.com/118953932/213681172-0c603170-6614-40d2-ab2b-ee1681633db3.png" height = "300"></p>
	
>	edit the scale to reflect the value in the magic tool. include PMOS and NMOS lib files. comment out the subckt and .end line to include the transient analysis controls. define supply voltages. specifies input pulse and the specification for the transient analysis. rename pmos and nmos models as in the model lib file. "ngspice sky130A_inv.spice" to run the spice simulation.
	
### Lab steps to characterize inverter using sky130 model files
	
```
#ngspice
	
plot y vs time a
```
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/213681373-d4882e94-6ee4-4dfe-821a-7bb34a3e8c87.png" height = "300"><img src = "https://user-images.githubusercontent.com/118953932/213682214-d6189727-fcfd-42da-ac61-f27e4f3ddd71.png" height = "300"></p>
	
>	plot y vs time a 
	
Note: increase the capacitance load (C3) to 2fF to make it better
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/213684137-1035a48f-cfa4-4ed7-b1b1-94c157d7d79c.png" height = "300"><img src = "https://user-images.githubusercontent.com/118953932/213684629-2fac45c0-e1d1-4d84-ac8d-deb139d2804d.png" height = "300"></p>
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/213684792-be035a36-f72d-49e1-97f8-b8f737c9b95c.png" height = "100"></p>

>	20% = 0.66, 80% = 2.64 | rise time = 0.06669 (difference of the X value)
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/213686311-ce1157a1-1226-4d14-a90d-1c6a6c00ce9a.png" height = "300"><img src = "https://user-images.githubusercontent.com/118953932/213686590-6227923b-ab57-4082-8498-9cd60474e507.png" height = "300"></p>
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/213686663-f392e3e8-f318-42e9-a343-5bb1b479e39e.png" height = "100"></p>
	
>	fall time = 0.06 (20% - 80%)
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/213688384-0a447992-edc1-4117-bf3c-4ed6741605fa.png" height = "300"></p>
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/213685851-9c2d409f-bd4a-4e40-9808-856e31311dd2.png" height = "100"></p>
	
cell rise delay = 0.06361 (50% output - 50% input)
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/213687095-e61174d6-8ee6-4a5f-9465-03fda4073ca3.png" height = "300"></p>
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/213687308-2c6569e2-4c0f-4cc2-92e7-dae89efda55b.png" height = "100"></p>
	
cell fall delay = 0.02692
	
### Lab introduction to Magic tool options and DRC rules
	
Link to know more detail: http://opencircuitdesign.com/
	
Link for Magic: http://opencircuitdesign.com/magic/index.html
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/213712643-f36f74a5-3fef-440c-811e-2ca4bb3dffed.png" height = "300"></p>
	
>	website to learn about Magic (eg: commands, tutorials, technology files (CIF, DRC))
	
###	Lab introduction to Sky130 pdk's and steps to download labs
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/213719559-3d132fec-a60c-4bb7-8bdb-35e767d1dea6.png" height = "250"><img src = "https://user-images.githubusercontent.com/118953932/213720104-8840140f-7edd-4d9c-98cb-06b9a5be1978.png" height = "150"></p>
	
>	for layout exercise
	
```
vim .magicrc 
```
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/213721967-4a3469f7-0651-4a9e-9db4-8f8421b9d0eb.png" height = "300"></p>
	
>	startup script for magic
	
**To start magic**
	
```
pwd #make sure at /Desktop/work/drc_tests
	
magic -d XR
```
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/213722854-c65eeffb-4ebd-4bba-a902-d10b2fd6055a.png" height = "300"></p>
	
### Lab introduction to Magic and steps to load Sky130 tech-rules
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/213723687-c022d601-f1df-4d48-994c-f60357aec6d1.png" height = "230"><img src = "https://user-images.githubusercontent.com/118953932/213723849-3fcda894-8224-46bf-a539-623c8b8d7ab5.png" height = "230"></p>
	
>	open met3.mag
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/214491434-48a599eb-a497-480e-b08e-d9b44ef4d706.png" height = "230"><img src = "https://user-images.githubusercontent.com/118953932/214492625-04e40e63-ecb7-4588-b1ab-ff3b866e2e51.png" height = "230"></p>
	
>	drc why to check what is the violation (up) make a square and then click the middle mouse or p key at the m3contact (down)
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/214494263-0e5891d0-9ff8-4a8f-964c-20df74a71fe6.png" height = "230"><img src = "https://user-images.githubusercontent.com/118953932/214494557-284a7111-7b56-4bc6-937c-2f5a585fdfce.png" height = "230"></p>
	
>	type command "cif see VIA2" to make the small black boxes which are contact cuts (created based on the rules in the tech file). The distance between the cut and the edge is always larger and will never be smaller than 0.065
	
Note: use feed clear to clear the one that we've made
	
### Lab exercise to fix poly.9 error in Sky130 tech-file
	
-	load poly.mag
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/214501474-5bbb75fd-abfd-409b-bd18-b2f9c1b57407.png" height = "230"><img src = "https://user-images.githubusercontent.com/118953932/214501806-4b01f84c-3427-4673-8f0b-c050231802d6.png" height = "230"></p>
	
>	below 0.22 so violated
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/214506536-4fce5d62-0d0e-448b-9062-a451e5a08aa7.png" height = "230"><img src = "https://user-images.githubusercontent.com/118953932/214507572-644a489a-13d9-4fcc-bc3d-431fb42befe3.png" height = "230"></p>
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/214508173-5129b7f6-7e55-4c3c-9299-cf10a4624f32.png" height = "230"><img src = "https://user-images.githubusercontent.com/118953932/214512589-e9d3ff1d-fff3-488c-bb2c-24ae815dcdf4.png" height = "230"></p>
	
>	edit sky130A.tech
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/214513028-2a5c22f6-cbc7-4be1-b0d5-6d46463bf7da.png" height = "250"></p>
	
>	command "tech load sky130A.tech" to read in the new modified tech rules. Run command "drc check" to apply the rule and "drc why" to know why it's violating
	
	
### Lab exercise to implement poly resistor spacing to diff and tap
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/214549753-cdc7e673-c74b-4041-881b-07442338e6f8.png" height = "250"></p>
	
>	copy and do as above. there's violation
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/214564685-1f5c96b7-d56a-4397-a3f3-66604c9d8ada.png" height = "230"><img src = "https://user-images.githubusercontent.com/118953932/214565164-875066b1-53e3-4e65-9815-372553abda7d.png" height = "230"></p>
	
>	edit the sky130A.tech
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/214565826-c8e19db7-92bb-438a-85f3-ffabce8579c0.png" height = "250"></p>
	
>	after changing the violation rule
	
	
### Lab challenge exercise to describe DRC error as geometrical construct
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/214566683-246a4778-ca65-4721-938d-04a939113e4a.png" height = "240"><img src = "https://user-images.githubusercontent.com/118953932/214567548-2a04d682-8e38-41fd-8afd-08f020a9bf50.png" height = "220"></p>
	
>	cifmaxwidth rule =  checks layers exactly as they appear in gds output even though the layers are not something you can draw directly in the layout
	
>	nwell_missing = a layer define a special cif output section in the tech file
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/214568529-5c88b126-4269-4bb9-8240-1b65cda11d2a.png" height = "220"><img src = "https://user-images.githubusercontent.com/118953932/214569010-ba85eac1-17a2-469a-a328-27e22025bc9c.png" height = "220"></p>
	
>	load nwell.mag and look at nwell.6. deep nwell yellow stripes and nwell green dot pattern
	
>	the point of the rule is that the edge of the dnwell needs be covered with overlap all the way around by a ring of regular n-well. The outside distance rule could be implemented by a simple surround drc rule, but the inside distance cant be captured with a simple edge type rule
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/214571443-b5f3e334-f9fd-406d-a932-f26827211b8d.png" height = "250"></p>
	
>	cif ostyle drc = can only see layers for the cif layer style that is selected for output

>	cif see dnwell_shrink = to see that area
	
>	feed clear = clear
	
>	cif see nwell_missing =shows the area which gets flagged with the error
	
### Lab challenge to find missing or incorrect rules and fix them
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/214580215-61f15b08-22c5-46bf-8266-69da6b18aac8.png" height = "200"><img src = "https://user-images.githubusercontent.com/118953932/214577228-db357650-3034-48f8-901e-d619ab672923.png" height = "220"></p>
	
>	edit the rule
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/214579270-1a55413d-28c7-4007-a56e-8f1311bfb8ca.png" height = "250"></p>
	
>	tech load the file and then drc check then drc check drc(full) and drc check again. still have error so copy the nwell and place the nsubstratencontact (blue x box) and the error goes away
	
</details>	
	
# Day-18
## Pre-layout timing analysis and importance of good clock tree

<details><summary>Timing modelling using delay tables</summary>
	
<details><summary>Lab steps to convert grid info to track info</summary>
	
Objective: extract LEF file from the .mag file and then plug the file into the picorv32a flow (previous is standard cell library)
	
Main guidelines:
1.	the input and output ports must lie on the intersection of the vertical and horizontal tracks
2.	the width of standard cell should be on the track pitch, and the height should be on the track vertical pitch
	

```
cd /home/nurul.aidayanti.muhammad.saleh/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/openlane/sky130_fd_sc_hd

less track.info
```
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/214727834-6f2ba979-43e7-4ecf-8909-ed51fd997772.png" height = "250"><img src = "https://user-images.githubusercontent.com/118953932/214729136-1913ca76-e7a9-442c-bf24-3bc503aa968b.png" height = "250"></p>
	
	
>	track info (using during routing stage)  routes can go over the track/layer (metal traces)
	
>	press g to enable grid (zoom in to see the grid) 
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/214729810-99e0d952-1195-441c-9cba-189a6e82a399.png" height = "230"><img src = "https://user-images.githubusercontent.com/118953932/214729865-7c54125a-22aa-481c-9859-b932aa93442d.png" height = "230"></p>
	
>	set the grid based on the track info (grid <space along x> <space along y> <x> <y>) converted the track into grid 
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/214730792-a1231aad-54e7-4113-b769-da522b44fa48.png" height = "250"></p>
	
>	ports are on the intersection of the horizontal and vertical tracks. it ensures that the routes can reach the ports from x and y direction
		
</details>
	
<details><summary>Lab steps to convert magic layout to std cell LEF</summary>
	
Second requirement: the width and height of the std cell should be in the odd multiples of the x and y pitch (to ensure the layout is done as per requirement)
	
-	Whenever a layout is made, the layers are defined, but there are no ports, ports does not mean anything to the magic. Port definitions are required when we want to extract the lef file. The ports will be defined as the pins of the macros

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/214734547-8375c0cf-0b5e-4639-938d-6d8d96e77695.png" height = "250"></p>
	
>	text helper to create the port in the design. port number = the order in which the port is written in the lef file (this is how the ports for all the layers are defined in the design)
	
Note: this has already been applied so dont click apply
	
-	define what is the purpose of the port (how tool know A is input port or Y is an output port)
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/214735211-eb0ee7ef-a323-4e8a-be2b-266af0eb5014.png" height = "250"></p>
	
>	set the port class and port use attribute
	
-	 extract the lef file
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/214735922-76f353ba-8d9d-49f9-8bf7-2bee0a3e5d01.png" height = "230"><img src = "https://user-images.githubusercontent.com/118953932/214736324-a6db04f1-6f36-438b-8ed4-65f5f0eaf535.png" height = "230"></p>
	
>	save the mag file and use that one (sky130_nrlinv.mag)
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/214736751-3a14fdb8-141e-4821-8cb3-c29e6fc9828a.png" height = "230"><img src = "https://user-images.githubusercontent.com/118953932/214736941-77bfee37-4274-45a0-b51b-941ca05e7a9e.png" height = "230"></p>
	
>	create lef life
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/214737487-f43a8f46-692b-4ca3-9b7f-f931141378bf.png" height = "250"></p>
	
>	pin usage
	
</details>
	
<details><summary>Introduction to timing libs and steps to include new cell in synthesis</summary>
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/214740469-ad91179b-0d00-480f-bf33-c66452276691.png" height = "250"></p>
	
>	copy the lef file and library into the design folder (/picorv32a/src). this is to include the custom cell into the openlane flow (first is synthesis). need to ensure the abc step maps the cell appropriately, thus we need to have a library which has the timing definitions
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/214742527-41af02d4-7f93-4661-bfe4-62ea8ca91d3f.png" height = "250"></p>
	
>	modify config.tcl
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/214746850-e98e45a5-bba8-4c83-8f98-1e46977fde1d.png" height = "230"><img src = "https://user-images.githubusercontent.com/118953932/214747113-c554078e-344b-4bd3-be57-9183df3db54d.png" height = "230"></p>
	
>	run synthesis
	
</details>
	
<details><summary>Lab steps to configure synthesis settings to fix slack and include vsdinv</summary>
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/214752614-e9afecc9-7b16-48b1-9945-fec2527581cb.png" height = "100"><img src = "https://user-images.githubusercontent.com/118953932/214752483-4f18d349-d2ce-4fac-a4a2-643559232d1d.png" height = "150"></p>
	
>	WNS, TNS and chip area
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/214756422-17f8f501-24ae-4c20-94bf-0e3cc6892d0d.png" height = "230"><img src = "https://user-images.githubusercontent.com/118953932/214756381-e2cb9462-8d93-4219-b3ff-318c2901f8f8.png" height = "230"></p>
	
>	increase area, improve timing (refer README.md) - fix sta
		
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/214759076-fc71510a-aab1-4464-aacb-121640737ab3.png" height = "250"></p>
	
>	nrlinv exists in merged.lef (picorv32a/.../runs/tmp)
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/214761047-493f21aa-e9d4-4389-8783-1be9e715d77f.png" height = "230"><img src = "https://user-images.githubusercontent.com/118953932/214761199-54931475-ccbf-4309-9947-c9c5ca2bf690.png" height = "230"></p>
	
>	run_floorplan and then run_placement
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/214762476-d8cc3783-b9c0-4c2f-ac16-1dc384f18de2.png" height = "230"><img src = "https://user-images.githubusercontent.com/118953932/214774544-b22c95ea-e998-4507-a60d-a893cbe83b97.png" height = "80"></p>
	
>	run magic and the custom cell is done plugin 
	
</details>
	
<details><summary>Introduction to delay tables</summary>

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/214775324-7eb8e831-232a-4ec3-bfc6-d677af1803fd.png" height = "250"></p>
	
>	AND GATE = clock propagate through the gate when logic is 1 (else block the clock) | OR GATE = clock propagate through the gate when logic is 0 (else block the clock)
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/214776362-840f9a6e-3a8e-4442-b119-a4bcd8b51885.png" height = "250"></p>
	
>	clock gating technique  (look into the timing characteristics of the buffer before swap out the buffer for a gate)
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/214776820-68c4b691-78ca-453c-b55a-2f15b47d525b.png" height = "250"></p>
	
>	observation need to be done as in picture. but need to keep in mind that the load at the output will be varying. since the load of one buffer is varying, the input transition of the following buffer is also varying. Hence, we will have a variety of delays.
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/214778394-345e7ebc-03e0-41e5-9509-ab11a63e4f24.png" height = "250"></p>
	
>	the delay table is characterized based on varying the input transition and output load of a cell, against the delay of that cell. Each and every type of cell or gate will have its own delay table for different sizes and threshold tables

	
</details>
	
<details><summary>Delay table usage</summary>
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/214778995-f2f0401f-5e72-416b-b046-0041c6529e64.png" height = "230"><img src = "https://user-images.githubusercontent.com/118953932/214779280-556f8a18-0495-4eb1-9575-3e4f96de2292.png" height = "230"></p>
	
>	for example, delay table for size 1 buffer, input slew = 60ps and output load = 70fF. So the delay of that will be x16. (increase pmos/nmos size, will reduce the resistance. vary the size of the device, it will also vary the RC constant which is delay of that particular cell). that why each and every cell has each own delay table
	
Note: if the values are not in the table, those values will be extrapolated from the given data (come out of a equation)
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/214781518-1a8b2227-af19-4cb7-bdcc-3102a6237683.png" height = "230"><img src = "https://user-images.githubusercontent.com/118953932/214782694-a5c24bfd-0542-4c8f-8b3a-a0ef859952cb.png" height = "230"></p>
	
>	latency from clock port to the sink pin (x9' + y15). If in the same level, the buffers drive different loads, then it will have non zero skew value. That's why it is preferred to have the nodes at each level driving the same load. same goes to having different size in the same level
	
>	power aware CTS, where we have to consider endpoints which are only active under certain conditions. In these cases, we need not propagate the clock (can stop the clock)
		
</details>
	
</details>
	
<details><summary>Timing analysis with ideal clocks using openSTA</summary>
	
<details><summary>Setup timing analysis and introduction to flip-flop setup time</summary>
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/214797321-d9611575-8dcf-4e42-894a-245c2ec0270c.png" height = "300"></p>
	
>	on the zero time, there is one clock edge that reaches the launch flop. And on the T time period (T=1ns), the second rising edge reaches the capture flop. Any analysis needs to be done in between 0 and T. For the combinational circuit to work, the combinational delay (the internal delay of the launch flop and combinational delay) needs to be less than the period, T (cannot exceed)
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/214797833-e727ce73-f3b6-49f3-a8ee-4531fa010476.png" height = "250"></p>
	
>	when clock switches from logic 0 to logic 1, the output of the mux will be fed back. data from Qm moves to Q. mux 1 delay or mux 2 delay will restrict the combinational delay requirements. Hence, finite Time 'S' required (before clk edge) for 'D' to reach Qm i.e. internal delay of Mux1 = setup time. this setup time needs to be subtracted away from the complete clock period T
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/214799392-8976e36a-1b3d-4422-8874-54c070ee8b37.png" height = "300"></p>
	
>	now the capture flop has enough time for it to bring the data to the flop and ensure the data system work at the amount of time
	
</details>
	
<details><summary>Introduction to clock jitter and uncertainty</summary>
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/214981873-7d5ed9b7-2aeb-4cf7-a924-d40fa01c65ee.png" height = "230"><img src = "https://user-images.githubusercontent.com/118953932/214982344-e9a661a3-e355-4339-9d3a-f667e9456dec.png" height = "230"></p>
	
>	clock is expected to reach the clock pin at exactly 0 or T. but in real scenarios, the clock source might not be able to reach exactly at that moment. this is due to the clock source generation might have its own built-in variation. The temporary variation of the clock period is called as jitter. The combinational delay will become more stringent becuase of the variations. Hence, we will model the jitter using one more parameter called uncertainty.
	
Note: SU = setup uncertainty
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/214982604-da9320c9-d843-4311-9fdb-f83e03fce125.png" height = "230"><img src = "https://user-images.githubusercontent.com/118953932/214982802-09a03820-f797-4bc6-a389-69c3a99e0d18.png" height = "230"></p>
	
>	combinational delay (should be less than 1ns-0.01ns-0.09ns = 0.9ns)
	
</details>
	
<details><summary>Lab steps to configure OpenSTA for post-synth timing analysis</summary>
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/214987106-907af7a2-1ede-459c-b9f2-ab469388d467.png" height = "150"><img src = "https://user-images.githubusercontent.com/118953932/214995825-4d8c55a0-6a60-448e-a9ea-b8ede40433f8.png" height = "230"></p>
	
>	write configuration pre_sta.conf (top) and my_base.sdc (bottom)
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/214996888-70861fc8-2fe5-4798-891e-815b4aa09303.png" height = "230"></p>
	
>	run sta using "sta pre_sta.conf" in openlane directory (where the file is)
	
</details>
	
<details><summary>Lab steps to optimize synthesis to reduce setup violations</summary>
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/215004112-f0083c92-0e0d-4101-82a6-241964131814.png" height = "250"></p>
	
>	ignore hold timing since CTS is not done yet
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/215004490-05cc54f3-12ab-4e8b-93ec-dfc95add684d.png" height = "250"></p>
	
>	delay are high for setup timing. the more the input slew, the more the delay. the more the cap, the more the output delay
	
```
#in openlane
	
set ::env(SYNTH_MAX_FANOUT) 4
	
run_synthesis
```

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/215032726-762b3475-1014-4992-8653-b358a836268b.png" height = "120"><img src = "https://user-images.githubusercontent.com/118953932/215033016-dd810e26-1583-4417-b1b7-a89135344a8a.png" height = "80"></p>
	
>	"sta pre_sta.tcl" before (left) after setting fanout (right)
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/215046418-8fc7d7be-1c17-4e0e-a69e-08ff3da8c0d7.png" height = "230"><img src = "https://user-images.githubusercontent.com/118953932/215048539-5c304d08-e36b-49a4-9125-42313b219153.png" height = "100"></p>
	
```
replace_cell _38618_ sky130_fd_sc_hd__dfxtp_4 #increase drive strength
	
report_checks -fields {net cap dlew input pins} -digits 4
	
report_tns

report_wns
```
	
>	wns and tns improved a bit
	
</details>
	
</details>
	
<details><summary>Clock tree synthesis TritonCTS and signal integrity</summary>	
	
<details><summary>Clock tree routing and buffering using H-Tree algorithm</summary>
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/215368265-46c0e833-abcf-4b08-86fd-8e7bb7887108.png" height = "240"><img src = "https://user-images.githubusercontent.com/118953932/215368881-0f2e09d8-42e0-4007-9f48-aa4d95551181.png" height = "240"></p>
	
>	make clock reach the flops by connecting it (left one is a bad tree) clock reaches each and every flop almost at the same time due to it connected at midpoint (right picture) H-Tree
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/215368459-ce13d38d-8cfb-4058-898b-dd9bf6857262.png" height = "250"></p>
	
>	want skew to be as close to 0 as possible
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/215369173-d2d3bfc4-66d1-4573-8ba8-3132a74183d7.png" height = "250"></p>
	
>	lot of resistance and capacitances in the path. expect output waveform be the same as input waveform but we didnt get it due to the rc network. Hence, need to add repeaters (help reproduce signal)
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/215369650-2ab56e5b-fe9b-4383-b5a3-50a6095768c1.png" height = "250"></p>
	
>	repeaters (red buffer = clock buffer) for clock have equal rise and fall time. clock signal which is being sent at the input will be continuosly reproduce at the flop clock end point
	
</details>
	
<details><summary>Crosstalk and clock net shielding</summary>
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/215370305-7d5e740c-423c-48a7-87a7-3cf93d75280a.png" height = "250"></p>
	
>	clock nets are the critical nets in the design, the clock tree are built to ensure there is a minimum skew. However, if there is any cross talk that happens and affect the clock signals, that will affect the design very badly. clock net shielding = protect the clock nets from the outside world
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/215370888-90dc7ad2-94a7-4a61-96f4-9839a2fdd6ea.png" height = "250"></p>
	
>	if glitch occurs on the clock net, incorrect data in the memory will result inaccurate functionality for the design. shield (wire) can be connected to Vdd or ground (because they wont switch)
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/215373047-2075c497-df1b-4b1c-af43-bf08064e9c7f.png" height = "250"></p>
	
>	impact of crosstalk delta delay
	
	
</details>
	
<details><summary>Lab steps to run CTS using TritonCTS</summary>
	
```
#in sta terminal
	
write_verilog ~/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/<date>/results/synthesis/picorv32a.synthesis.v
```

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/215092735-599dd07b-a622-4fb4-88e5-13ca842b759a.png" height = "60"><img src = "https://user-images.githubusercontent.com/118953932/215092626-43f39b32-5adb-43e9-8c0d-9f0f93bd958a.png" height = "90"></p>
	
>	create new netlist (overwritten the old file)
	
```
#in openlane
	
run_floorplan
	
run_placement
	
run_cts
```
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/215094936-28eb3fee-9da5-4431-ba98-de913e478ab6.png" height = "150"></p>
	
>	README.md
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/215095226-038bb8ae-bb28-4845-908e-8d91af7d6cbe.png" height = "100"></p>
	
>	cts file generated

</details>
	
<details><summary>Lab steps to verify CTS runs</summary>
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/215096839-0bbc1f5e-f97f-4188-9ac5-440fcc8f3ff0.png" height = "200"></p>
	
>	open the tcl file for cts stage (every stage has its own .tcl file)
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/215097695-ddd740d1-4bbc-4c3a-9e8f-3595f5654b7c.png" height = "100"><img src = "https://user-images.githubusercontent.com/118953932/215097953-c1d5f3dd-94a8-4a1c-87c3-9854c453963f.png" height = "250"></p>
	
>	or_cts.tcl
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/215098954-c3038131-2ad0-4a9a-8c50-80ec8cf57617.png" height = "130"></p>
	
>	clock buffer cells are added. disadvantage of the tritonCTS = cannot create an optimized CTS for multi corner
	
</details>
	
</details>
	
<details><summary>Timing analysis with real clocks using openSTA</summary>
	
<details><summary>Setup timing analysis using real clocks</summary>
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/215373673-761e1499-d394-43f3-84cb-d312cb9e8727.png" height = "240"><img src = "https://user-images.githubusercontent.com/118953932/215374164-dcdd0fc6-b3da-41d5-a679-79cfd9d7cdf6.png" height = "240"></p>
	
>	due to the buffers insertion, the clock edge will reach the clock pin with consideration to the delays of the buffers inserted (causing window to shift)
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/215374483-98b434f5-b047-425f-9e01-c2f9aee722f9.png" height = "250"></p>
	
>	real complete setup timing analysis equation
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/215374665-0c517506-c1e2-494d-8cf9-d0885b6e02ee.png" height = "100"></p>
	
>	slack (violating if negative)
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/215375189-883edf5e-98c0-4e4c-9a00-e2740aa78af0.png" height = "240"><img src = "https://user-images.githubusercontent.com/118953932/215375362-4bae71a4-dc0a-4e2f-9424-c6d01c0d8c1f.png" height = "240"></p>
	
>	hold timing analysis (the 0 edge will be sent to launch flop and capture flop) capture flop send message to the launch flop to send data after hold time (mux 2 delay). need to send existing data outside of the flop first
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/215375722-55ccd3b7-9ced-4d4d-ac54-6ee9481e6d0f.png" height = "250"><img src = "https://user-images.githubusercontent.com/118953932/215375766-3bb55b77-d593-4134-936e-1e5d477f9d02.png" height = "90"></p>
	
>	hold equation with the presents of clock buffer
	
</details>
	
<details><summary>Hold timing analysis using real clocks</summary>
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/215376687-008cd9b0-89b9-403b-b76b-75d38b5f5f0e.png" height = "250"></p>
	
>	arrival greater than required
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/215378464-3a010f20-0c7b-42d8-8bdb-3af3c7a68fce.png" height = "250"></p>
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/215379428-0019c017-3cc3-4bad-a49f-42a6a9cafd8c.png" height = "230"><img src = "https://user-images.githubusercontent.com/118953932/215379512-ed9daf35-4925-4962-96ca-2e0e8191c549.png" height = "230"></p>
	
>	setup and hold time
	
</details>
	
<details><summary>Lab steps to analyze timing with real clocks using OpenSTA</summary>
	
```
openroad #invoke openroad
read_lef /openLANE_flow/designs/picorv32a/runs/19-01_07-02/tmp/merged.lef
read_def /openLANE_flow/designs/picorv32a/runs/19-01_07-02/results/cts/picorv32a.cts.def
write_db pico_cts.db
read_db pico_cts.db
read_verilog /openLANE_flow/designs/picorv32a/runs/19-01_07-02/results/synthesis/picorv32a.synthesis_cts.v
read_liberty -max $::env(OPENLANE_ROOT)/designs/picorv32a/src/sky130_fd_sc_hd__slow.lib
read_liberty -min $::env(OPENLANE_ROOT)/designs/picorv32a/src/sky130_fd_sc_hd__fast.lib
set_propagated_clock [all_clocks]
read_sdc designs/picorv32a/src/my_base.sdc
report_checks -path_delay min_max -format full_clock_expanded -digits 4
```
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/215101234-3255221d-abc1-495b-b840-47cdafe85ed7.png" height = "250"><img src = "https://user-images.githubusercontent.com/118953932/215102881-f4b9c51f-64fa-4da4-96a1-0347dd680f2a.png" height = "250"></p>
	
>	use “openroad” to perform timing analysis of the clock tree (able to use the variables set within the openlane flow). needs to rectified hold slack first because the violation cannot be solved by simply changing the period
	
</details>
	
<details><summary>Lab steps to execute OpenSTA with right timing libraries and CTS assignment</summary>
	
```
exit 
openroad
read_db pico_cts.db
read_verilog /openLANE_flow/designs/picorv32a/runs/19-01_07-02/results/synthesis/picorv32a.synthesis_cts.v
read_liberty $::env(LIB_SYNTH_COMPLETE)
link_design picorv32a
read_sdc designs/picorv32a/src/my_base.sdc
set_propagated_clock [all_clocks]
report_checks -path_delay min_max -fields {slew trans net cap input pin} -format full_clock_expanded
echo $::env(CTS_CLK_BUFFER_LIST) #list of buffers
```
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/215105810-62e105d3-9373-4d99-9f1c-36d5e0ce46ab.png" height = "230"></p>
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/215106306-5f167f67-5a17-4cd2-b291-96d9f5655f53.png" height = "230"></p>
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/215105983-12de381b-93f1-4469-8bc3-2fdb791d59b7.png" height = "230"></p>
	
>	both hold and setup timing met. this is due to the clock buffers are inserted based on the CTS_CLK_BUFFER_LIST from left to right to meet the skew value. if the skew value is not met, then the next buffer is used, but the buffer will increase in size from left to right (skew values needs to be within the 10% of the max clock period)
	
</details>
	
<details><summary>Lab steps to observe impact of bigger CTS buffers on setup and hold timing</summary>
	
```
exit 
echo $::env(CTS_CLK_BUFFER_LIST)
set ::env(CTS_CLK_BUFFER_LIST) [lreplace $::env(CTS_CLK_BUFFER_LIST) 0 0]
echo $::env(CURRENT_DEF)
set ::env(CURRENT_DEF) /openLANE_flow/designs/picorv32a/runs/13-01_14-09/results/placement/picorv32a.placement.def
run_cts
```
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/215110303-b659e380-f00e-41cc-98ee-599d53bd4b8f.png" height = "230"></p>
	
```
openroad
read_lef /openLANE_flow/designs/picorv32a/runs/19-01_07-02/tmp/merged.lef
read_def /openLANE_flow/designs/picorv32a/runs/19-01_07-02/results/cts/picorv32a.cts.def
write_db pico_cts1.db
read_db pico_cts1.db
read_verilog /openLANE_flow/designs/picorv32a/runs/19-01_07-02/results/synthesis/picorv32a.synthesis_cts.v
read_liberty $::env(LIB_SYNTH_COMPLETE)
link_design picorv32a
read_sdc designs/picorv32a/src/my_base.sdc
set_propagated_clock [all_clocks]
report_checks -path_delay min_max -fields {slew trans net cap input pin} -format full_clock_expanded
```
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/215111942-f713e220-0488-493f-a765-b263d2937810.png" height = "230"></p>
	
>	timing improved a bit (buffer change from 1 to 2)
	
```
report_clock_skew -hold
report_clock_skew -setup
```
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/215113007-b23fbed1-9606-49d1-b1cf-3d72cd878364.png" height = "150"></p>
	
>	report clock skew for hold and setup
	
```
set ::env(CTS_CLK_BUFFER_LIST) [linsert $::env(CTS_CLK_BUFFER_LIST) 0 sky130_fd_sc_hd__clkbuf_1]
```
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/215113462-eb2d49cd-067e-41a6-82d3-c59fca331dd0.png" height = "70"></p>
	
>	add back to clkbuf 1
	
</details>
	
</details>
	
# Day-19
	
## Final steps for RTL2GDS using tritonRoute and openSTA
	
<details><summary>Routing and design rule check (DRC)</summary>
	
<details><summary>Introduction to Maze Routing Â LeeÂs algorithm</summary>
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/215386242-fc097f59-93c3-4cc4-af47-09d8e39cb682.png" height = "250"></p>
	
>	find best possible connection (shortest path and minimal zigzag lines) between 2 endpoint (source and target)
	
Note: physical design engineer = route (physical wire) algorithm = 2 different points which needs to be connected
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/215387726-74b7180c-727a-44ea-9d0d-e796b54527c8.png" height = "250"></p>
	
>	Lee's algorithm (maze routing). first, creates routing grid. then determines 2 points (source and target). next label the grid ground (adjacent of horizontal and vertical grid) continue labeling until reach the target
	
</details>
	
<details><summary>LeeÂs Algorithm conclusion</summary>
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/215388421-34bbb450-7fae-4136-a141-b4ab0b002ca2.png" height = "250"><img src = "https://user-images.githubusercontent.com/118953932/215388455-edb275ea-9861-492c-9168-bef4a2604326.png" height = "250"><img src = "https://user-images.githubusercontent.com/118953932/215388705-958f93a5-be07-49ab-9a80-1300bcef5189.png" height = "250"></p>
	
>	it will not do at the logical blockage. it will prefer the less zigzag route (left) which is the shortest one
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/215389082-b13ff3e3-34b2-4db5-8a21-fbb22ba5d116.png" height = "250"><img src = "https://user-images.githubusercontent.com/118953932/215389192-c3a0e1c6-5e6a-47b0-9897-f4dc771f3f91.png" height = "250"></p>
	
>	algorithm prefer lower number of bends (connecting 2 points with the shortest distance)
	
</details>
	
<details><summary>Design Rule Check</summary>
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/215403675-9f07de80-e3ad-4947-b660-da92a72f1fe9.png" height = "250"></p>
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/215404000-a2551083-0f85-4493-827e-acc69eb2b3b0.png" height = "100"><img src = "https://user-images.githubusercontent.com/118953932/215404299-42cef9e0-dad4-48e8-bae7-49e9c9ab2832.png" height = "100"></p>
	
DRC rules to be followed when performing the routing of design
	
1.	wire width (should be not less than a specified amount but can exceed)
	
2.	wire pitch (centre-to-centre distance of those 2 wires should be at least amount of distance spesified)
	
3.	wire spacing (minimum spacing should be followed which means can be more but cant be less)
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/215404653-ebacf2d0-86ae-4cdf-aa05-5cbb69ce06b9.png" height = "250"></p>
	
>	signal short (buffer tries to send signal tu ff2 but it can shorted because both are same wires at the same metal layer)

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/215404881-817cb55a-b76e-49c0-b20b-b438cc029c95.png" height = "250"></p>
	
>	solution: introduce one more layer at the top of it (upper metal layer wider than lower metal layer)
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/215405165-553cc655-62c6-4879-a868-c21b5d4747a3.png" height = "250"><img src = "https://user-images.githubusercontent.com/118953932/215405417-09d6971c-8acd-4484-b1c1-81c7517eb9cc.png" height = "250"></p>
	
>	although no more signal short but there are 2 new design rule to be check which are via width (should be no less than a certain value) and via spacing (the distance between 2 vias cannot be less than a specific distance)
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/215405685-1b13f1b4-ea9e-4785-9ff5-04bdc62b5f13.png" height = "250"></p>
	
>	parasitics extraction (resistances and capacitances of the wires are extracted and used for further processes)
	
</details>
	
</details>

<details><summary>Power Distribution Network and routing</summary>
	
<details><summary>Lab steps to build power distribution network</summary>
	
```
#in openlane (invoke openlane as previous)

echo $::env(CURRENT_DEF) #should be cts.def
	
gen_pdn #run power distribution network
```
	
Note: prep -design -tag **-overwrite** is used when want to create a fresh run with new configurations but without changing the tag name
	
>	LEF and DEF files are read. then it will create the gird and transfer the power and ground. the standard cells are placed in the standard cell rows (will need to have the power and ground lines along the side rows where the standard cells are placed) then, the straps are provided for the chip. from the power pads, the power goes into the straps. from the straps, it drills down into the standard cell rails
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/215444344-09859c4e-e506-41d6-8453-4611a0e0a697.png" height = "250"></p>


</details>	

<details><summary>Lab steps from power straps to std cell power</summary>
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/215434516-18189b0b-16ef-47ee-902e-4ebbdc620905.png" height = "250"></p>
	
>	power/ground pads (pastel red or blue coloured rectangle) power/ground rings (red or blue rectangle ring) power/ground strap (red or blue vertical line) power/ground rails (red or blue horizontal lines) 
	
power and ground flows:
	
power/ground pads -> power/ground ring -> power/ground straps -> power/ground rails
	
</details>
	
<details><summary>Basics of global and detail routing and configure TritonRoute</summary>
	
	
```
echo $::env(CURRENT_DEF) #will see change from CTS 1 to floorplan/pdn.def 
	
echo $::env(ROUTING_STRATEGY) #will get 0
	
run_routing
```

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/215437844-f1c36d1d-d7de-45b0-bbc0-304776cd1f74.png" height = "280"></p>
	
>	routing guideline in README.md
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/215437961-aece2a61-3160-4995-8257-2e8e255a0ad7.png" height = "80"></p>
	
>	run_routing complete
	
</details>
	
</details>
	
<details><summary>TritonRoute Features</summary>
	
<details><summary>TritonRoute feature 1 - Honors pre-processed route guides</summary>
	
-	Global Routing: Form routing guides that can route all the nets. The tool used is FastRoute.

-	Detailed Routing: Uses the global routing's guide to connect the pins with the least amount of wire and bends. The tool used is TritonRoute.
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/215407053-c263b913-dcad-41cf-a1bd-4ab6afc5ba64.png" height = "250"></p>
	
-	performs initial detail route
	
-	honors the preprocessed route guides (obtained after fast routes) i.e. attempts as much as possible to route within route guides
	
-	assumes route guides for each net satisfy inter-guide connectivity
	
-	works on proposed MILP-based (algorithm) panel routing scheme with intra-layer parallel (within a layer M1) and inter-layer sequential routing framework (in between layers M1, M2, M3). via does not happened during lower layer
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/215407923-6d03ea64-2400-48f5-9300-714a8159ab28.png" height = "250"></p>
	
>	after global route (done by FastRoute). output of the FastRoute is initial routing guide. it will divide not proper direction (supposed vertical but encounters horizontal) called spilitting. then, merging which is merging the edges. net, bridging which bridges additional upper layer. finally, preprocessed guides (M1 = vertical, M2 = horizontal)
	
</details>
	
<details><summary>TritonRoute Feature2 & 3 - Inter-guide connectivity and intra- & inter-layer routing</summary>
	
**Inter-guide connectivity**
	
-	two guides are connected if:
	-	they are on the same metal layer with touching edges, or
	-	they are on neighboring metal layers with a nonzero vertically overlapped area
	
-	each unconnected terminal i.e. pin of a standard-cell instance should have its pin shape overlapped by a route guide
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/215410686-5486e902-cb50-4990-9f03-ba0fec2ffa52.png" height = "250"></p>
	
>	dash line = panels. each routing guide is assign to one panel. routing in the higher layers will begin only if the routing of the bottom layers have been completed
	
</details>
	
<details><summary>TritonRoute method to handle connectivity</summary>
	
-	Inputs: LEF file, DEF file, and the Preprocessed route guides
	
-	Outputs: detailed routing solution with optimized wire-length and via count
	
-	Constraints: route guide honouring, connectivity constraints and design rules
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/215412091-75e668d4-72d8-4e60-8845-2afd33e04ad1.png" height = "250"></p>
	
>	access point and access point cluster
	
>	access point refers to the point where the via can be placed to allow connectivity between layers. the objective of the Mixed Integer Liner Programming (MILP) is to connect one access point to another access point optimally. first, choose one of the access points where the via should be dropped. second, determining how the first access point will connect to the next access point.
	
</details>
	
<details><summary>Routing topology algorithm and final files list post-route</summary>
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/215429480-196716df-6537-4438-966f-c2d9de2e868c.png" height = "250"></p>
	
>	for each APC, find the cost associated to it. then, minimum spanning tree, MST, between the APCs and the costs (minimal and optimal point between 2 APC).
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/215429961-48c4dfa8-3368-4b66-8543-dcc981d132ce.png" height = "250"></p>
	
>	memory that was taken up by the tool and the number of DRC violations (= 3) in the design port routing
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/215430267-ed835080-7ab4-40a2-886c-750d2e50455d.png" height = "150"></p>
	
>	modify or fix it manually to get rid of the violations
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/215430884-ad830c94-f85a-40d7-9055-e37157fbb731.png" height = "400"></p>
	
>	routing guides (less fastroute guide)
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/215431874-13c10dce-9ab2-4ea8-954f-2a801367245e.png" height = "200"></p>
	
>	extract parasitics (need to declare the LEF and the DEF first)
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/215432308-3b617f81-7161-4f6d-a29c-dd6781ee2f9c.png" height = "80"></p>
	
>	files created
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/215432681-6d3f59aa-e3d7-4f1e-b6d4-92d4592ca826.png" height = "80"></p>
	
>	 netlist modified due to the antenna diodes insertions happens
	
	
</details>
	
</details>
	
# Day-20
## Floorplanning and Power Planning Lab
	
```
git clone https://github.com/manili/VSDBabySoC.git
git clone https://github.com/bharath19-gs/VSDBabySoC_ICC2.git
git clone https://github.com/bharath19-gs/synopsys_ICC2flow_130nm.git
```
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/217689500-6560dbc2-6bf2-42bb-a635-741192902b97.png" height = "500"><img src = "https://user-images.githubusercontent.com/118953932/217689648-3568d92f-0f25-49f6-af12-ac45b2738952.png" height = "430"></p>
	
>	modify the vsdbabysoc.tcl (use own local file)
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/217690067-f6ae05ff-c0ff-486a-bf19-7cf31387a47b.png" height = "250"></p>
	
>	in dc_shell, source vsdbabysoc.tcl
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/217690775-e8b6ccd5-b606-4dde-86d7-d563f71b810c.png" height = "190"><img src = "https://user-images.githubusercontent.com/118953932/217690823-a6d95a05-1104-47a5-9046-74b4d3d5d5d9.png" height = "210"></p>
	
>	check_design before and after optimization done
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/217691341-4864d040-1449-43ad-8aa6-ad45506a5fac.png" height = "250"><img src = "https://user-images.githubusercontent.com/118953932/217691281-ae63c6cd-3389-4c79-a9d5-8ff9ff5120ad.png" height = "330"></p>
	
>	schematic design
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/217692403-27429af2-be79-41fe-9a00-5ec475100e60.png" height = "300"><img src = "https://user-images.githubusercontent.com/118953932/217692423-1cca0d90-6701-4cbd-a820-a700af765cee.png" height = "300"><img src = "https://user-images.githubusercontent.com/118953932/217692465-f1d86351-78c0-4009-b79f-acbed2b2de47.png" height = "320"></p>
	
>	report_area, report_timing, report_power
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/217714304-4cb40fa9-6f89-4a73-97d6-021ee038f53a.png" height = "450"></p>

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/217714493-745de464-43e2-42ea-a77b-08762512e1dc.png" height = "450"></p>
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/217714554-96f0fdfb-8cbf-4be6-a64f-edd37cb3faa9.png" height = "450"></p>

<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/217714607-52b7fc61-d6dd-4ac8-acd0-7bf61f367544.png" height = "450"></p>
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/217714638-08ec18e1-0f2a-420a-9da1-1f4e9522875e.png" height = "450"></p>
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/217714681-e9a33fd2-d587-4f35-8a2c-3ac2b88a0ab2.png" height = "450"></p>
	
>	modify all the files
	
-	7% core utilization
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/217714948-d0bb2dc3-2e2b-4334-b974-15469d0b9f50.png" height = "200"><img src = "https://user-images.githubusercontent.com/118953932/217715063-fb5f4ea2-355a-4d69-83c3-4c472ac282be.png" height = "300"></p>
	
>	flow completed. then, start_gui
	
<p align="center"><img src = "https://user-images.githubusercontent.com/118953932/217715469-1e2c5658-47f4-419d-85a7-dc36c2ece7e0.png" height = "300"><img src = "https://user-images.githubusercontent.com/118953932/217715345-be062c13-cbb6-4a89-80b7-9f3a2f67307e.png" height = "300"></p>
