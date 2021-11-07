
Creating 2D array of size 1024 x 1024

## Description
Is there a way to speed up the compilation of code with large arrays?
For my use case, I am trying to load a matrix (of size 1024 x 1024) and compute its product with a vector (of size 1024).

This code snipper has not yet finished despite running the for 9+ hours.
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
```

Any suggestions to speed up the compilation is highly appreciated!
