# Vim Practice
> Task: changing the name of the `start` parameter and its uses to `base`.

Shortest path: 
`/start<enter>5sbase<esc>n.n.n.:wq`.

---

I first vimmed into the java file by `vim DocSearchServer.java`.
Then, I did `/start`to look for each `start` in this file because `/` stands for search, and should followed by the keyword we need to search.

![image](Week7Screenshots\searchStart.png)

Then, I hit enter to confirm the word to search, and the cursor jumps to the first character of the last `start` it finds.

![image](Week7Screenshots\enter.png)

I then did `5s`, this means delete 5 characters after the cursor and turn into insert mode.

![image](Week7Screenshots\5s.png)

I then typed in `base` to change start from base.

![image](Week7Screenshots\base.png)

I hit <esc> to exit insert mode. The INSERT in the bottom left corner disappears.

![image](Week7Screenshots\esc.png)

After exiting insert mode and entering normal mode, I did `n` to go to the next search result. It goes to the next `start` entry it finds.

![image](Week7Screenshots\n.png)

I then did `.`, this executes the former series of commands, which is `5sbase`.

![image](Week7Screenshots\formerCommand.png)

I did `n.` for three times until every `start` has been changed into `base`. I know this because when I hit the forth `n`, I got this message in the bottom left corner.

![image](Week7Screenshots\lastN.png)

Lastly, I used `:wq` to save and exit the vim.

![image](Week7Screenshots\exitVim.png)