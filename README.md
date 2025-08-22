# 8-Bit-Arithmetic-Operations-using-8085
## Aim:
To perform 8-bit arithmetic operations such as addition, subtraction, multiplication, and division using the 8085 microprocessor.
Apparatus Required:
•	Laptop with internet connection
## Algorithm:
## For Addition (With Carry Consideration):
1.	Load the first number from memory location 4200H into register A.
2.	Load the second number from memory location 4201H into register B.
3.	Add the contents of registers A and B.
4.	If carry is generated, store carry in 4301H.
5.	Store the sum in memory location 4300H.
## For Subtraction (Considering Greater Number):
1.	Load the first number from memory location 4200H into register A.
2.	Load the second number from memory location 4201H into register B.
3.	Compare A and B.
4.	If A < B, swap the values of A and B to ensure positive result.
5.	Subtract the content of B from A.
6.	Store the result in memory location 4300H.
## For Multiplication:
1.	Load the first number from memory location 4200H into register A.
2.	Load the second number from memory location 4201H into register B.
3.	Multiply A and B using repeated addition.
4.	Store the result in memory locations 4300H and 4301H (if required for higher bits).
## For Division:
1.	Load the dividend from memory location 4200H into register A.
2.	Load the divisor from memory location 4201H into register B.
3.	Perform division using repeated subtraction.
4.	Store the quotient in 4300H and remainder in 4301H.
## Program:

## Addition of two 8-bit numbers:

LDA 2050H   ; Load first number into Accumulator
MOV B, A   ; Copy to register B
LDA 2051H   ; Load second number into Accumulator
ADD B      ; Add B to Accumulator (A = A + B)
STA 2052H   ; Store result at memory location 2052
HLT        ; Stop program

## Subtraction of two 8-bit numbers.

LDA 4150H    ; Load first number (minuend) into accumulator
MOV B, A     ; Copy first number into B (save it)

LDA 4151H    ; Load second number (subtrahend) into accumulator
MOV C, A     ; Copy second number into C

MOV A, B     ; Restore first number into accumulator
SUB C        ; A = A - C = (First number - Second number)

STA 4152H    ; Store result at 4152H
HLT          ; Halt program

## Multiplication of two 8- bit nos. using repeated Addition

LDA 2050H      ; Load first number into Accumulator
MOV B, A      ; Store it in B (multiplier)
LDA 2051H      ; Load second number into Accumulator
MOV C, A      ; Store it in C (multiplicand)
MVI A, 00     ; Clear Accumulator for result
LOOP: ADD C   ; Add multiplicand to result
DCR B         ; Decrease multiplier by 1
JNZ LOOP      ; Repeat until multiplier = 0
STA 2052H      ; Store result in memory 2052H
HLT           ; Stop

## Division of two 8- bit nos. using repeated Subtraction.

LDA 2050H       ; Load dividend into Accumulator
MOV B, A       ; Store dividend in B
LDA 2051H       ; Load divisor into Accumulator
MOV C, A       ; Store divisor in C
MVI D, 00      ; Clear D (will hold Quotient)

LOOP: CMP C    ; Compare A with divisor
JC END         ; If A < C, jump to END
SUB C          ; A = A - C
INR D          ; Increment quotient
JMP LOOP       ; Repeat

END: MOV E, A  ; Store remainder into E
MOV A, D       ; Move quotient to A
STA 2052H       ; Store quotient at 2052H
MOV A, E       ; Move remainder to A
STA 2053H       ; Store remainder at 2053H
HLT            ; Stop

## Output:

## Addition of two 8-bit numbers.

<img width="1919" height="914" alt="Screenshot 2025-08-20 091129" src="https://github.com/user-attachments/assets/829b762c-311c-4eeb-9174-26ccee2b6f6b" />

## Subtraction of two 8-bit numbers.

<img width="1919" height="908" alt="Screenshot 2025-08-20 091627" src="https://github.com/user-attachments/assets/fd8ae1e8-201c-4920-aa5c-3a58ba532c20" />

## Multiplication of two 8- bit nos. using repeated Addition

<img width="1919" height="909" alt="Screenshot 2025-08-20 093014" src="https://github.com/user-attachments/assets/a3d30824-c66d-4fff-8a05-53e85ee4f6fb" />

## Division of two 8- bit nos. using repeated Subtraction.

<img width="1919" height="909" alt="Screenshot 2025-08-20 093458" src="https://github.com/user-attachments/assets/e42e1208-de1f-424c-9c53-ef2d5a3e3d29" />


## Result:
The 8-bit arithmetic operations using the 8085 microprocessor have been successfully executed and verified using memory access for input and output.
