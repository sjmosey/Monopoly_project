```{r}
# dice function
# Creating function to roll 2 dice
d2Roll = function(i){
  matrix(sample(1:6, 2, replace=T),
         ncol = 2)
}

# creating function to roll dice again if double is rolled
DoubleRoll = function(roll) {
  length(unique(roll)) == 1
}

# combining above to create a players turn
turn = function(jail = F){
  roll = d2Roll()
  
  if(jail) {
    roll
  } else {
    nRolls = 1
    
    while(nRolls < 3  && DoubleRoll(roll[nrow(roll), ])) {
      roll = rbind(roll, d2Roll())
      
      nRolls = nRolls + 1
    }
    roll
  }
}


spaces = function(turn){
  if(nrow(turn) == 3 && DoubleRoll(turn[nrow(turn), ])) {
    rowSums(head(turn) == "Jail")} else {rowSums(turn)}
  }

```






```{r}
# creating the board
tiles <- c("GO", "Mediterranean Avenue", "Community Chest", "Baltic Avenue", "Income Tax", "Reading Railroad", "Oriental Avenue","Chance","Vermont Avenue", "Connecticut Avenue", "Jail", "St. Charles Place", "Electric Company", "States Avenue", "Virginia Avenue","Pennsylvania Railroad", "St. James Place", "Community Chest","Tennessee Avenue","New York Avenue","Free Parking","Kentucky Avenue","Chance","Indiana Avenue","Illinois Avenue","B. & O. Railroad","Atlantic Avenue","Ventnor Avenue", "Water Works", "Marvin Gardens","Go To Jail","Pacific Avenue","North Carolina Avenue", "Community Chest", "Pennsylvania Avenue","Short Line", "Chance","Park Place", "Luxury Tax", "Boardwalk")

board <- data.frame(numeric_tile = 1:40, tiles)

```

```{r}
#need to run this once to prep the start of each player. (you can change the name to whatever data frame you want to save them in)
P1 = as.vector(1)
P2 = as.vector(1)
P3 = as.vector(1)
P4 = as.vector(1)
```


```{r}
# creating vectors for each player where each roll adds the sum of the dice and then adds it to the vector.  This can be run and will continue around the game board.  Just need to figure out the location we want to save it in.
P1 = append(P1,(1+sum(d2Roll())))
TurnLocP1 = tiles[sum(P1)%%length(tiles)]

P2 = append(P2,(1+sum(d2Roll())))
TurnLocP2 = tiles[sum(P2)%%length(tiles)]

P3 = append(P3,(1+sum(d2Roll())))
TurnLocP3 = tiles[sum(P3)%%length(tiles)]

P4 = append(P4,(1+sum(d2Roll())))
TurnLocP4 = tiles[sum(P4)%%length(tiles)]
```

