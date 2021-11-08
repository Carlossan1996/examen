#include "p16F887.inc"   
 	__CONFIG	_CONFIG1,	_INTRC_OSC_NOCLKOUT & _WDT_OFF & _PWRTE_OFF & _MCLRE_ON & _CP_OFF & _CPD_OFF & _BOR_OFF & _IESO_ON & _FCMEN_ON & _LVP_OFF 
 	__CONFIG	_CONFIG2,	_BOR40V & _WRT_OFF

RES_VECT  CODE    0x0000            
    GOTO    START                   

MAIN_PROG CODE                      
 
i equ 0x20
j equ 0x21
k equ 0x22
m equ 0x23
q1 equ 0x24
q2 equ 0x25
q3 equ 0x26
q4 equ 0x27
q5 equ 0x28
q6 equ 0x29
q7 equ 0x30
q8 equ 0x31
x1 equ 0x32
x2 equ 0x33
x3 equ 0x34
x4 equ 0x35
x5 equ 0x36
x6 equ 0x37
x7 equ 0x38
x8 equ 0x39 
a equ 0x40
w equ d'0'


START

    BANKSEL PORTA ;
    CLRF PORTA 
    BANKSEL ANSEL ;
    CLRF ANSEL 
    CLRF ANSELH
    BANKSEL TRISA 
    CLRF TRISA
    CLRF TRISB
    CLRF TRISC
    CLRF TRISD
    CLRF TRISE
    BCF STATUS,RP1
    BCF STATUS,RP0
    CLRF PORTA
    CLRF PORTB
    CLRF PORTC
    CLRF PORTD
    CLRF PORTE
    
    BCF STATUS, RP1 
    BSF STATUS, RP0 
    MOVLW b'00000000' 
    MOVWF TRISC 
    MOVLW b'00001111' 
    MOVWF TRISD
    BCF STATUS, RP0 
    
    
INITLCD
    BCF PORTA,0		
    MOVLW 0x01
    MOVWF PORTB
    
    BSF PORTA,1		
    CALL time
    BCF PORTA,1
    CALL time
    
    MOVLW 0x0C		
    MOVWF PORTB
    
    BSF PORTA,1		
    CALL time
    BCF PORTA,1
    CALL time
         
    MOVLW 0x3C		
    MOVWF PORTB
    
    BSF PORTA,1		
    CALL time
    BCF PORTA,1
    CALL time
    
    
