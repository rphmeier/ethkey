# ethkey

[![Build Status][travis-image]][travis-url]

[travis-image]: https://travis-ci.org/ethcore/ethkey.svg?branch=master
[travis-url]: https://travis-ci.org/ethcore/ethkey

Ethereum keys generator.

[Documentation](http://ethcore.github.io/ethkey/ethkey/index.html)

### Usage

```
Ethereum keys generator.
  Copyright 2016 Ethcore (UK) Limited

Usage:
    ethkey generate random [options]
    ethkey generate prefix <prefix> <iterations> [options]
    ethkey generate brain <seed> [options]
    ethkey sign <secret> <message>
    ethkey verify <public> <signature> <message>
    ethkey [-h | --help]

Options:
    -h, --help         Display this message and exit.
    -s, --secret       Display only the secret.
    -p, --public       Display only the public.
    -a, --address      Display only the address.

Commands:
    generate           Generates new ethereum key.
    random             Random generation.
    prefix             Random generation, but address must start with a prefix
    brain              Generate new key from string seed.
    sign               Sign message using secret.
    verify             Verify signer of the signature.
```

### Examples

```
ethkey generate brain "this is sparta"
```

```
secret:  17d08f5fe8c77af811caa0c9a187e668ce3b74a99acc3f6d976f075fa8e0be55
public:  689268c0ff57a20cd299fa60d3fb374862aff565b20b5f1767906a99e6e09f3ff04ca2b2a5cd22f62941db103c0356df1a8ed20ce322cab2483db67685afd124
address: 26d1ec50b4e62c1d1a40d16e7cacc6a6580757d5
```

--

```
ethkey generate random
```

```
secret:  7d29fab185a33e2cd955812397354c472d2b84615b645aa135ff539f6b0d70d5
public:  35f222d88b80151857a2877826d940104887376a94c1cbd2c8c7c192eb701df88a18a4ecb8b05b1466c5b3706042027b5e079fe3a3683e66d822b0e047aa3418
address: a8fa5dd30a87bb9e3288d604eb74949c515ab66e
```

--

```
ethkey generate prefix ff 1000
```

```
secret:  2075b1d9c124ea673de7273758ed6de14802a9da8a73ceb74533d7c312ff6acd
public:  48dbce4508566a05509980a5dd1335599fcdac6f9858ba67018cecb9f09b8c4066dc4c18ae2722112fd4d9ac36d626793fffffb26071dfeb0c2300df994bd173
address: fff7e25dff2aa60f61f9d98130c8646a01f31649
```

--

```
ethkey sign 17d08f5fe8c77af811caa0c9a187e668ce3b74a99acc3f6d976f075fa8e0be55 bd50b7370c3f96733b31744c6c45079e7ae6c8d299613246d28ebcef507ec987
```

```
c1878cf60417151c766a712653d26ef350c8c75393458b7a9be715f053215af63dfd3b02c2ae65a8677917a8efa3172acb71cb90196e42106953ea0363c5aaf200
```

--

```
ethkey verify 689268c0ff57a20cd299fa60d3fb374862aff565b20b5f1767906a99e6e09f3ff04ca2b2a5cd22f62941db103c0356df1a8ed20ce322cab2483db67685afd124 c1878cf60417151c766a712653d26ef350c8c75393458b7a9be715f053215af63dfd3b02c2ae65a8677917a8efa3172acb71cb90196e42106953ea0363c5aaf200 bd50b7370c3f96733b31744c6c45079e7ae6c8d299613246d28ebcef507ec987
```

```
true
```

--

```
ethkey verify 689268c0ff57a20cd299fa60d3fb374862aff565b20b5f1767906a99e6e09f3ff04ca2b2a5cd22f62941db103c0356df1a8ed20ce322cab2483db67685afd124 c1878cf60417151c766a712653d26ef350c8c75393458b7a9be715f053215af63dfd3b02c2ae65a8677917a8efa3172acb71cb90196e42106953ea0363c5aaf200 bd50b7370c3f96733b31744c6c45079e7ae6c8d299613246d28ebcef507ec986
```

```
false
```
