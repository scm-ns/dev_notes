
A technique to add a different project managed as a different repo into another repo. 
The basic idea is that the current repo will maintain a pointer to the lib repo ( repo that you want to add )
(via the commit hash)  so you don't have to place the lib repo into the curr repo's version control. 

If you make changes to the lib repo, then you need to update the pointer that the current repo holds with the next commit hash, 
so that git can download the lib repo with the right version you need for the current repo. 
It is a cute system and there are alternatives like git sub-trees, but I haven't used them. 

use this website for more information : https://chrisjean.com/git-submodules-adding-using-removing-and-updating/

git submodule add git_repo lib/repo_name

now a .gitmodules file will be created pointing to the repo that your added. 
Along with it, as folder will be created lib/repo_name but it might be empty. ( based on the git versions, it could have the entire porject "

If empty use : 
	git submodule init
	git submodule update

When you clone a project, the submodules are not automatically added to the project. To add them either follow the steps above or do this : 
    git submodule update --init --recursive

Updating submodules : 
	Navigate to the sub module that you added and make the necessary changes. 
    
    Say you want the latest version of the sub module or a specific version of the lib, 
    use git pull origin master or something similar to get the new version

	Now navigate back to the curr repo, there when you run git status
	lib/repo_name will show up with (new commits)
	now you add lib/repo_name and create a commit, 
    The pointer then keeps track of the verion ( of the submodule lib) will be updated and now your curr repo 
	will use the new version of the submodule repo. 

Internal storage.
    The commit that the library points to is stored in .git     
    So checkout the branch / commit you need, move back to the master repo and then update 
    the changes that will show up in the lib.
    
How to fix a particular version / tag /commit
    Go to the submodule and do 
        git checkout <COMMIT_SHA1>

    Go back to the master project
        git add lib/submodule

    Then commit the changes in the master project
    Now the current commit in the master project will tag the submodule to a particular commit. 
            
        The subproject commit seems to be stored in lib/dlib file. 
        This is odd as it shows up as directory when in the terminal, but for git that seems to be a file ??? 

rm a submodule adding by init
    git rm submodule_path

