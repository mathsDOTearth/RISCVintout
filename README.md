# RISCVintout
RISC-V assembly program to output an integer to the terminal

When working in Assembly Language, you are not getting any short cuts in life. If you want to output a single integer you need to add 48 to it to turn it in to an ASCII numeric character and then output that single character with a system call to the Linux write syscall.

Things get more complicated when you want output a multi-digit integer. First you need to split the number in to individual characters by getting the modulus 10 of the number, add 48 and put that on a stack, then divide the number by 10 and repeat until there are no more digets left in the integer

Finally we pop each ascii number off the stack and send to stdout with a syscall. We loop this action until the stack is empty.

# Assemble and Run
```
as -mno-relax -o intout.o intout.s
ld -o intout intout.o
./intout
```
