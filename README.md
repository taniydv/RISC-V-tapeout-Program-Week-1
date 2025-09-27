<img width="639" height="326" alt="Screenshot 2025-09-26 132504" src="https://github.com/user-attachments/assets/26510334-1d44-4326-849a-c18ae785e809" /># RISC-V-tapeout-Program-Week-1
Continuing to the Journey of RISC-V Let's study the basics of simulation, synthesis with the lab experiments. 
Week 1 focuses on different aspects like learning the basic flow of simulation and synthesis. Learning the basics of different combinational and sequential circuits with the fine way of coding. Also, learned and exposed to hands on training experience on generating netlist and doing the gate level simulation. We also learned about the good way of coding in order to prevent the occurrence of inferred latches by synthesizer.

### DAY 1: Introduction to Open-source simulator iverilog
Day 1 deals with the introduction of basics simulator, design, testbench and the basics of simulation flow with the synthesizer tool i.e yosys. Lab of this day consists of the setting the environment and to do work on iverilog and gtkwave. Yosys is a synthesizer tool which is used to convert the RTL code into netlist. In yosys the design and the library file containing the information of standard cell is given which it generate the corresponding netlist file.
     1. Environment setup
     <img width="809" height="535" alt="Screenshot 2025-09-25 000024" src="https://github.com/user-attachments/assets/a9e7cac6-9ada-4a5b-b3be-032c8f838ba3" />
<img width="1770" height="482" alt="Screenshot 2025-09-25 021316" src="https://github.com/user-attachments/assets/6f0a486e-d9cc-4320-a5a1-81569d679e42" />
     2. Iverilog and GTKwave: Done simulation of good_mux
     These are invoke using : 
     iverilog good_mux.v tb_good_mux.v
     
     ./a.out
     
     gtkwave tb_good_mux.vcd
     
     <img width="1920" height="1080" alt="Screenshot 2025-09-25 022247" src="https://github.com/user-attachments/assets/f292da63-4e25-40c7-b6ec-eb4ce4e457b1" />
     3. Yosys: Yosys is invoke using: 
     yosys
     read_liberty -lib ../lib/sky130fd_sc_hd__tt_025c_1v80.lib
     read_verilog good_mux.v
     synth -top good_mux
     abc -liberty ../lib/sky130fd_sc_hd__tt_025c_1v80.lib
     show
     write_verilog -noattr good_mux_net.v
     
<img width="615" height="592" alt="Screenshot 2025-09-25 031103" src="https://github.com/user-attachments/assets/80f7b646-3f96-4f39-8ec4-ca5160f48d9e" />
Netlist is shown as: 
<img width="871" height="497" alt="Screenshot 2025-09-25 032317" src="https://github.com/user-attachments/assets/360d0690-3dc3-46b2-bba5-5bdfd15e1139" />

### DAY 2: Introduction to .lib
Day 2 deals with the introduction of librsry file and the information it contains. "sky130fd_sc_hd__tt_025c_1v80.lib" this is the library file containing the parameters like process variations, voltage and temperature. 
<img width="635" height="993" alt="Screenshot 2025-09-25 034228" src="https://github.com/user-attachments/assets/2ed22908-7bf6-48b3-86ea-7e813e52bdf7" />

Here, tt stands for typical process, o25c is the temperature with 1v80 as the voltage. In this we also learn about the hierarchical and flat synthesis. here we synthesize the multiple_modules.v file having different submodules. 
<img width="764" height="182" alt="Screenshot 2025-09-25 042704" src="https://github.com/user-attachments/assets/a051cb4f-dc01-4f3a-852f-928bd2c99958" />
In this we also synthesize the submodule level.
<img width="609" height="214" alt="Screenshot 2025-09-25 044811" src="https://github.com/user-attachments/assets/4d0d2281-7fec-4fd0-8066-e6dc2cb3b630" />
After this, we learned about the basics of flip-flop and the variation in output depending on the synchronous/asynchronous set/reset. Following are the attachments of gtkwave wave of the flip-flop working under different conditions.
<img width="1819" height="427" alt="Screenshot 2025-09-26 070628" src="https://github.com/user-attachments/assets/fffd240e-6749-46ac-bfb5-e9f81bd945b8" />
<img width="1813" height="422" alt="Screenshot 2025-09-26 070912" src="https://github.com/user-attachments/assets/8718583f-1191-4e6f-a66e-c75e150450e6" />

