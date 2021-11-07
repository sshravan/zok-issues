
Optimizing range checks

## Description
I noticed that the Zokrates uses the range check algorithm from the Sapling ([Pg 140 Section A.3.2.2](https://github.com/zcash/zips/blob/master/protocol/sapling.pdf))

If I am not wrong, checking ```x < const```, would take at most ```2*log2(const)``` constraints using the approach described in the sapling spec.
However, it takes ~525 constraints to range check in the following code snippet. After looking at the ztf file, it looks like ```x``` is split into 254 bits instead of ```ceil(log2(const))``` bits.

Would it be possible improve the range checks?

## Environment

- Compiler version: 0.7.7 (fc55d881)
- Operating system: Ubuntu

## Steps to Reproduce

bug/main.zok

```zokrates
const field LIMIT = 16383
def main(field x):
    assert(x < LIMIT)
    return
```

```bash
$ zokrates compile -i bug/main.zok --ztf
```