INICIO
    BCF PORTA,0		
    CALL time
    
    MOVLW 0x01		
    MOVWF PORTB
    CALL exec
    
    BSF PORTA,0		
    CALL time
    
    
    BCF PORTA,0		
    CALL time
    
    MOVLW 0x80		
    MOVWF PORTB
    CALL exec
    
    BSF PORTA,0		
    CALL time
    
    
    MOVLW 'N'
    MOVWF PORTB
    CALL exec
    
    MOVLW 'U'
    MOVWF PORTB
    CALL exec
   
    MOVLW 'E'
    MOVWF PORTB
    CALL exec

    MOVLW 'V'
    MOVWF PORTB
    CALL exec
    
    MOVLW 'A'
    MOVWF PORTB
    CALL exec
    
    MOVLW ' '
    MOVWF PORTB
    CALL exec
    
    MOVLW 'C'
    MOVWF PORTB
    CALL exec
    
    MOVLW 'O'
    MOVWF PORTB
    CALL exec
    
    MOVLW 'N'
    MOVWF PORTB
    CALL exec
    
    MOVLW 'T'
    MOVWF PORTB
    CALL exec
    
    MOVLW 'R'
    MOVWF PORTB
    CALL exec
    
    MOVLW 'A'
    MOVWF PORTB
    CALL exec
    
    MOVLW ':'
    MOVWF PORTB
    CALL exec
    
    BCF PORTA,0		;command mode
    CALL time
    
    MOVLW 0xC0		;LCD position
    MOVWF PORTB
    CALL exec
    
    BSF PORTA,0		;data mode
    CALL time
    
    
    CALL numeros
    BTFSS w,0
    GOTO $-2
    MOVFW a
    MOVWF q1
    BCF w,0
    
    
   CALL numeros
    BTFSS w,0
    GOTO $-2
    MOVFW a
    MOVWF q2
    BCF w,0
    
    
    CALL numeros
    BTFSS w,0
    GOTO $-2
    MOVFW a
    MOVWF q3
    BCF w,0
    
    
    CALL numeros
    BTFSS w,0
    GOTO $-2
    MOVFW a
    MOVWF q4
    BCF w,0
    
    
    CALL numeros
    BTFSS w,0
    GOTO $-2
    MOVFW a
    MOVWF q5
    BCF w,0
    
    CALL numeros
    BTFSS w,0
    GOTO $-2
    MOVFW a
    MOVWF q6
    BCF w,0
    
    CALL numeros
    BTFSS w,0
    GOTO $-2
    MOVFW a
    MOVWF q7
    BCF w,0
    
    CALL numeros
    BTFSS w,0
    GOTO $-2
    MOVFW a
    MOVWF q8
    BCF w,0
    
 contra2: 
    BCF w,0
    BCF PORTA,0		
    CALL time
    
    MOVLW 0x90		
    MOVWF PORTB
    CALL exec
    
    BSF PORTA,0		
    CALL time
    MOVLW ' '
    MOVWF PORTB
    CALL exec
    
    MOVLW ' '
    MOVWF PORTB
    CALL exec
    
    MOVLW ' '
    MOVWF PORTB
    CALL exec
    
    MOVLW ' '
    MOVWF PORTB
    CALL exec
    
    MOVLW ' '
    MOVWF PORTB
    CALL exec
    
    MOVLW ' '
    MOVWF PORTB
    CALL exec
    
     MOVLW ' '
    MOVWF PORTB
    CALL exec
    
     MOVLW ' '
    MOVWF PORTB
    CALL exec
     MOVLW ' '
    MOVWF PORTB
    CALL exec
     MOVLW ' '
    MOVWF PORTB
    CALL exec
     MOVLW ' '
    MOVWF PORTB
    CALL exec
    MOVLW ' '
    MOVWF PORTB
    CALL exec
    MOVLW ' '
    MOVWF PORTB
    CALL exec
    MOVLW ' '
    MOVWF PORTB
    CALL exec
    
   BCF PORTA,0		
    CALL time
    
    MOVLW 0x90		
    MOVWF PORTB
    CALL exec
    
    BSF PORTA,0		
    CALL time
    
    MOVLW 'C'
    MOVWF PORTB
    CALL exec
    
    MOVLW 'O'
    MOVWF PORTB
    CALL exec
    
    MOVLW 'N'
    MOVWF PORTB
    CALL exec
    
    MOVLW 'F'
    MOVWF PORTB
    CALL exec
    
    MOVLW 'I'
    MOVWF PORTB
    CALL exec
    
    MOVLW 'R'
    MOVWF PORTB
    CALL exec
    
    MOVLW 'M'
    MOVWF PORTB
    CALL exec
    
    MOVLW 'A'
    MOVWF PORTB
    CALL exec
    
    MOVLW ' '
    MOVWF PORTB
    CALL exec
    
    MOVLW 'C'
    MOVWF PORTB
    CALL exec
    
    MOVLW 'O'
    MOVWF PORTB
    CALL exec
    
    MOVLW 'N'
    MOVWF PORTB
    CALL exec
    
    MOVLW 'T'
    MOVWF PORTB
    CALL exec
    
    MOVLW 'R'
    MOVWF PORTB
    CALL exec
    
    MOVLW 'A'
    MOVWF PORTB
    CALL exec
    
    MOVLW ':'
    MOVWF PORTB
    CALL exec
    
     BCF PORTA,0		;command mode
    CALL time
    
    MOVLW 0xD0		;LCD position
    MOVWF PORTB
    CALL exec
    
    BSF PORTA,0		;data mode
    CALL time
    
    
    CALL numeros
    BTFSS w,0
    GOTO $-2
    MOVFW a
    MOVWF x1
    BCF w,0
   
    CALL numeros 
    BTFSS w,0
    GOTO $-2
    MOVFW a
    MOVWF x2
    BCF w,0
    
    CALL numeros 
    BTFSS w,0
    GOTO $-2
    MOVFW a
    MOVWF x3
    BCF w,0
     
    CALL numeros 
    BTFSS w,0
    GOTO $-2
    MOVFW a
    MOVWF x4
    BCF w,0
    
    CALL numeros
    BTFSS w,0
    GOTO $-2
    MOVFW a
    MOVWF x5
    BCF w,0
    
    
    CALL numeros 
    BTFSS w,0
    GOTO $-2
    MOVFW a
    MOVWF x6
    BCF w,0
    
    
    CALL numeros 
    BTFSS w,0
    GOTO $-2
    MOVFW a
    MOVWF x7
    BCF w,0
    
    
    CALL numeros 
    BTFSS w,0
    GOTO $-2
    MOVFW a
    MOVWF x8
    BCF w,0 
   
    
    
    MOVFW q1
    XORWF x1,W
    BTFSS STATUS,Z
    CALL ig
    
    MOVFW q2
    XORWF x2,W
    BTFSS STATUS,Z
    CALL ig
    
    MOVFW q3
    XORWF x3,W
    BTFSS STATUS,Z
    CALL ig
    
    MOVFW q4
    XORWF x4,W
    BTFSS STATUS,Z
    CALL ig
    
    MOVFW q5
    XORWF x5,W
    BTFSS STATUS,Z
    CALL ig
    
    MOVFW q6
    XORWF x6,W
    BTFSS STATUS,Z
    CALL ig
    
    MOVFW q7
    XORWF x7,W
    BTFSS STATUS,Z
    CALL ig
    
    MOVFW q8
    XORWF x8,W
    BTFSS STATUS,Z
    CALL ig
    
    CALL bien
    
   
    
       
    GOTO INICIO
    
    
