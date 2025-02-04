# home work assignment 1 
First thing I did was look at the assignment prompt
I then used the pwd command to check where I was 
Then I used the LS function to see what files and folders were there 
I then used the cd commands to get into the haiku folder 
from there i used the code that was provided and edited the text to include the poem that I picked 
I then used the -o function to create the file and named it within the code 
From there I double checked the file to make sure it was read in the way assigned 
it worked! 
# code 
`maverick@Arnolds-MacBook-Pro ~ % 'pwd'
/Users/maverick
maverick@Arnolds-MacBook-Pro ~ % 'ls'
Applications	Downloads	Music		Splice
Desktop		Library		Pictures	tmp
Documents	Movies		Public
maverick@Arnolds-MacBook-Pro ~ % 'cd'
maverick@Arnolds-MacBook-Pro ~ % /Users/maverick/Documents/GitHub/itp/Haiku 
zsh: permission denied: /Users/maverick/Documents/GitHub/itp/Haiku
maverick@Arnolds-MacBook-Pro ~ % 'pwd'
/Users/maverick
maverick@Arnolds-MacBook-Pro ~ % 'cd'
maverick@Arnolds-MacBook-Pro ~ % 'cd'
maverick@Arnolds-MacBook-Pro ~ % 'cd' documents
maverick@Arnolds-MacBook-Pro documents % 'cd' github
maverick@Arnolds-MacBook-Pro github % 'cd'itp
zsh: command not found: cditp
maverick@Arnolds-MacBook-Pro github % 'cd' itp
maverick@Arnolds-MacBook-Pro itp % 'ls'
Haiku		README.md
maverick@Arnolds-MacBook-Pro itp % 'cd' haiku
maverick@Arnolds-MacBook-Pro haiku % say "dark deep dangerous and splendor all around it was in the roots and under" -o haikuassignment.aiff
maverick@Arnolds-MacBook-Pro haiku % 
`