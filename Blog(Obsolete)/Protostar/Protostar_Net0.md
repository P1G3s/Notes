### NET0
#### 1 done
- (1). struct.pack("I",1900401144) in python
- (2). type the output from (1)
```
user@protostar:~$ echo -e "`cat`"|netcat 127.0.0.1 2999
Please send '1900401144' as a little endian 32bit int
\xf8\xd1Eq
Thank you sir/madam
```

- what server reads
```
[pid  6589] read(0, "\370\321Eq", 4)    = 4
```
<br>


#### 2 done
- (1). (DEC)1052496937 = (HEX)‭3EBBD429‬
- (2). type \x29\xd4\xbb\x3e
```
user@protostar:~$ echo -e "`cat`"|netcat 127.0.0.1 2999
Please send '1052496937' as a little endian 32bit int
\x29\xd4\xbb\x3e
Thank you sir/madam
```
- what client send (after echo -e)
```
user@protostar:~$ echo -e "\x29\xd4\xbb\x3e"
)Ի>
```
- what server reads
```
[pid  6593] read(0, ")\324\273>", 4)    = 4
```
<br>


#### 3 failed (without echo -e "")
- (1). (DEC)‭1218377378‬ = (HEX)‭‭48 9E F6 A2‬‬
- (2). type \xa2\xf6\x9e\x48
```
user@protostar:~$ cat|netcat 127.0.0.1 2999
Please send '1218377378' as a little endian 32bit int
\xa2\xf6\x9e\x48
I'm sorry, you sent 845248604 instead
```
- what server reads
```
[pid  6597] read(0, "\\xa2", 4)         = 4
```

### Summary
- `echo -e ""` translate the content start with "\x" _("\x" indicates a hexadecimal character escape)_ to **ASCII characters**, which will be sent to server later.
- The return value of struct.pack() is already translated to ASCII character (Some might not be because their value is out of the range of ASCII).
- In Example 3, special character seems to be escaped to a literal before server reads it, thats why echo -e is needed, to enable interpretation of "\".
