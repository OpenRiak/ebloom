# ebloom

## Overview

![ebloom OpenRiak Status](https://github.com/OpenRiak/ebloom/actions/workflows/erlang.yml/badge.svg?branch=openriak-3.2)

`ebloom` is a NIF wrapper around a basic bloom filter.

## Quick Start

You must have [Erlang/OTP 22](http://erlang.org/download.html) or later and a GNU-style build system to compile and run =ebloom=.

```
git clone git://github.com/basho/ebloom.git
cd ebloom
make
```

Start up an Erlang shell with the path to =ebloom= included.

```
erl -pa path/to/ebloom/ebin
```

Create a new bloom filter, insert elements, and test for an elements presence.

```
1> PredictedElementCount=5.
5
2> FalsePositiveProbability=0.01.

3> RandomSeed=123.
123
4> {ok, Ref} = ebloom:new(PredictedElementCount, FalsePositiveProbability, RandomSeed).
{ok,<<>>}
5> ebloom:insert(Ref, <<"abcdef">>).
ok
6> true = ebloom:contains(Ref, <<"abcdef">>).
true
7> false = ebloom:contains(Ref, <<"zzzzzz">>).
false
```

## Contributing

The `ebloom` module is maintained to support a single function within the Riak legacy replication feature.  It is not actively developed (i.e. to consider new features or performance improvements).

