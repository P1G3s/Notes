### NET0
Assuming:
```c
wanted = ‭1094861636‬ (0x41424344)
sprintf(fub, "%d", wanted);

if(write(0, &wanted, sizeof(wanted)) != sizeof(wanted)) {
    errx(1, ":(\n");
}

if(fgets(buf, sizeof(buf)-1, stdin) == NULL) {
    errx(1, ":(\n");
}
q = strchr(buf, '\r'); if(q) *q = 0;
q = strchr(buf, '\n'); if(q) *q = 0;

if(strcmp(fub, buf) == 0) {
    printf("you correctly sent the data\n");
} else {
    printf("you didn't send the data properly\n");
```
We have:

- fub = "‭1094861636‬" (0x41424344)

- &wanted --> &wanted+sizeof(wanted) = \x44\x43\x42\x41 (‭how 1094861636‬ is stored in mem in hex value) **(little endian - LSB at lowest address)**

- write(...) writes "\x44\x43\x42\x41" to client socket which client received as characters "DCBA" translated through ASCII ([ASCII Strings are not affected by little-endian, still be operated from lower address to higher address](https://stackoverflow.com/questions/1568057/ascii-strings-and-endianness))

Solution:
- Encode() received **string** to **hex**
- Unpack() **hex** to **int**
- Str() **int** to **string**
- Send() **string** to server
