### Data(To-be-organized)
- The Largest Negative Denormalized Floating points Value is NOT -0
- Difference between !a and ~a
- 0x2020+(0x1fff....e)*8
```
	//Watch out for the negative value, which can simplify the complication
	=0x2020+(0001111....1110)bin*8
	=0x2020-(1110000....0010)bin*8
	=0x2020-(0000000...10000)bin
	=0x2020-0x10=0x2010
```