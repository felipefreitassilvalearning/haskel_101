# aula3p2-tipos-basicos

### Comandos utilizados

modo interativo
```
    ghci
```
`command`
- `result`

`True`
- `True`

`:t True`
- `True :: Bool`

`Olá, Mundo!`
- `Ol\225, Mundo!`

`x = 3`

`:t x`
- `x :: Num a => a`
  - `Num` é uma classe de tipos, que são tipos que podem ser interpretados como números

`:t sqrt x`
- `sqrt x :: Floating a => a`
  - `Floating` é uma classe de tipos, que são tipos que podem ser interpretados como números de ponto flutuante

`[1,2,3,4,5]`
- `[1,2,3,4,5]`

`:t [1,2,3,4,5]`
- `[1,2,3,4,5] :: Num a => [a]`

`['1', 'a', '5', 'o', 'À']`
- `"1a5o\192"`

`(1, 'a', True, 4.5)`
- `(1,'a',True,4.5)`

`:t (1, 'a', True, 4.5)`
- `(1, 'a', True, 4.5) :: (Fractional d, Num a) => (a, Char, Bool, d)`

`t = (1, 'a', True, 4.5)`

`[t]`
- `[(1,'a',True,4.5)]`

`:t [t]`
- `[t] :: (Fractional d, Num a) => [(a, Char, Bool, d)]`

`([t])`
- `[(1,'a',True,4.5)]`

`([t], 12345)`
- `([1,'a',True,4.5],12345)`

`:t (+)`
- `(+) :: Num a => a -> a -> a`