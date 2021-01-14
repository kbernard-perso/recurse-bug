# recurse-bug
Step to reproduce my issue

git init  
git checkout -b master  
git submodule add https://github.com/kbernard-perso/recurse-bug.git  
git submodule init  
git add .  
git commit -m "Add submodule"  
cd recurse-bug/  
echo "file1 modified" >> file1.txt  
git add .  
git commit -m "file1.txt modified"  
cd ..  
git add .  
git commit -m "Modified file1 in submodule"  
cd recurse-bug/  
echo "file2 modified" >> file2.txt  
cd ..  
git status  
git checkout --recurse-submodules HEAD^  
git status  

The uncommited modifications made with "echo "file2 modified" >> file2.txt" are  
discarded by git checkout --recurse-submodules HEAD^  
