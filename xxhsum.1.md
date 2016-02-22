xxhsum(1) -- print or check xxHash non-cryptographic checksums
==============================================================

SYNOPSIS
--------

`xxhsum` [<OPTION>] ... [<FILE>] ...

DESCRIPTION
-----------

Print or check xxHash (32 or 64bit) checksums.  When <FILE> is `-`, read
standard input.

`xxhsum` supports a command line syntax similar but not indentical to
md5sum(1).  Differences are: `xxhsum` doesn't have text/binary mode switch
(`-b`, `-t`);  `xxhsum` always treats file as binary file;  `xxhsum` doesn't
have short option switch for warning (`-w`).  `xxhsum` has hash bit width
switch (`-H`);

Since xxHash is non-cryptographic checksum algorithm, `xxhsum` should not be
used any more for security related purposes.

OPTIONS
-------

* `-b`:
  Benchmark mode

* `-B`<BLOCKSIZE>:
  <BLOCKSIZE> specifies benchmark mode's test data block size in bytes.
  Default value is 102400

* `-c`, `--check`:
  Read xxHash sums from the <FILE>s and check them

* `-h`:
  Display help and exit

* `-H`<HASHTYPE>:
  Hash selection.  <HASHTYPE> means `0`=32bits, `1`=64bits.
  Default value is `1` (64bits)

* `--little-endian`:
  Set output hexadecimal checksum value as little endian convention.
  By default, value is displayed as big endian

* `-V`:
  Display xxhsum version

**The following four options are useful only when verifying checksums (`-c`)**

* `--quiet`:
  Exit non-zero for improperly formatted checksum lines

* `--strict`:
  Don't print OK for each successfully verified file

* `--status`:
  Don't output anything, status code shows success

* `--warn`:
  Warn about improperly formatted checksum lines

EXIT STATUS
-----------

`xxhsum` exit `0` on success, `1` if at least one file couldn't be read or
doesn't have the same checksum as the `-c` option.

EXAMPLES
--------

Output xxHash (64bit) checksum values of specific files to standard output

    $ xxhsum -H1 foo bar baz

Output xxHash (32bit and 64bit) checksum values of specific files to standard
output, and redirect it to `xyz.xxh32` and `qux.xxh64`

    $ xxhsum -H0 foo bar baz > xyz.xxh32
    $ xxhsum -H1 foo bar baz > qux.xxh64

Read xxHash sums from specific files and check them

    $ xxhsum -c xyz.xxh32 qux.xxh64

BUGS
----

Report bugs at: https://github.com/Cyan4973/xxHash/issues/

AUTHOR
------

Yann Collet