# cpf-checksum
Algebraic simplification of the usual description. [See here for example.](https://www.geradorcpf.com/algoritmo_do_cpf.htm)  [See also wikipedia page.](https://en.wikipedia.org/wiki/CPF_number)

```
//abc.def.ghi-jk

j=(a+2b+3c+4d+5e+6f+7g+8h+9i) mod 11

if(j==10) k=(b+2c+3d+4e+5f+6g+7h+8i) mod 11
else k=(9a+8b+7c+6d+5e+4f+3g+2h+i) mod 11

if(j==10) j=0
if(k==10) k=0
```

# Discussion
A clever use of the fact that 11 is a prime number close to 10. In Z_11, multiplication by a unit induces a bijection. This provides a protection in case two digits get swapped. For example, if we use j=(a+b+c+d+e+f+g+h+i) mod 11 instead, then all the permutations would share the same j. This protection is weakened by the fact that j+k = -(a+b+c+d+e+f+g+h+i) mod 11 most of the time.

The trade-off on using Z_11 is that a character is lacking from the set {0,1,2,3,4,5,6,7,8,9}, so 0 is used to represent 10. This introduces a slight statistical bias for 0, which is a small cost for using the Z_11 structure.

Finally, the special logic on j==10 is intriguing to me.
