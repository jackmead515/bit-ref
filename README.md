## SYMBOLS

`&` - and - both values are 1

`|` - or - one or the other is 1

`^` - xor - if only one value is 1

`~` - not - flips the bit

`<<` - left shift - shifts the bits left, same thing as multiplying by 2! COOL!
```
00010110 << 00000010 = 01011000
22 * 2 * 2 = 88
```

`>>` - right shift - shifts bits to the right, same thing as diving by 2, with rounding down! COOL!
```
00010110 >> 00000010 = 00000101
22 / 2 / 2 = 5
```

## BIT MASKING
A mask is just a positional reference to the bit that needs to be set.

### SETTING A BIT AT POSITION

x = 000000, 6 bits.
If I want to clear the second bit (or the 4th column from the right) to 1, I make this mask:<br/>
`mask = 1 << 4` or `mask = 1 << 000100`<br/>
`x = x | mask` or `x |= mask` which is `000000 | 010000`

### CLEARING A BIT AT POSITION

x = 001011, 6 bits.
If I want to set the third bit (or the 3th column from the right) to 0, I make this mask:<br/>
`mask = 1 << 3` or `mask = 1 << 000011`<br/>
`x = x & ~mask` or `x &= ~mask`<br/>
`x =    001011`<br/>
`m =    001000`<br/>
`~m =   110111`<br/>
`x&~m = 001011 & 110111 = 000011 = 3`<br/>

### FLIPPING A BIT

x = 001011, 6 bits
If I want to flip the second bit (or 4th column from the right) to 1, I make this mask:<br/>
`mask = 1 << 4` or `mask = 1 << 000100`<br/>
`x = x ^ mask` or `x ^= mask`

### TESTING IF A BIT IS SET OR NOT

x = 001011, 6 bits
Testing the second bit (4th column from right, 1st column from left), I make this mask:<br/>
`mask = x >> 000100`<br/>
`shifted = mask & 1`<br/>
Shifted will be 1 if set, 0 if not set

### CHECK IF NUMBER IS EVEN OR ODD

x = 001011, 6 bits<br/>
`x & 1 == 0` or `001011 & 000001 = 000001`

### CHECK IF POWER OF TWO

x = 001011, 6 bits<br/>
`(x & x-1 == 0)` or `(001011 & 001011 - 000001)` or `(001011 &  001010 = 001010)` which is not 0

## USEFUL METHODS

### HOW MANY BITS ARE DIFFERENT BETWEEN TWO NUMBERS?

```
x = 0b001011
y = 0b111001
def how_many_different(x, y):
  dif = 1
  z = x ^ y
  for i in range(6):
    if (z>>i)&1=1
      dif+=1
  return dif

(how_many_different(x, y) == 3) is True
```