ig:
    BCF PORTA,0		
    CALL time
    
    MOVLW 0x01		
    MOVWF PORTB
    CALL exec
    
    BSF PORTA,0		
    CALL time 
    
    BCF PORTA,0		
    CALL time
    
    MOVLW 0x0C		
    MOVWF PORTB
    CALL exec
    
    BSF PORTA,0		
    CALL time
    
    
    BCF PORTA,0		
    CALL time
    
    MOVLW 0xC3		
    MOVWF PORTB
    CALL exec
    
    BSF PORTA,0		
    CALL time
    
    MOVLW 'C'
    MOVWF PORTB
    CALL exec
    
    MOVLW 'O'
    MOVWF PORTB
    CALL exec
    
    MOVLW 'N'
    MOVWF PORTB
    CALL exec
    
    MOVLW 'T'
    MOVWF PORTB
    CALL exec
    
    MOVLW 'R'
    MOVWF PORTB
    CALL exec
    
    MOVLW 'A'
    MOVWF PORTB
    CALL exec
    
    MOVLW 'S'
    MOVWF PORTB
    CALL exec
    
    MOVLW 'E'
    MOVWF PORTB
    CALL exec
    
    MOVLW 'N'
    MOVWF PORTB
    CALL exec
    
    MOVLW 'A'
    MOVWF PORTB
    CALL exec
    
    BCF PORTA,0		
    CALL time
    
    MOVLW 0x93		
    MOVWF PORTB
    CALL exec
    
    BSF PORTA,0		
    CALL time
    
    MOVLW 'D'
    MOVWF PORTB
    CALL exec
    
    MOVLW 'I'
    MOVWF PORTB
    CALL exec
    
    MOVLW 'F'
    MOVWF PORTB
    CALL exec
    
    MOVLW 'E'
    MOVWF PORTB
    CALL exec
    
    MOVLW 'R'
    MOVWF PORTB
    CALL exec
    
    MOVLW 'E'
    MOVWF PORTB
    CALL exec
    
    MOVLW 'N'
    MOVWF PORTB
    CALL exec
    
    MOVLW 'T'
    MOVWF PORTB
    CALL exec
    
    MOVLW 'E'
    MOVWF PORTB
    CALL exec
    
    
    BSF PORTC,0
    CALL time
    BTFSS PORTD,3
    GOTO $-3
   
    GOTO INICIO
    
bien:
    BCF PORTA,0		
    CALL time
    
    MOVLW 0x01		
    MOVWF PORTB
    CALL exec
    
    BSF PORTA,0		
    CALL time 
    
    BCF PORTA,0		
    CALL time
    
    MOVLW 0xC3		
    MOVWF PORTB
    CALL exec
    
    BSF PORTA,0		
    CALL time
    
    MOVLW 'C'
    MOVWF PORTB
    CALL exec
    
    MOVLW 'O'
    MOVWF PORTB
    CALL exec
    
    MOVLW 'N'
    MOVWF PORTB
    CALL exec
    
    MOVLW 'T'
    MOVWF PORTB
    CALL exec
    
    MOVLW 'R'
    MOVWF PORTB
    CALL exec
    
    MOVLW 'A'
    MOVWF PORTB
    CALL exec
    
    MOVLW 'S'
    MOVWF PORTB
    CALL exec
    
    MOVLW 'E'
    MOVWF PORTB
    CALL exec
    
    MOVLW 'N'
    MOVWF PORTB
    CALL exec
    
    MOVLW 'A'
    MOVWF PORTB
    CALL exec
    
    BCF PORTA,0		
    CALL time
    
    MOVLW 0x93		
    MOVWF PORTB
    CALL exec
    
    BSF PORTA,0		
    CALL time
    
    MOVLW 'C'
    MOVWF PORTB
    CALL exec
    
    MOVLW 'O'
    MOVWF PORTB
    CALL exec
    
    MOVLW 'N'
    MOVWF PORTB
    CALL exec
    
    MOVLW 'F'
    MOVWF PORTB
    CALL exec
    
    MOVLW 'I'
    MOVWF PORTB
    CALL exec
    
    MOVLW 'R'
    MOVWF PORTB
    CALL exec
    
    MOVLW 'M'
    MOVWF PORTB
    CALL exec
    
    MOVLW 'A'
    MOVWF PORTB
    CALL exec
    
    MOVLW 'D'
    MOVWF PORTB
    CALL exec
    
    MOVLW 'A'
    MOVWF PORTB
    CALL exec
    
    BSF PORTC,0
    CALL time
    BTFSS PORTD,3
    GOTO $-3
    
    GOTO INICIO
     
