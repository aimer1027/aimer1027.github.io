#Nim Game
[problems linker](https://leetcode.com/problems/nim-game/)<br/>
<b>descriptions:</b><br/>
You are playing the following Nim Game with your friend:<br/>
There is a heap of stones on the table, each time one of you take turns to remove 1 to 3 stones.<br/>
The one who removes the last stone will be the winner. You will take the first turn to remove the stones.<br/>

Both of you are very clever and have optimal strategies for the game. <br/>
Write a function to determine whether you can win the game given the number of stones in the heap.<br/>

For example, if there are 4 stones in the heap, then you will never win the game: <br/>
no matter 1, 2, or 3 stones you remove, the last stone will always be removed by your friend.<br/>

source code:


```c++
class Solution {
public:
    bool canWinNim(int n) {
        if(n%4==0)
            return false ;
        else 
            return true ;
    }
};
```