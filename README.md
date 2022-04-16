# iBoard
iBoard is the future of board games, like chess, Checkers, go

This project provides an interface iBoard which is the base of iChess, iGo and other implementations
Those interface initiali abstracts the behavior of any board game with mxn squares, in a way that provides good performance and built in tools to perform calculations, validations and to create extensions

iBoard is writen in Rust, which can run in any platform, (windows, linux, ios, ruspbarry)

``` mermaid
flowchart BT
b[iBoard]
e[iBoardElement]
f[iBoardBackground]
p[iElement]
e-->b
f-->b
p-->e
```