numeros:
    BSF PORTC,0
    CALL time
    BTFSC PORTD,0
    CALL numero1
    BTFSC PORTD,1
    CALL numero4
    BTFSC PORTD,2
    CALL numero7
    BCF PORTC,0
    BSF PORTC,1
    CALL time
    BTFSC PORTD,0
    CALL numero2
    BTFSC PORTD,1
    CALL numero5
    BTFSC PORTD,2
    CALL numero8
    BTFSC PORTD,3
    CALL numero0
    BCF PORTC,1
    BSF PORTC,2
    CALL time
    BTFSC PORTD,0
    CALL numero3
    BTFSC PORTD,1
    CALL numero6
    BTFSC PORTD,2
    CALL numero9
    BTFSC PORTD,3
    CALL borrar
    BCF PORTC,2
   
    
 
    RETURN
    

  
    
numero0:
   MOVLW d'0'
    MOVWF a
    MOVLW '*'
    MOVWF PORTB
    CALL exec
    BSF w,0
    BTFSC PORTD,0
    GOTO $-1
    RETURN
    
numero1:
    MOVLW d'1'
    MOVWF a
    MOVLW '*'
    MOVWF PORTB
    CALL exec
    BSF w,0
    BTFSC PORTD,0
    GOTO $-1
    RETURN

numero2:
    MOVLW d'2'
    MOVWF a
    MOVLW '*'
    MOVWF PORTB
    CALL exec
    BSF w,0
    BTFSC PORTD,0
    GOTO $-1
    RETURN

numero3: 
    MOVLW d'3'
    MOVWF a
    MOVLW '*'
    MOVWF PORTB
    CALL exec
    BSF w,0
    BTFSC PORTD,0
    GOTO $-1
    RETURN
    
numero4:
    
    MOVLW d'4'
    MOVWF a
    MOVLW '*'
    MOVWF PORTB
    CALL exec
    BSF w,0
    BTFSC PORTD,1
    GOTO $-1
    RETURN
  
numero5:
    MOVLW d'5'
    MOVWF a
    MOVLW '*'
    MOVWF PORTB
    CALL exec
    BSF w,0
    
    BTFSC PORTD,1
    GOTO $-1
    RETURN

numero6:
    MOVLW d'6'
    MOVWF a
    MOVLW '*'
    MOVWF PORTB
    CALL exec
    BSF w,0
    BTFSC PORTD,1
    GOTO $-1
    RETURN
 
numero7: 
    MOVLW d'7'
    MOVWF a 
    MOVLW '*'
    MOVWF PORTB
    CALL exec
    BSF w,0
    BTFSC PORTD,2
    GOTO $-1
    
    RETURN

numero8:  
    MOVLW d'8'
    MOVWF a
    MOVLW '*'
    MOVWF PORTB
    CALL exec
    BSF w,0
    BTFSC PORTD,2
    GOTO $-1
    RETURN
    
numero9:
    MOVLW d'9'
    MOVWF a
    MOVLW '*'
    MOVWF PORTB
    CALL exec
    BSF w,0
    BTFSC PORTD,2
    GOTO $-1
    RETURN
    

exec

    BSF PORTA,1		;exec
    CALL time
    BCF PORTA,1
    CALL time
    RETURN

    
    

    
time
    CLRF i
    MOVLW d'10'
    MOVWF j
ciclo    
    MOVLW d'80'
    MOVWF i
    DECFSZ i
    GOTO $-1
    DECFSZ j
    GOTO ciclo
    RETURN
    

tiemp
    
    movlw d'127' 
    movwf m
mloop1
    decfsz m,f
    goto mloop1
    movlw d'25' 
    movwf i
iloop1
    nop 
    movlw d'62' 
    movwf j
jloop1
    nop 
    movlw d'74' 
    movwf k
kloop1
    decfsz k,f
    goto kloop1
    decfsz j,f
    goto jloop1
    decfsz i,f
    goto iloop1
    return 
			

borrar:
    
    CALL tiemp
    GOTO contra2
   
    END
