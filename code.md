```assembly
section .text
	global _start

_start:
	mov ecx,[factorialBase]; designate number to take the factorial of as counter index
	mov eax,[factorialBase]; designate eax as the iterative value of the factorial
	loop iterate; decrement index and begin calculation

iterate:
	imul eax,ecx; multiply current value of factorial by current index
	loop iterate; decrement index and loop, exits when index = 0

	mov [factorialValue],eax; store calculated value of factorial in uninitialized variable
	jmp exit; terminate program

exit:
	mov eax,1
	int 0x80

section .data
	factorialBase dd 6; numerical value to calculate the factorial of

segment .bss
	factorialValue resb 4; result of the factorial calculation will be stored in this uninitialized variable
```
