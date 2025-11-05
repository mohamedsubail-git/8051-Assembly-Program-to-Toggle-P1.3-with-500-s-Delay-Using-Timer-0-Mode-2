# 8051-Assembly-Program-to-Toggle-P1.3-with-500-s-Delay-Using-Timer-0-Mode-2

# MPMCSKILL_ASSESSMENT2

## AIM
To write an 8051 assembly language program to generate a 2-second delay using Timer 0 in Mode 1 and to blink an LED connected to Port 3.7 continuously.
---

## APPARATUS REQUIRED
- Personal computer with Keil software

---

### Algorithm

**Algorithm:**

1. Start the program.
2. Set Port 3.7 as output (for LED).
3. Configure **Timer 0 in Mode 1 (16-bit timer mode)**.
4. Load initial count values in **TH0** and **TL0** for 2-second delay.
5. Start Timer 0.
6. Wait for the **Timer 0 overflow flag (TF0)** to be set.
7. Stop Timer and clear the overflow flag.
8. Toggle the LED connected to **P3.7**.
9. Repeat steps 4–8 continuously.




---

## FLOWCHART
<img width="311" height="467" alt="image" src="https://github.com/user-attachments/assets/abb8f483-7508-4fdb-a9cb-1a10b4d1abba" />


---

## PROGRAM
```asm
ORG 0000H           
MAIN:
    MOV P3, #0FFH     
BLINK:
    CLR P3.7            
    ACALL DELAY_2SEC   
    SETB P3.7           
    ACALL DELAY_2SEC   
    SJMP BLINK          
DELAY_2SEC:
    MOV TMOD, #01H      
    MOV R2, #31         
TIMER_LOOP:
    MOV TH0, #0FCH    
    MOV TL0, #0CH      
    SETB TR0            
WAIT_OVERFLOW:
    JNB TF0, WAIT_OVERFLOW 
    CLR TR0           
    CLR TF0            
    DJNZ R2, TIMER_LOOP 
    RET
END


```
OUTPUT

<img width="1145" height="647" alt="sa2 output " src="https://github.com/user-attachments/assets/35eff1f6-cd41-47bc-9460-fd7524981247" />

---


RESULT

The assembly language program was successfully executed on the 8051 microcontroller.
An LED connected to Port 3.7 blinked ON and OFF at an interval of 2 seconds, confirming that Timer 0 in Mode 1 generated the required delay accurately.
---


