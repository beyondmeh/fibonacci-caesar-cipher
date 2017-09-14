# Fibonacci Caesar Cipher

A [Caesar cipher](https://en.wikipedia.org/wiki/Caesar_cipher) that shifts letters based on the [Fibonacci sequence](https://en.wikipedia.org/wiki/Fibonacci_number).

You should not use this to protect secrets. That said, it is slightly more interesting and obscure than the ubiquitous [ROT13](https://en.wikipedia.org/wiki/ROT13).

## Usage
Pass either *encrypt* or *decrypt* along with the message to `fibrot`. For instance:


```console
$ fibrot encrypt "Hello World"
```

    Hfmnr Bwegl

```console
$ fibrot decrypt "Gppfedm Pmchw Knexc"
```

    Goodbye Cruel World

## Encipherment Description

Characters are rotated based on their position and corresponding Fibonacci number. Non-alphabet letters are skipped. Fibonacci numbers past the 10th number are [modulo](https://en.wikipedia.org/wiki/Modulo_operation) by 26; the 10th number in the series is 34, so the result would be to rotate by 8 characters.

## Key Schedule
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


## Detailed Encipherment Example

> ATTACK AT DAWN

| ----------------------- | - | - | - | - | - | - | --- | -- | -- | ---- | -- | -- | --- | --- |
| **Message:**            | A | T | T | A | C | K |     | A  | T  |      | D  | A  | W   | N   |
| **Fibonacci Sequence:** | 0 | 1 | 1 | 2 | 3 | 5 | 8   | 13 | 21 | 34   | 55 | 89 | 144 | 233 |
| **Rotation:**           | 0 | 1 | 1 | 2 | 3 | 5 | *-* | 13 | 21 | *-*  | 3  | 11 | 14  | 25  |
| **Result:**             | A | U | U | C | F | P |     | I  | G  |      | Y  | I  | Z   | Y   |


### Other Examples

*Hello World*

> Hfmnr Bwegl

---

*We hold these truths to be self-evident, that all men are created equal, that they are endowed by their Creator with certain unalienable Rights, that among these are Life, Liberty and the pursuit of Happiness.*

> Wf iqoi buzah eftgtr ey wj sjqp-tuwqfbi, wzvg igo kfm aqd aozsgjv bfgby, hipj ycet vhp fzqnipa jd gzjft Bsebuqu bqgc khchzvz tykgnesflad Fvhviv, lcnb vpmof tgdqb vjr Qact, Xjossio fid ocu avdftue ln Mnhufpdts.


## Feedback
I would love your feedback! If you use `piu` in your status bar send me [an email](mailto:timothykeith@gmail.com) with a screenshot. For the privacy conscious, feel free to encrypt any messages using my [PGP key](http://pgp.mit.edu/pks/lookup?op=vindex&fingerprint=on&search=0xF4F4A135C022EE12):

> 4135 C593 1D89 368E 7F32 C8ED F4F4 A135 C022 EE12

To import it into your keyring:
```console
$  gpg --keyserver pgp.mit.edu --recv-key 4135C5931D89368E7F32C8EDF4F4A135C022EE12
```

Submit bug reports via GitHub's [Issue Tracker](https://github.com/keithieopia/fibonacci-caesar-cipher/issues)


## Author
Copyright &copy; 2017 Timothy Keith, except where otherwise noted.

Licensed under the [MIT license](https://github.com/keithieopia/fibonacci-caesar-cipher/blob/master/LICENSE).

*This is free software: you are free to change and redistribute it. There is NO WARRANTY, to the extent permitted by law.*
