
A technique to add a different project managed as a different repo into another repo. 
The basic idea is that the current repo will maintain a pointer to the lib repo ( repo that you want to add )
(via the commit hash)  so you don't have to place the lib repo into the curr repo's version control. 

If you make changes to the lib repo, then you need to update the pointer that the current repo holds with the next commit hash, 
so that git can download the lib repo with the right version you need for the current repo. 
It is a cute system and there are alternatives like git sub-trees, but I haven't used them. 



use this website for more information : https://chrisjean.com/git-submodules-adding-using-removing-and-updating/


git submodules add git_repo lib/repo_name

now a .gitmodules file will be created pointing to the repo that your added. 
Along with it, as folder will be created lib/repo_name but it might be empty. ( based on the git versions, it could have the entire porject "

If empty use : 
	git submodules init
	git submodules update

Updating submodules : 
	Navigate to the sub module that you added and make the necessary changes. 
	Now navigate back to the curr repo, there when you run git status
	lib/repo_name will show up with (new commits)
	now you add lib/repo_name and create a commit, the pointer when keeps track of the repo version will be updated and now your curr repo 
	will use the latest version of the lib repo . 



