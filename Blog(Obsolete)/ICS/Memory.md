# Memory&Encoding
### Example (in C)
```c
int x = 0x12345678
x = (char)x	 //when x gets read from memory, only reads 1 byte instead of 4 bytes. 
int x = 0x12345678
*((unsigned char*)&x)// 0x78 
```
1. compiler uses &x to locate data, and reads "sizeof(unsigned char)" bytes from it 
2. which also means the first byte that the address(&x) indicates is the LSB of (int x).
3. unsigned char* --> read 1 byte, when printf, print 1 byte (in fact printf doesnt know the type of the pointer, derefference is done by compiler).


### Type Casting
**How compiler casts type**

```
/*
int x = 0x12345678;
x = (char)x;
*/

movl       $0x12345678,0xc(%rsp)	//int x = 0x12345678
movsbl     0xc(%rsp),%eax
movsbl     %al,%eax			//This instruction preserve the lower 8 bits and clear the higher bits to zero (movsbl(ATT) = movsx(intel)
mov        %eax,0xc(%rsp)
```

**How Compiler find out every value's type and use specific code for each value like above? (It just do)**
