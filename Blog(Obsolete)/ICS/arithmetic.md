# ICS:Arithmetic

```mermaid
graph LR;
	Unsigned1[Unsigned]
	Signed1[Signed]
	Binary1[Binary]

	Unsigned1	-->|U2B| Binary1
	Binary1		-->|"B2T (Two's complement)"| Signed1 
	Signed		-->|"T2B (Two's complement)"| Binary
	Binary		-->|B2U| Unsigned
```

<hr>
----|------Signed------|------Signed & Unsigned------|------Unsigned------|---- <br>
[TMIN]&emsp;&emsp;&emsp;&emsp;&emsp;&nbsp;[0]&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&ensp;[TMAX]&emsp;&emsp;&emsp;&emsp;&emsp;[UMAX]



```mermaid
graph LR;
	Binary		-->|"<0 && >=TMIN"|	b["Unsigned = Sign+2^(w-1)+2^(w-1)"]
	Binary		-->|">=0 && <=TMAX"|	a["Signed == Unsigned"]
	Binary		-->|">TMAX && <=UMAX"|	c["Signed = Unsigned-2^(w-1)-2^(w-1)"]
```
