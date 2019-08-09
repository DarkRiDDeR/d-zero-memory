[![Dub](https://img.shields.io/dub/v/zero-memory.svg?style=flat)](https://code.dlang.org/packages/zero-memory)
[![Build Status](https://travis-ci.org/DarkRiDDeR/d-zero-memory.svg?branch=master)](https://travis-ci.org/DarkRiDDeR/d-zero-memory)
[![License](https://img.shields.io/github/license/DarkRiDDeR/d-zero-memory.svg?style=flat)](https://github.com/DarkRiDDeR/d-zero-memory/blob/master/LICENSE)

# D Zero Memory

This is a function implementation SecureZeroMemory in D programming language.

Fills a block of memory with zeros. SecureZeroMemory is designed to be a more secure version of zero memory function.

Use this function instead of zero memory function when you want to ensure that your data will be overwritten promptly,
as some compilers can optimize a call to zero memory function by removing it entirely.

## Install

```sh
$ dub add zero_memory
```

## Usage example

```d
import zero_memory;

ubyte[] ar  = [0, 0, 0, 0, 0];
ubyte[] ar2 = [1, 2, 3, 4, 5];

secureZeroMemory(ar2.ptr, ar2.length);
assert(ar == ar2);


uint[] i  = [0, 0, 0,  0, 0 ];
uint[] i2 = [8, 5, 99, 5, 99];
// !!! function secureZeroMemory processes data by byte. Therefore, it is wrong:
secureZeroMemory(i2.ptr, i2.length);
assert(i != i2);
// Need to calculate the length:
secureZeroMemory(i2.ptr, uint.sizeof * i2.length);
assert(i == i2);
```


## License

MIT License
