# Test

@alebaccioli

Testare di Git e GitHub.

## Test vari

Variabili:

- h1: titolo 1 della pagina
- repo: titolo del repo
- repodesc: descrizione del repo

Test:

- [1 livello, no README, no omit](md1/no-omit.md): h1 / repo
- [1 livello, no README, omit](md1/omit.md): repo / repodesc
- [1 livello, README, no omit](md2/no-omit.md): h1 / repo
- [1 livello, README, omit](md2/omit.md): repo / repodesc
- [2 livelli, no README, no omit](inner/md1/no-omit.md): h1 / repo
- [2 livelli, no README, omit](inner/md1/omit.md): repo / repodesc
- [2 livelli, README, no omit](inner/md2/no-omit.md): h1 / repo
- [2 livelli, README, omit](inner/md2/omit.md): repo / repodesc

README.md: h1 / repo

Se h1 == repo, allora repo / repodesc

[no-omit, toc.level 2..6](indice.md)