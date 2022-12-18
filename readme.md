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
