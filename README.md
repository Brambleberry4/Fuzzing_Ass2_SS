# Assignment 2 - Fuzzing Project - Software security - Group 10

### Felix Mölder, Naveen Vinayakamoorthy, Chris Musteaţă, George-Nicolas Nădejde

## AFL++ installation via Docker

To run a single afl-fuzz thread within a docker container run:
```shell
docker run --name afl -ti -v ${PWD}:/src aflplusplus/aflplusplus
```


