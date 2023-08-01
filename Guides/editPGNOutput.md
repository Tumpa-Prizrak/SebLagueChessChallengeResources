This file will contain various methods of modifying pgn output.<br/>
Code here generally needs to be put somewhere into Chess-Challenge\src\Framework\Chess\Helpers\PGNCreator.cs.

## How to mark games exported in pgn for easy search
Adds ["MyBot" is mated] to the beginning of the PGN output. 
Name is swapped to the name of whichever bot is mated in current match, like ["EvilBot" is mated].
```csharp
if (result is not GameResult.NotStarted or GameResult.InProgress)
{
    if(result == GameResult.WhiteIsMated) pgn.AppendLine($"[\"{whiteName}\" is mated]");
    if(result == GameResult.BlackIsMated) pgn.AppendLine($"[\"{blackName}\" is mated]");
}
```
Put that in Chess-Challenge\src\Framework\Chess\Helpers\PGNCreator.cs as shown below.
![](https://media.discordapp.net/attachments/1134968626122854450/1134968626378719242/image.png)<br/>
Example result: <br/>
```
["MyBot" is mated]
[White "EvilBot"]
[Black "MyBot"]
[Result "BlackIsMated"]
1. Nh3 a6 2. a3 a5 3. g4 a4 4. f4 c6 5. b3 c5 6. bxa4 Rxa4 7. g5 Re4 8. Nf2 Rxf4 9. Ng4 Rxg4 10. a4 Rxg5 11. d4 Qa5+ 12. Qd2 Qa6 13. Qxg5 Qa5+ 14. Bd2 Qa6 15. Qxc5 Qf6 16. Qxc8# 
```
## Count to exported PGNs
The PGNs are outputted to a file using Chess-Challenge\src\Framework\Chess\Helpers\PGNCreator.cs<br/>
Within that add these lines of code:
```cs
// above CreatePGN()
private static int numGames = 0;

// before the "// Headers" comment
pgn.AppendLine($"[Game #" + numGames + "]");
numGames++;
```
When you are done, it should look like
![](https://media.discordapp.net/attachments/1135381007449718906/1135381007667830824/image.png)
and when you open up the .txt file it should have a new tag that looks like
![](https://media.discordapp.net/attachments/1135381007449718906/1135381008204705892/image.png)
