<b>Goal</b>

This project can be broken down into two distinctive parts:<br>
• The assembler: this is the program that will compile your champions and translate them from the language you will write them in (assembly language) into “Bytecode”.Bytecode is a machine code, which will be directly interpreted by the virtual
machine.<br>
• The virtual machine: It’s the “arena” in which your champions will be executed.
It offers various functions, all of which will be useful for the battle of the champions.
Obviously, the virtual machine should allow for numerous simultaneous processes;
we are asking you for a gladiator fight, not a one-man show simulator.

<b>The assembler</b>

Your virtual machine will execute a machine code (or “bytecode”) that will be
generated by your assembler. The assembler (the program) will get a file written in
assembly language as argument and generate a champion that will be understood
by the virtual machine.<br>
• It will run like that:<br>
   ./asm mychampion.s<br>
• It will read the assembly’s code processed from the file .s given as argument, and
write the resulting bytecode in a file named same as the argument by replacing the
extension .s by .cor.<br>
• In case of an error, you will need to display a relevant message on the standard
error output and not create the .cor file.<br>

<b>The virtual machine</b>

• Each process will have available the following exclusive elements available:<br>

◦ REG_NUMBER registries, each of which are the size REG_SIZE octets. A
registry is a small memory “box” with only one value. On a real machine, it
is an internal of the processor and as a result very FAST to access.<br>
◦ A PC ("Program Counter"). This is a special registry that only contains, within
the memory of the virtual machine, the address of the next set of instructions
to code and execute. Very useful to figure out where we are at in the execution,
giving us tips on when to write stuff in the memory...<br>
◦ A flag named carry, if the latest operation was successful. Only certain operations can modify the carry.<br>

• The number of the player is generated by the machine or specified at launch and is
given to the champions via the r1 registry of their first process at startup. All the
other registries are at 0, except PC.<br>
• The champions are charged within the memory so that they can space out evenly
their entry points.<br>
• The virtual machine will create a memory space dedicated to the combat of the
players, it will then load each champion and their associated processes and execute
them sequentially until they die.<br>
• Every CYCLE_TO_DIE cycles, the machine needs to make sure that each process
has executed at least one live since the last check. A process that does not abide
by this rule will be killed immediately with a virtual foamy bat (bonus for sound
effect!)<br>
• If during one of those checkup we notice that there has been at least one NBR_LIVE
execution of live since the latest check up, we will decrease CYCLE_TO_DIE of
CYCLE_DELTA units.<br>
• The game is over when all processes are dead.
