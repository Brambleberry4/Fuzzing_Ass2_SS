# Assignment 2 - Fuzzing Project - Software security - Group 10

### Felix Mölder, Naveen Vinayakamoorthy, Chris Musteaţă, George-Nicolas Nădejde

## Prerequisites and building tipps:

 1. Install and start docker before going on
 2. If you want to build svg2ass locally it is advised to change "strip -s" to "strip -S" in the Makefile when building on macOS. For more information see README\_SVG2ASS.md

## AFL++ installation via Docker

To pull the docker image (remember you only need that once) run:
```shell
docker pull aflplusplus/aflplusplus
```

To run a single afl-fuzz thread within a docker container, cd into the repository and run:
```shell
docker run --name afl -ti -v ${PWD}:/src aflplusplus/aflplusplus
cd /src
make CC=../AFLplusplus/afl-clang-fast CXX=../AFLplusplus/afl-clang-fast++ LD=../AFLplusplus/afl-clang-fast
afl-fuzz -i ./testcases -o ./afl_output -M main -- ./svg2ass @@ ./output
```

To run a single afl-fuzz thread with address or memory sanitizer, cd into the repository and run:
```shell
AFL_USE_ASAN=1 make CC=../AFLplusplus/afl-clang-fast CXX=../AFLplusplus/afl-clang-fast++ LD=../AFLplusplus/afl-clang-fast
afl-fuzz -i ./testcases -o ./afl_output_ASan -S ASan -- ./svg2ass @@ ./output
```
Or:
```shell
AFL_USE_MSAN=1 make CC=../AFLplusplus/afl-clang-fast CXX=../AFLplusplus/afl-clang-fast++ LD=../AFLplusplus/afl-clang-fast
afl-fuzz -i ./testcases -o ./afl_output_ASan -S MSan -- ./svg2ass @@ ./output
```


