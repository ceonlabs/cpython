# Compiling Python3.11 with Cosmopolitan

This repo contains the source code of [Python 3.11.0rc1][py311] customized to
compile with [Cosmopolitan][cosmo] libc.  Meant for experimental purposes only.

** Note: ** this does not build a Python3.11 APE just yet -- I still need to
figure out how Python3.11 adds elements to `sys.path` (something involving
`Modules/getpath.py`).

# Steps to compile

1. clone the cosmopolitan repo somewhere nearby (for headers)

```bash
cd ../
git clone https://github.com/jart/cosmopolitan
```

2. download the cosmopolitan amalgamation (`cosmopolitan.a`, `ape.lds` and
   friends) somewhere

```bash
cd ../
mkdir amalg
cd amalg/
wget https://justine.lol/cosmopolitan/cosmopolitan.zip
unzip cosmopolitan.zip
```

3. set the `COSMO_REPODIR` variable in `superconfigure` to point to wherever you
   have the cosmopolitan repo (in this case `../cosmopolitan`)

4. set the `COSMO_LIBDIR` variable in `superconfigure` to point to wherever you
   have the cosmopolitan amalgamation (in this case `../amalg`)

5. run `superconfigure`

6. run `make -j4`

7. run `./python`



[py311]: https://github.com/python/cpython/tree/41cb07120b7792eac6413b0c56256a25e9b14e5d
[cosmo]: https://github.com/jart/cosmopolitan
