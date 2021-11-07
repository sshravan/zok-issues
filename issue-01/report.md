
Creating 2D array of size 1024 x 1024

## Description
I am unable to load moderately sized const 2D array. In the following code snippet, I am simply trying to load a matrix and multiply it with a scalar.
However, after running for 10+ hours, the compiler simply fails.
Here is the link to the [full code](https://github.com/sshravan/zok-issues/tree/main/issue-01/).

## Environment

- Compiler version: 0.7.7 (fc55d881)
- Operating system: Ubuntu

## Steps to Reproduce

bug/utils/matrix.zok

```zokrates
const u32 SIZE = 1024
const field[1024][1024] MATRIX = [
	[
	       1,       2,       3,       4, ...
	],
	...
	[
	       4,       3,       2,       1, ...
	]
]

```

bug/main.zok

```zokrates
from "./utils/matrix" import MATRIX
const u32 SIZE = 1024

def main(field scalar):
    field[SIZE][SIZE] result = [[0; SIZE]; SIZE]
    for u32 i in 0..SIZE do
        for u32 j in 0..SIZE do
            result[i][j] = MATRIX[i][j] * scalar
        endfor
    endfor

    assert(result == [[0; SIZE]; SIZE])
    return
```

```bash
$ zokrates compile -i bug/main.zok
Compiling bug/main.zok

[2]    366099 killed     zokrates compile -i bug/main.zok
zokrates compile -i bug/main.zok  37104.11s user 32.63s system 99% cpu 10:21:45.32 total
```

Any suggestions to speed up the compilation is highly appreciated!
