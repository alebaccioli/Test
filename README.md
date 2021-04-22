# Test

Test vari su repository, GitHub e altro. @alebaccioli

- [1. GitHub Pages title](#1-github-pages-title)
  - [1.1. Legenda](#11-legenda)
  - [1.2. Test](#12-test)
  - [1.3. toc.level](#13-toclevel)
- [2. GitHub Pages header](#2-github-pages-header)
  - [2.1. Test _config.yml](#21-test-_configyml)

## 1. GitHub Pages title

Con l'estensione *Markdown All in One* di *Visual Studio Code* aggiungo un *TOC* auto-generato, ma voglio evitare di mettere `#` nell'indice. Si può mettere `<!-- omit in toc -->` sopra o accanto `#` per ignorarlo, ma questo crea problemi quando viene automaticamente scelto il `title` della risultante pagina *HTML*.

Di seguito vari test per verificare il comportamento di `<!-- omit in toc -->` in varie situazioni.

### 1.1. Legenda

- h1: `#` della pagina
- repo: titolo del repo
- repodesc: descrizione del repo

### 1.2. Test

- [1 livello, no README, no omit](md1/no-omit.md): h1 / repo
- [1 livello, no README, omit](md1/omit.md): repo / repodesc
- [1 livello, README, no omit](md2/no-omit.md): h1 / repo
- [1 livello, README, omit](md2/omit.md): repo / repodesc
- [2 livelli, no README, no omit](inner/md1/no-omit.md): h1 / repo
- [2 livelli, no README, omit](inner/md1/omit.md): repo / repodesc
- [2 livelli, README, no omit](inner/md2/no-omit.md): h1 / repo
- [2 livelli, README, omit](inner/md2/omit.md): repo / repodesc

README.md: h1 / repo, ma se h1 == repo, allora repo / repodesc

### 1.3. toc.level

Imposto *Markdown All in One* in modo da ignorare `#` tramite l'opzione `toc.level` mettendo come valore `2..6`. Non mi serve più `<!-- omit in toc -->`.

[no-omit, toc.level 2..6](indice.md): h1 / repo

**OK**: comportamento voluto raggiunto, `title` comprende il valore di `#` ma non è presente nell'indice *TOC* auto-generato.

## 2. GitHub Pages header

Nel tema di default, *Primer*, non compare un `header` ma un `h1` che corrisponde a repo, in aggiunta all'`h1` di `#` (eccetto quando `h1` e `#` hanno lo stesso valore, in tal caso ne compare solo uno).

Negli altri temi invece (non so se in tutti) compare un `header` che comprende, tra l'altro, repo e repodesc. 

Per togliere solo `h1` aggiuntivo, in `_config.yml` aggiungere:

```
name: something
title: null
```

Non basta solo `title`, deve essere presente anche `name`. `name` verrà usato nelle pagine in `title` al posto di repo.

Per togliere invece tutto l'`header` per i temi che lo supportano, in `/assets/css/style.scss` inserire:

```css
---
---

@import "(( site.theme ))";

header {
  display: none;
}
```

Convertire le parentesi *( )* in *{ }*. Ho cambiato parentesi qua perché altrimenti la variabile viene automaticamente convertita da *GitHub Pages*, es. `@import "{{ site.theme }}";`.

### 2.1. Test _config.yml

```
name: Titolo Alternativo
title: null
```

README.md: h1 / Titolo Alternativo, niente `h1` aggiuntivo

indice.md: h1 / Titolo Alternativo, niente `h1` aggiuntivo

**OK**: ora posso mettere nome repository minuscolo, es. *appunti*, ma titoli pagina maiuscoli, es. *Appunti*, grazie a `_config.yml`. E niente `h1` aggiuntivo.