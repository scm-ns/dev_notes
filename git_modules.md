
A technique to add a different project managed as a different repo into another repo. 
The basic idea is that the current repo will maintain a pointer to the lib repo ( repo that you want to add )
(via the commit hash)  so you don't have to place the lib repo into the curr repo's version control. 

If you make changes to the lib repo, then you need to update the pointer that the current repo holds with the next commit hash, 
so that git can download the lib repo with the right version you need for the current repo. 
It is a cute system and there are alternatives like git sub-trees, but I haven't used them. 




