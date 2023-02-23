# Compiling Python3.11.0rc1 + Django 4.1.7 with Cosmopolitan Libc

This repo contains the source code of [Python 3.11.0rc1][py311] customized to
compile with [Cosmopolitan][cosmo] libc. It also includes Django 4.1.7. **Meant
for experimental purposes only**.

# Steps to compile

1. clone the cosmopolitan repo somewhere nearby (for headers)

```bash
cd ../
git clone https://github.com/jart/cosmopolitan
```

2. build the necessary artifacts from the cosmopolitan libc repo

```bash
cd ../cosmopolitan
make -j4 o/cosmopolitan.h
make -j4 o//cosmopolitan.a
make -j4 o//third_party/sqlite3/libsqlite3.a
```

3. set the `COSMO_REPODIR` variable in `superconfigure` to point to wherever you
   have the cosmopolitan repo (in this case `../cosmopolitan`)

4. set the `COSMO_LIBDIR` variable in `superconfigure` to point to wherever you
   have the cosmopolitan build artifacts (in this case `../cosmopolitan/o`)

5. run `superconfigure`

6. run `make -j4`

7. run `./python.com -m django help`



[py311]: https://github.com/python/cpython/tree/41cb07120b7792eac6413b0c56256a25e9b14e5d
[cosmo]: https://github.com/jart/cosmopolitan
