This document will contain various Token Optimization techniques.

## Lambdas
Use lambdas everywhere. <br/>
Instead of
```csharp
public distance(int x, int y, int x2, int y2)
{
  return (int)Math.Sqrt(Math.Pow(Math.Abs(x - y)
            + Math.Abs(x2 - y2),2));
}
```
write
```cs
int dist(int x, int y, int x2, int y2) => (int)Math.Sqrt(Math.Pow(Math.Abs(x - y)
            + Math.Abs(x2 - y2),2));
```
##
Instead of storing evaluation or other values in a separate array, if it's used only once, you can return it like
```cs
Array.Sort( //use MinBy/MaxBy instead
legalMoves.Select(x =>
        new Random().Next(3)
        - Math.Abs(x.StartSquare.Index - board.GetKingSquare(board.IsWhiteToMove).Index)*2
        + 5000 * Convert.ToInt32(x.CapturePieceType)
        )
    .ToArray(),
legalMoves);
```
or like
```cs
board.GetLegalMoves().MinBy(move =>
    board.SquareIsAttackedByOpponent(move.TargetSquare) ? 999999999 : move.MovePieceType - move.CapturePieceType
);
```
or like
```cs
board.GetLegalMoves().MaxBy(x =>
{
    board.MakeMove(x);
    bool cm = board.IsInCheckmate();
    board.UndoMove(x);
    return
        cm | x.IsPromotion ? 999999 :
        board.SquareIsAttackedByOpponent(x.TargetSquare) ? -999999 :
        new Random().Next(23) +
        50 * (int)x.CapturePieceType
        - Math.Abs(x.StartSquare.Index - 32)
        ;
}
```
##
Count() also lets you filter stuff this way. <br/>
Instead of doing this
```cs
.Where(y => y.StartSquare == x.TargetSquare).Count();
```
do this
```cs
.Count(y => y.StartSquare == x.TargetSquare);
```
## Ternary operator
With it you can push conditional statements everywhere, including your returned expression.<br/>
For example
```cs
int abs(int x) => x < 0 ? -x : x; //use System.Math.Abs() instead, writing it yourself won't save tokens
```
or
```cs
return
    cm ? 999999 :
    dr ? -99999 :
    + (board.SquareIsAttackedByOpponent(x.TargetSquare) ? -1000 : 0)
    + (int)x.PromotionPieceType * 99999 
    + new Random().Next(15) 
    + 1 * caps[(int)x.CapturePieceType]
    - 1 * uses[(int)x.MovePieceType]
    //..., it's enough to show but if you want it's entire code then it is always somewhere on mentioned discord server
    //however it is from a pretty weak bot
```
## Current smallest possible bot that's still beating EvilBot.cs
Through common effort this was achieved
```cs
//48 tokens, 133W-28L-839D
using System.Linq;
using ChessChallenge.API;

public class MyBot : IChessBot
{
    public Move Think(Board board, Timer timer) =>
    board.GetLegalMoves().MinBy(move =>
        board.SquareIsAttackedByOpponent(move.TargetSquare) ? 999999999 : move.MovePieceType - move.CapturePieceType
    );
}
```
