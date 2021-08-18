# PICcode2LaTeX
PIC Assembler syntax and style for latex lstlisting package.

## Features
1. The 35 instructions for the PIC16F882/883/884/886/887
2. All special function registers
3. Some directives and keywords
4. Easily extended for other devices

You can change the colors or other parameters as letter size or break long lines option.

## Usage

Copy the PIC16F887.tex file in your project folder and add it to your main file.

```latex
\usepackage{listings} % Environment needed to paste the code inside of it

% Add the file in the preamble (before \begin{document}) using:
\input{PIC16F887}
```
Now you just need to paste your code inside a listing environment. Example:

```latex
\begin{lstlisting}
C_P:    NOP
		
	CALL T1A
		
	CALL T1B
		
	CALL T2A
		
	CALL T2B
		
	GOTO C_P
	;-------------------------------------------------------------------------------
T1A:	MOVLW	0x00	;T1CKPS1:T1CKPS0 = 11 | 0.52428[s]
	MOVWF	TMR1H
	MOVLW	0x00
	MOVWF	TMR1L
T1AX:	BTFSS	PIR1,PIR1_TMR1IF_POSITION
	GOTO	T1AX			    ;if TMR1IF == 0 then repeat
	BCF	PIR1,PIR1_TMR1IF_POSITION   ;if TMR1IF == 1 then reset TMR1IF
	RETURN
\end{lstlisting}
```

### Block comment
![Preview](https://raw.github.com/hasecilu/PICcode2LaTeX/main/images/Example.png)

### Small code
![Preview](https://raw.github.com/hasecilu/PICcode2LaTeX/main/images/Example2.png)
