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
