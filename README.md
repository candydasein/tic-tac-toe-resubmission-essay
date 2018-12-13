# tic-tac-toe-resubmission-essay
For this Tic Tac Toe project, the very first thing I worked on was the game logic. I actually found it quite challenging to think of the game logic in purely abstract form — that is, without some concrete representation of a game board — so the very first thing I did was write the basic HTML for the game board. This, in turn, allowed me to map out all of my click handlers, which, in turn, allowed me to conceive of the logic of the game itself.

The game logic was in some ways the easiest thing to implement. There are probably more efficient ways to do it, but I felt most comfortable working with arrays, so I created a board array for each game in which each index corresponded to a square on my game board (beginning on the upper left — space 0 — then going horizontally to the right (spaces 1 and 2) and repeating this process with each row. In this way I started with an empty board array and could determine whether there was a win or tie based on which of the spaces were filled by which “player” (defined as an ‘X’ or an ‘O’). It turns out that there are only eight possible combinations of X’s or O’s on a tic tac toe board that will result in victory. I mapped each one of these in an elaborate set of “if” statements for both O and X -- e.g.:

```
if (boardArray[0] === 'O' && boardArray[1] === 'O' && boardArray [2] === ‘O' || boardArray[3] === 'O' && boardArray[4] === 'O' && boardArray [5] === ‘O’
```

and so forth). I also added “draw” functionality by creating a second array which simply measured the quantity of total clicks, regardless of their position/index. If the length of this second array were to reach 9 and neither side has achieved any of the winning combinations of board/array positions in the first array, then the game would result in a draw. 

Next, I worked to tackle some of the minute but challenging details of this particular game (e.g., that X and O need to alternate, that the user cannot change an X to an O or vice versa after it’s already been placed, and so on). Whenever I hit obstacles while trying to solve these problems, I would switch to building out my API requests using AJAX. These were simple to build, and once I was able to get the game working exactly as planned (and after working out several bugs that were discovered by my 6- and 8-year-old children), I worked on linking the game logic to the API. The main challenge here was being certain that the data object I was giving the API in my patch requests was in the exact format that it needed. The key here was making sure that all of my variable lined up with the API’s structure:

```
 const data = {
         game: {
            cell: {
        value: currentPlayer,
        index: event.target.id
        },
        over: overOrNot
         }
    }
```

I encountered bugs frequently, and the project was largely error-driven. One bug in particular was a very interesting learning experience. After I got my game working perfectly, including in its interactions with the API, I began to find that it would only work perfectly on the first iteration of the game. However, if the user asked to play again, strange things would happen. My change player function would break down, with O or X repeating. A draw would be called after only a few moves. X would be declared the winner when they had not yet won. My two arrays were set to reset as part of a game over function, but with the help of my instructional team and an astonishing amount of console.logging, I eventually discovered that the event handlers themselves were not resetting between games. Therefore, if you had not clicked on a particular space in the first game and then did so in the next game, things would go as planned. But if you had clicked a particular space in the previous game and also did so in the next game, the event handler would be doubled — which would push two moves instead of one into my arrays (thus destroying the game logic) and would also confuse the change player function. Once this was successfully debugged the project was complete in my mind.

However, I left some things in by mistake — console.logs (which I actually didn’t realize were not allowed because I failed to read the instructions all the way through, a fairly big mistake that I will certainly never repeat!), uncleared forms (which I also didn’t know were disallowed!) and a “play” button, which I should have made disappear as soon as it is pressed the first time since the logic that prevents the click handlers from doubling in the way I describe above is attached not to that button but only to the “play again” button. I also did not fix one outstanding problem where if you sign in after signing out, the board does not reappear. This is also an easy fix that I plan to address before my portfolio goes public.

Overall, I am proud of the work I did on this project and I found it to present some very exciting and fun challenges.




