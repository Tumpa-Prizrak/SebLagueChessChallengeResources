This document will contain everything related to managing your FENs in SebLague's app.
## Replacing contents of default Fens.txt file
Find the file shown on the image below<br/>
![](https://github.com/Odin7094/SebLagueChessChallengeResources/assets/130106357/ad169d25-835e-4bb5-8f16-9c2befbb83b5)<br/>
Open it, each FEN visible here is being played twice by the program. <br/>
500 lines of FENs, played first normally and then with the sides flipped, resulting in 1000 games by default.<br/>
Modify the contents in any way you want to modify it, for example replace everything with your desired FENs list, and save it. <br/>
It's unlikely that the change will take place if you press the ![](https://github.com/Odin7094/SebLagueChessChallengeResources/assets/130106357/f0d104d4-6468-4d3e-8be1-63b9cc5660ba) right away. <br/>
Press the Rebuild Solution button instead.<br/>
![](https://github.com/Odin7094/SebLagueChessChallengeResources/assets/130106357/e76d2f57-6576-49bb-8cf8-478c844c7c79)<br/>
Now you can press ![](https://github.com/Odin7094/SebLagueChessChallengeResources/assets/130106357/f0d104d4-6468-4d3e-8be1-63b9cc5660ba) and the change will likely take effect.

## Having several FEN presets
Navigate to resources as shown<br/>
![](https://github.com/Odin7094/SebLagueChessChallengeResources/assets/130106357/b071ffaf-63c5-4c28-8b66-cd04fafe2de4)<br/>
Put your file with your fens in it.<br/>
In the ChallengeController.cs file you'll find<br/>
![](https://github.com/Odin7094/SebLagueChessChallengeResources/assets/130106357/3bbcb593-50fa-4420-86b7-7b48041e2a3e)<br/>
Swap the filename. You're done.<br/>
However, there is one more problem you might have. I have created the fen files in it via Windows Explorer, and then files have appeared on their own within the project, which might have lead to that problem, but I do not have the knowledge of whether or not it happens if you make files be there via VS interface or in any other your way.<br/>
If on pressing ![](https://github.com/Odin7094/SebLagueChessChallengeResources/assets/130106357/f0d104d4-6468-4d3e-8be1-63b9cc5660ba) you're getting error saying that your file was not found after swapping filename in ChallengeController.cs, you will need to do as said below. It's also probable that default Fens.txt will work just fine if you switch it back, but don't let it fool you.<br/>
Double-click on a position shown below<br/>
![](https://github.com/Odin7094/SebLagueChessChallengeResources/assets/130106357/f9558972-28b5-404f-b4f5-eceac752b5f4)<br/>
Navigate the file until you find the <br/>
![](https://github.com/Odin7094/SebLagueChessChallengeResources/assets/130106357/dba4c16f-5e3c-43b5-8cc7-185adbd1f427)<br/>
and make sure that there is a similar structure for each of your new files. Most likely by creating one.<br/>
![obraz](https://github.com/Odin7094/SebLagueChessChallengeResources/assets/130106357/1327048e-2f9c-4b8a-ad72-b03a5d8d090f)<br/>


