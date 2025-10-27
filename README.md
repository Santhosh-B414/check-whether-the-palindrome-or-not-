# MPMC_SKILL_ASSESSMENT_1
# PALINDROME OR NOT USING 8086 

## AIM
To write and execute an 8086 assembly language program to check whether a given number is a palindrome or not.

---

## APPARATUS REQUIRED
- Personal computer with DOSBOX Software 

---

## ALGORITHM

1.Start the program.

2.Load the given number into a register (say AX).

3.Copy the number to another register for comparison later.

4.Initialize the reverse value as 0.

5.Divide the number by 10 repeatedly to extract the last digit.

6.Multiply the reverse by 10 and add the remainder to build the reversed number.

7.Repeat until the number becomes 0.

8.Compare the reversed number with the original number.

9.If both are equal, display “Palindrome”; otherwise, display “Not Palindrome”.

10.Stop the program.

---

## FLOWCHART
<img width="683" height="1024" alt="image" src="https://github.com/user-attachments/assets/68b0f588-dd52-45be-800c-69e86236d55a" />

---

## PROGRAM
```asm
.model small
.stack 100h
.data
num dw 12321
temp dw ?
rev dw 0
rem dw 0
msg1 db 0Ah,0Dh,'The number is a Palindrome.$'
msg2 db 0Ah,0Dh,'The number is NOT a Palindrome.$'

.code
main proc
    mov ax,@data
    mov ds,ax

    mov ax,num
    mov temp,ax
    mov rev,0

reverse_loop:
    mov dx,0
    mov bx,10
    div bx
    mov rem,dx
    mov ax,rev
    mov bx,10
    mul bx
    add ax,rem
    mov rev,ax

    mov ax,temp
    mov bx,10
    div bx
    mov temp,ax
    cmp temp,0
    jne reverse_loop

    mov ax,rev
    cmp ax,num
    je palindrome
    jne not_palindrome

palindrome:
    mov dx,offset msg1
    mov ah,09h
    int 21h
    jmp end_program

not_palindrome:
    mov dx,offset msg2
    mov ah,09h
    int 21h

end_program:
    mov ah,4Ch
    int 21h
main endp
end main



```
## OUTPUT

![palindrome](https://github.com/user-attachments/assets/c213fd8d-eb9e-4868-9980-dcf3bb1ec2b5)




---


## RESULT

Thus, the 8086 Assembly Language Program to check whether a given number is a palindrome or not has been successfully executed and the output was verified.

---
