## Welcome to Mj's GitHub Pages
Owned by Mathew Jerard Paglinawan (Mj)

![alt text](https://media.giphy.com/media/YwRhMm0TONQdYGeMTS/giphy.gif) 

### Chill space
---------------------------------------

Welcome to my chill space, here you can see my favorite songs.

| Song | Artist |
| ----------- | ----------- |
|1. [Space song](https://open.spotify.com/track/7H0ya83CMmgFcOhw0UB6ow?si=400831fcf2c24d6e) | Beach house|
|2. [Passionfruit](https://open.spotify.com/track/5mCPDVBb16L4XQwDdbRUpz?si=3068eef69ed349d2) | Drake |
|3. [Here we go... again](https://open.spotify.com/track/1NhjYYcYTRywc0di98xHxf?si=82580b8923d74ecd) | The weekend, Tyler the creator |
|4. [Untitled](https://open.spotify.com/track/3PbV3ocgAp3Xn0omGFC0cG?si=5aedea95d2e345b3) | Rex Orange County |
|5. [Moments](https://open.spotify.com/track/1g6aK9HzKkbbQ2RpqtUyvL?si=cbebd6b07a05492d) | Micah Edwards |
|6. [Emiliana](https://open.spotify.com/track/0vNY7uNEG8El6doRdP21D5?si=947c6ca6ef91458b) | Ckay |
|7. [More than a woman](https://open.spotify.com/track/2cX2coZS1PYBfPs8wgbdWE?si=95d2c722c44d400b) | Bee Gees|
|8. [Fine line](https://open.spotify.com/track/6VzcQuzTNTMFnJ6rBSaLH9?si=784bdaf3b1594f36) | Harry Styles|
|9. [Am I Dreaming](https://open.spotify.com/track/6isTQfKXhNO3EyJd9mSxx8?si=3eea2a6860894210) | Lil Nas X, Miley Cyrus|
|10. [Spotless mind](https://open.spotify.com/track/40oLHUxXfd6mWRZcXzfV1U?si=b190a3d48dd0408a) | Emily Lind|
|11. [Moonlight](https://open.spotify.com/track/5A7CwBNDUhvLWuSU5oJEh3?si=52874810452f4b81) | Ariana Grande|
|12. [Show me how](https://open.spotify.com/track/6A46jG17UumVQLqodsFxuV?si=98db8ee7649d4972) | Men I trust|
|13. [All too well](https://open.spotify.com/track/5enxwA8aAbwZbf5qCHORXi?si=91014ff4c7364df5) | Taylor Swift|
|14. [Something About you](https://open.spotify.com/track/6RiiSy9GzSwiyDEJDiMuKe?si=0214ccaeeeda4858) | Eyedress, Dent May|
|15. [The less I know the better](https://open.spotify.com/track/6K4t31amVTZDgR3sKmwUJJ?si=41f673f398b74d39) |Tame Impala|

---------------------------------------

### My Favorite Albums

[![image-text](https://upload.wikimedia.org/wikipedia/en/b/b1/Harry_Styles_-_Fine_Line.png)](https://open.spotify.com/album/7xV2TzoaVc0ycW7fwBwAml?si=cW9l4AEeQZaQnT_0S0bGgA)   [![image-text](https://upload.wikimedia.org/wikipedia/en/b/bf/Lil_Nas_X_-_Montero.png)](https://open.spotify.com/album/6pOiDiuDQqrmo5DbG0ZubR?si=gxa2VVQ5RfSAM2jex3gkqw) 

---------------------------------------

### More songs that I love can be found on

[My Spotify](https://open.spotify.com/user/s10lzz7ryaefmrh2oqy7brn3g?si=2b30245b40b64c4f)

![alt text](https://media.giphy.com/media/TjLUXM7BA6JtZqB9A4/giphy.gif) 

import random

class Minesweeper:
    def __init__(self, rows, columns, mines):
        self.board = [['.' for j in range(columns)] for i in range(rows)]
        self.mines = set()
        while len(self.mines) < mines:
            i = random.randint(0, rows - 1)
            j = random.randint(0, columns - 1)
            if (i, j) not in self.mines:
                self.mines.add((i, j))
        self.rows = rows
        self.columns = columns
        self.mines = mines
        self.game_over = False
        self.flag_mode = False
    
    def display(self):
        for i in range(self.rows):
            for j in range(self.columns):
                print(self.board[i][j], end=' ')
            print()
        print()
    
    def count_mines(self, row, col):
        count = 0
        for i in range(row-1, row+2):
            for j in range(col-1, col+2):
                if 0 <= i < self.rows and 0 <= j < self.columns:
                    if (i, j) in self.mines:
                        count += 1
        return count
    
    def play(self, row, col):
        if (row, col) in self.mines:
            self.game_over = True
            print("Boom! You lost.")
        else:
            count = self.count_mines(row, col)
            self.board[row][col] = str(count) if count else ' '

def main():
    rows = int(input("Enter number of rows: "))
    columns = int(input("Enter number of columns: "))
    mines = int(input("Enter number of mines: "))
    game = Minesweeper(rows, columns, mines)
    while not game.game_over:
        game.display()
        row = int(input("Enter row: "))
        col = int(input("Enter column: "))
        game.play(row, col)

if __name__ == "__main__":
    main()

