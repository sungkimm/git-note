# git submodule

```
repository structure

├── superproject
│   ├── README.md
│   ├── ...
│   ├── submodule1
│   ├── submodule2

 ```

## Add submodule to superproject
Add the latest commited submodule **with files and directory** inside the submodule from remote
``` bash
$ cd superproject
$ git submodule add url {define submodule name(optional)}
$ ls 

ex) 

├── superproject
│   ├── README.md
│   ├── ...
│   ├── submodule1
```    

## Update(pull) submodule from remote
***

Assume your repository structure is like the followings:
```
repository structure

├── superproject
│   ├── README.md
│   ├── ...
│   ├── submodule1
│   ├── submodule2

 ```

### 1. pull inside submodule
``` bash
$ cd submodule1
$ git pull
$ cd ..
$ git push # if needed
``` 

### 2. update(pull) 
Pull every submodule inside superproject at once.  
`--remote` option pulls from remote. Without remote option, it pulls the commit already specified in the superproject(local). 
``` bash
$ git submodule update --remote
# or 
$ git submodule update (from local)
```    


## Submodule summary/log check
### `git submodule summary`
ex)  

``` bash
$ superproject git:(master) ✗ git submodule summary
* sub-1 4ad935c...97c0476 (1):
        current commit:4ad935c
        current checkout (by remote):97c0476 --> HEAD is ahead in this case.  this might happen when you git submodule update --remote and pulls the most updated version; your HEAD points to the latest version, but your commit is behind.

* sub-2 dd31051...b04045e (2):
``` 


### `git submodule`
``` bash
(base) ➜  superproject git:(master) ✗ git submodule        
+97c0476d96eb1fe7d209dd1c448ad01b1f701e9c sub-1 (remotes/origin/HEAD)
+b04045e2798a71a3580522a8b1f1c2d10baf8358 sub-2 (remotes/origin/HEAD)

current checkout ver:97c0476d96eb1fe7d209dd1c448ad01b1f701e9c
+ sign means that it hasnt commited yet -> this might happen when you git submodule update --remote and pulls the most updated version; your HEAD points to the latest version, but your commit is behind.
```


### pull superproject and every submoudule
Pulls not only all the submodules, but also the superproject at once
``` bash 
$ cd superproject
$ git pull --recurse-submodules
```

### Run command for each submodule
Use `git submodule foreach` 
ex)
``` bash
$ git submodule foreach "git log --oneline; ls -al"
```


## Cloning superproject

### Cloning superproject and submodule folder only(files inside submodule not included)
``` bash
$ git clone url(superproject url)
```


### Cloning submodule(including files)
After `git clone url`, if you want to clone submodule including files then
``` bash
$ git submodule init {name_of_submodule}
$ git submodule update (--remote)
```

### Cloning everything at once
``` bash
$ git clone url --recurse
```


