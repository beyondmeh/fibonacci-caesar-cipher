# Fibonacci Caesar Cipher

A [Caesar cipher](https://en.wikipedia.org/wiki/Caesar_cipher) that shifts letters based on the [Fibonacci sequence](https://en.wikipedia.org/wiki/Fibonacci_number). You should not use this to protect secrets. That said, it is slightly more interesting and obscure than the ubiquitous [ROT13](https://en.wikipedia.org/wiki/ROT13).

**Sample**

> We hold these truths to be self-evident, that all men are created equal, that they are endowed by their Creator with certain unalienable Rights, that among these are Life, Liberty and the pursuit of Happiness.

*Wf iqoi buzah eftgtr ey wj sjqp-tuwqfbi, wzvg igo kfm aqd aozsgjv bfgby, hipj ycet vhp fzqnipa jd gzjft Bsebuqu bqgc khchzvz tykgnesflad Fvhviv, lcnb vpmof tgdqb vjr Qact, Xjossio fid ocu avdftue ln Mnhufpdts.*


## Usage
Pass either *encrypt* or *decrypt* along with the message to `fibrot`. For instance:


### Encrypt

```console
$ fibrot encrypt "Hello World"
```

    Hfmnr Bwegl

### Decrypt

```console
$ fibrot decrypt "Gppfedm Pmchw Knexc"
```

    Goodbye Cruel World

## Encipherment Description

Characters are rotated based on their position and corresponding Fibonacci number. Non-alphabet letters are skipped. Fibonacci numbers past the 10th number are [modulo](https://en.wikipedia.org/wiki/Modulo_operation) by 26; the 10th number in the series is 34, so the result would be to rotate by 8 characters.

### Key Schedule
The below sample table is for 20 iterations / characters, the main `fibrot` script supports longer or shorter messages.


| Fibonacci | Rotation | A = ? |
| --------- | -------- | ----- |
| 0         | 0        | A     |
| 1         | 1        | B     |
| 1         | 1        | B     |
| 2         | 2        | C     |
| 3         | 3        | D     |
| 5         | 5        | F     |
| 8         | 8        | I     |
| 13        | 13       | N     |
| 21        | 21       | V     |
| 34        | 8        | I     |
| 55        | 3        | D     |
| 89        | 11       | L     |
| 144       | 14       | O     |
| 233       | 25       | Z     |
| 377       | 13       | N     |
| 610       | 12       | M     |
| 987       | 25       | Z     |
| 1597      | 11       | L     |
| 2584      | 10       | K     |
| 4181      | 21       | V     |

### `key_schedule` script

The `key_schedule` script will print the corresponding Fibonacci and Rotation key schedule for the given length of a message.

For example:

```console
$ key_schedule 5
```

    fibonacci    rotation
    0            0
    1            1
    1            1
    2            2
    3            3


## Encipherment Example

|                         |   |   |   |   |   |   |     |    |    |      |    |    |     |     |
| ----------------------- | - | - | - | - | - | - | --- | -- | -- | ---- | -- | -- | --- | --- |
| **Message:**            | A | T | T | A | C | K |     | A  | T  |      | D  | A  | W   | N   |
| **Fibonacci Sequence:** | 0 | 1 | 1 | 2 | 3 | 5 | 8   | 13 | 21 | 34   | 55 | 89 | 144 | 233 |
| **Rotation:**           | 0 | 1 | 1 | 2 | 3 | 5 |  -  | 13 | 21 | -    | 3  | 11 | 14  | 25  |
| **Result:**             | A | U | U | C | F | P |     | I  | G  |      | Y  | I  | Z   | Y   |


## Decryption Exercise for the Reader

> Wf'sg qt agmiqrsqf fn wyqj  
> Ytz ucnk gis gxdzf iig qp co H  
> Z drgd ptejxfnrbu'h mmvt D'h jsjzxhzr ln  
> Dbm blwken'u hgw ypvn nuza zak nerzw gzd  
>  
> S ytgg xocw lj gmgo wpt hnv G'j awrqakv  
> Spghb bqpz yjp kyeqerflkl  
>  
> Srnjo inonb hkyj gbp cs, ysurd fzxif ljy idt rbxb  
> Chnze ojqlb qum zplpfq ffa sqtrfu nez  
> Ieqzh rpzaz ylhm dbm hoa, mfvfs irsvn nib rcnqnxp  
> Xzaew lycmo gfza d ddr iig fvqt xns

Submit bug reports via GitHub's [Issue Tracker](https://github.com/beyondmeh/fibonacci-caesar-cipher/issues)


## Author
Copyright &copy; 2017-2023 BeyondMeh, except where otherwise noted.

Licensed under the [MIT license](https://github.com/keithieopia/fibonacci-caesar-cipher/blob/master/LICENSE).

*This is free software: you are free to change and redistribute it. There is NO WARRANTY, to the extent permitted by law.*
