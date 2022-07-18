# git submodule


git submodule add url
    add the latest commited submodule with files and directory inside the submodule from remote


git submodule update --remote
    checkout the lastest git commit(submodules) from remote server at once
git submodule update 
    checkout the commit already specified in the index of the superproject. 




git submodule summary
(base) ➜  submodule_ex git:(master) ✗ git submodule summary
* sub-1 4ad935c...97c0476 (1):
current commit:4ad935c
current checkout:97c0476

* sub-2 dd31051...b04045e (2):




git submodule
(base) ➜  submodule_ex git:(master) ✗ git submodule        
+97c0476d96eb1fe7d209dd1c448ad01b1f701e9c sub-1 (remotes/origin/HEAD)
+b04045e2798a71a3580522a8b1f1c2d10baf8358 sub-2 (remotes/origin/HEAD)

current checkout ver:97c0476d96eb1fe7d209dd1c448ad01b1f701e9c
+ sign means that it hasnt commited yet




git pull --recurse-submodules
    pull not only all the submodules, but also the superproject at once




foreach ex)
git submodule foreach "git log --oneline; ls -al"






git clone superproject

git clone url(superproject)
    only clone submodule folder

if you want to clone submodule then
git submodule init {nameofsubmodule}
git submodule update (--remote)



clone everyting at once
git clone url --recurse



