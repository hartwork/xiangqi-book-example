# About

This repository intends to demo creation of a book
featuring razor-sharp Xiangqi board setups
based on
LaTeX,
[xiangqi-setup](https://github.com/hartwork/xiangqi-setup),
and (a subset of) [FEN notation](http://wxf.ca/xq/computer/fen.pdf).

For details please see:
- [`GNUmakefile`](GNUmakefile)
- [`book.tex`](book.tex)
- `setups/`
    - [`default.wxf`](setups/default.wxf)
    - [`demo.wxf`](setups/demo.wxf)


# Build-time Requirements

- GNU make
- Python >=3.6
- Inkscape
- LaTeX


# How to Build

```console
# make
[..]
# okular book.pdf &
```


# FEN Notation

Example FEN, the default starting position:

> `rheakaehr/9/1c5c1/p1p1p1p1p/9/9/P1P1P1P1P/1C5C1/9/RHEAKAEHR w`

With regard to FEN notation, the syntax rules are:

- *Lowercase* letters indicate pieces of
  the *black* (or *blue*) party (with their palace at the top of the board),
  *uppercase* letters indicate pieces of
  the *red* (or *white*) party (with their palace at the bottom of the board).

- The pieces are:
    - `a`/`A` — advisor
    - `c`/`C` — cannon
    - `e`/`E`/`b`/`B` — elephant
    - `h`/`H`/`n`/`N` — horse
    - `k`/`K` — king
    - `p`/`P` — pawn
    - `r`/`R` — rook

- Digits `1` (one) to `9` (nine) is the number of consecutive empty fields in a row.

- A `/` (slash or solidus) starts a new row.

- Suffix ` w` or ` b` indicates that
  *red* (or *white*) is to move or that *black* (or *blue*) is to move,
  respectively.

This is effectively the first two fields described at http://wxf.ca/xq/computer/fen.pdf
plus the alternative letters used at https://www.chessdb.cn/query_en/ .
