# Monopoly_project
```{r}
# creating board
gameboard = data.frame(space = 1:40, title = c("Go", "Mediterranean Avenue", "Community Chest", "Oriental Avenue", "Income Tax", "Reading Railroad", "Oriental Avenue", "Chance", "Vermont Avenue", "Connecticut Avenue", "Jail", "St Charles Place", "Electric Company", "States Avenue", "Virginia Avenue", "Pennsylvania Avenue", "St James Place", "Community Chest", "Tennesse Avenue", "New York Avenue", "Free Parking", "Kentucky Avenue", "Chance", "Indiana Avenue", "Illinois Avenue", "B & O Railroad", "Atlantic Avenue", "Ventor Avenue", "Water Works", "Marvin Gardens", "Go To Jail", "Pacific Avenue", "North CArolina Avenue", "Community Chest", "Pennsylvania Avenue", "Short Line", "Chance", "Park Place", "Luxury Tax", "Boardwalk"), stringsAsFactors = FALSE)


# dice function
dice = function(verbose = FALSE){
  faces = sample(1:6,2, replace=TRUE)
  if(faces[1]==faces[2]) doules =TRUE
  else doubles = FALSE
  movement = sum(faces)
  if(verbose) cat("Rolled:", faces[1],faces[2],"\n")
  return(list(faces=faces, doubles=doubles, movement=movement))
}
```

https://www.youtube.com/watch?v=INVFh0P0IXU

Community chest/chance/title deed references
https://www.pinterest.com/pin/613263674237507441/
https://fliphtml5.com/bvlg/brca/basic
