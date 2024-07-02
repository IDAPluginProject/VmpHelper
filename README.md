# VmpHelper

a vmp-analysis ida plugin, currently under development...

only supports Vmp3.5 x86

## How to use

1、Place the Ghidra directory and Revampire.dll into the IDA plugin directory

2、Use ida to load demo.exe.

At 00401D7E，right click to pop up menu -> Revampire -> Mark as VmEntry

3、At 00401D70，right click to pop up menu -> Revampire -> Execute Vmp 3.5.0.

Then you may get a flow chart like the following:

![graph](graph.png)

## Current Target

1、Identify all handlers of vmp

2、Print out the complete flow chart of vmp

## Reference

ghidra:https://github.com/NationalSecurityAgency/ghidra

unicorn:https://github.com/unicorn-engine/unicorn

capstone:https://github.com/capstone-engine/capstone

keystone:https://github.com/keystone-engine/keystone

z3:https://github.com/Z3Prover/z3

cereal:https://github.com/USCiLab/cereal



## Sponsor this project

![赞助](sponsor.png)

