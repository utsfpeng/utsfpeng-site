---
title: "Reverse Engineering"
date: 2019-02-25T10:24:52+11:00
draft: true
---

## Reverse Engineering

Today we were introduced to Reverse Engineering by Ruben Thijssen, a Application Security Manager from Symantec.

He demonstrated the use of Binary Ninja to reverse engineer high-level language (C) and disassemble it into Assembly Language.

He gave us a set of introductory challenges to reverse engineering and binary exploitation.

The session itself challenged us to think outside the box and be strategic at what we look for.

We were exposed to new tools such as Binary Ninja, GDB (GNU Debugger), PEDA (Python Exploit Development Assistance) and the use of x86 Opcode and Instruction Reference.

It was unlike anything I have ever seen. I really wanted to pick his brain since he had such a vase understanding of how systems work to a very low level perspective. He was able to recognise structures from the back of his hand and develop an idea of a problem from brief descriptions. It was amazing to see such mastery of assembly language.

### 0x01 - Abradolf Lincler Challenge

The first challenge that he posed to use was called "0x01 - Abradolf Lincler". This involved investigating a binary file which contains a hidden flag that we need to find in order to complete the challenge. Going in depth into the assembly instruction set was a first for me and I was really nervous at first due to the level of complexity. However, after trial and error along with Ruben's explanations, it started to make a bit more sense. It involved understanding the basic structure of the program through certain traits and patterns that occur commonly, such as recognising calls that are looping back and ones that split into two (for if/else statements) among other things.

I started off downloading using the commands:

```
git clone https://github.com/longld/peda.git ~/peda
echo "source ~/peda/peda.py" >> ~/.gdbinit
```

before running the binary file with:

```
./0x01-abradolf-lincler
```

followed by:

```
gdb 0x01-abradolf-lincler
```

which launched up GDB (GNU Debugger) and put a breakpoint on main using:

```
b main
```

afterwards I inspected with Binary Ninja and found that there was a main and 2 functions.

Upon using the x/s command for a closer inspection, we realised that there was a flag once decoded from binary to character constants.

{{< figure src="/img/rev-eng/abradolf-1.PNG">}}

{{< figure src="/img/rev-eng/abradolf-2.PNG">}}


## 0x02 - Morty Crypto

Morty Crypto involved some similar steps in the beginning:

```
./0x02-mortycrypto
gdb 0x02-mortycrypto
b main
r
```

Note: There is an XOR function in the main.

{{< figure src="/img/rev-eng/morty-1.PNG">}}

To understand what is actually happening when running the whole binary file of the application, we inspected the ELF graph to get a visual overview of what is going on.

{{< figure src="/img/rev-eng/morty-2.PNG">}}

Based on the view, we can tell that there is a loop which checks if a counter hits a certain value (27). Once it does, it moves to the else statement section of the code.

After it moves to the else statement, it has finished running the xor'ing process. Hence, we can use the starting instruction of the else statement as a breakpoint to look at hints about the flag. In my case, the assembly instruction mov eax, 0x0 was residing at the address 0x8049bc5 .

{{< figure src="/img/rev-eng/morty-3.PNG">}}


To find the flag, we need to look at the application through GDB after adding the breakpoint for the mov instruction.

```
b *0x8049bc5
```

So from start to finish,

```
./0x02-mortycrypto
gdb 0x02-mortycrypto
b main
b *0x8049bc5
r
continue
```
After you press enter on the continue, it will go through and decode the whole flag.



References

Ref: http://uts-cs.securitygrounds.org/reverse-engineering/0x00/index.html