<img width="1836" height="418" alt="Screenshot 2025-09-26 071126" src="https://github.com/user-attachments/assets/e3b74634-92aa-4297-bcf2-76d3f3dc9726" />
<img width="1849" height="313" alt="Screenshot 2025-09-26 072832" src="https://github.com/user-attachments/assets/f3066bb9-3436-4e84-be90-8532cf80151d" />
<img width="1846" height="317" alt="Screenshot 2025-09-26 073031" src="https://github.com/user-at<img width="1853" height="339" alt="Screenshot 2025-09-26 073219" src="https://github.com/user-attachments/assets/ee8a00c2-5b04-48e9-bdd5-dd96e6c59177" />
tachments/assets/e8d613ed-051f-4124-9224-818f0d2898e0" />

We also look at the special cases of multiply where only the last bit is appending with 0 when multiply by even factor while when there is odd factor there is only replica of same input.
<img width="665" height="163" alt="Screenshot 2025-09-26 120408" src="https://github.com/user-attachments/assets/32db935b-9663-4f0b-b4e3-11e0a966f77d" />
This doesn't require the mapping.

<img width="796" height="291" alt="Screenshot 2025-09-26 113200" src="https://github.com/user-attachments/assets/2920a5a8-5cc4-47d6-9d5c-187a91f3fb52" />

### DAY 3: Combinational and Sequential Optimisations
Day 3, we learned about the basics of combinational and sequential logic optimisations.
    1.Combinational logic optimisation means squeezing the logic to get the most optimized design. It is done through constant propagation and using Boolean logic optimisation. In the opt_check.v files are used. Synthesis involves the following steps:
    yosys
    read_liberty -lib ../lib/sky130fd_sc_hd__tt_025c_1v80.lib
    read_verilog opt_check.v
    synth -top opt_check
    opt_clean -purge
    abc -liberty ../lib/sky130fd_sc_hd__tt_025c_1v80.lib
    show
    <img width="600" height="148" alt="Screenshot 2025-09-26 125707" src="https://github.com/user-attachments/assets/3ed6c222-1cdc-417a-864e-20de72c5aef6" />
Similarly done for different files like opt_check2.v, multiple_module_opt.v

<img width="639" height="326" alt="Screenshot 2025-09-26 132504" src="https://github.com/user-attachments/assets/75ecd973-aeec-4436-a556-5ffe43674de5" />

    2. Sequential logic optimization: It involves two methods: Basic which is a sequential constant propagation and second one is advanced which involves state optimisations, retiming and sequential logic cloning.
    We done the optimisation of dff_const4.v and dff_const5.v files.
    # dff_const4.v
    <img width="559" height="1011" alt="Screenshot 2025-09-27 083918" src="https://github.com/user-attachments/assets/4adab8a7-7942-4333-a9b2-6ea79372d27b" />

    <img width="1015" height="290" alt="Screenshot 2025-09-27 083558" src="https://github.com/user-attachments/assets/fbba6cef-6d7d-4e04-b332-760c30b7bdfd" />

    # dff_const5.v
    <img width="519" height="856" alt="Screenshot 2025-09-27 084004" src="https://github.com/user-attachments/assets/6b64f25b-3ef0-4460-a940-3d130e8dfb13" />
<img width="984" height="343" alt="Screenshot 2025-09-27 084339" src="https://github.com/user-attachments/assets/db50035f-5175-4a09-9bd9-51f243730a25" />

On this day we also learned the sequential optimisation for unused outputs. Here we use the file counter_opt.v, in this all the three bits are used.
<img width="627" height="261" alt="Screenshot 2025-09-27 090121" src="https://github.com/user-attachments/assets/30b1297c-b59c-486c-9b26-35468ac539db" />

<img width="1846" height="424" alt="Screenshot 2025-09-27 092629" src="https://github.com/user-attachments/assets/50e9783e-a19c-4cea-b918-334b15dfc97f" />

In the below attached code only one bit is used while ither two are unused and the code and the netlist is look like as:
<img width="993" height="292" alt="Screenshot 2025-09-27 090037" src="https://github.com/user-attachments/assets/f28fbf2e-2008-4ae5-a245-09fcffa8374f" />

<img width="1845" height="232" alt="Screenshot 2025-09-27 085457" src="https://github.com/user-attachments/assets/0a944f07-7619-4be9-9ae3-99b4dd9e485f" />

### DAY 4: Introduction to Gate level simulation
Day 4 deals 

### DAY 5

# Acknowledgement
I'm grateful to the VSD team for this RISC-V tapeout program.
