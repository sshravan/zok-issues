

Number of constraints after compile

## Description
Prior to 0.7.9, ```zokrates compile ``` would return the constraints count after successful compilation. However this is no longer the case in newer versions.
How to enable this feature in the latest version?


## Environment

- Compiler version: 0.7.9 (048221ba)
- Operating system: Ubuntu

## Steps to Reproduce
example.zok
```zokrates
def main(private field a, field b):
  assert(a * a == b)
  return
```

```bash
zokrates compile -i example.zok
```

Expected output:
```bash
Compiling example.zok

Compiled code written to 'out'
Number of constraints: 1
```

actual output
```bash
Compiling example.zok

Compiled code written to 'out'
```
