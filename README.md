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

## structure

``` delphi
IBoard<E> = Interface
  func canMove(O, D): boolean;
  func getE(e): E;
  prop Element[Index: integer]: E read getE;
end;

IBoardElement = interface
  Element: IElement;
  Background: IElementColor;
end;
```

Example, implementation of Knight using iBoard

``` Delphi
TKnight = class(IElement)
  func canMove(O, D; Board: IBoard): boolean;
  func getE(e): E;
 end;
 
 implementation
 
TKnight.canMove(O, D; Board: IBoard): boolean;
 begin
   Result := (Board.DeltaX(O,D) + Board.DeltaY(O,D) = 3) and (Board.DeltaX(O,D) * Board.DeltaY(O,D) = 2);
 end;
```

as TBoard also implements canMove, then the game can check general situations first;

``` delphi
implementation

TBorad.canMove(O, D): boolean;
 begin
   Result := (Element(O).Background = CurrentPlayer.Background and Element(D).Background = None);
 end;
```

And Before Move just calling the engine verification

``` delphi
if not GameOver(CurrentUser) then
if UserInCheck(CurrentUser) then chooseStrategy(SafeYourself)
else chooseStrategy(NormalGame);
```

Implementing mos advanced rules

``` delphi
implementation

TBorad.canMove(O, D): boolean;
 begin
   if isCastle(O, D) then Result := chooseStrategy(Castle)
   else if isPawnPassant(O, D) then Result := chooseStrategy(Castle)
   else if isPromotion(O, D) then Result := chooseStrategy(Promotion)
   else  Result := (Element(O).Background = CurrentPlayer.Background and Element(D).Background = None);
 end;
```
