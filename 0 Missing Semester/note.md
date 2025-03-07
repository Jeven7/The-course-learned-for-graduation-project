# Missing Semester
The specific notes can be seen on the lecture website https://missing.csail.mit.edu/2020/
## Lecture 1 Shell
absolute path start with'/'
In relative path, '.' means current dir, '..' means parent dir
'cd ~' go to the home directory
'cd -' go to the previous directory
'mv file1 file2' means rename the file
'cp path1 path2' means copy file
'mkdir 'name'' creat the file
'cat file1' print contents of file1
'cat <hello.txt > hello2.txt' means using the content of hello.text as the input and write anything cat print to the hello2.txt
">>" means append instead of overwrite
"|" pipe means take the output of the program to the left and make it the input of the program to the right 

## Lecture 6 Git
In git, folders called "tree" and files called "blob".
Git uses a directed acyclic graph to model history

### git Data model, as pseudocode 
    // a file is a bunch of bytes
        type blob = array<byte>

    // a directory contains named files and directories
    type tree = map<string, tree | blob>

    // a commit has parents, metadata, and the top-level tree
    type commit = struct {
        parents: array<commit>
        author: string
        message: string
        snapshot: tree
    }

### Objects and content-addressing
An “object” is a blob, tree, or commit:
    `type object = blob | tree | commit`
In Git data store, all objects are content-addressed by their SHA-1 hash.
    objects = map<string, object>

    def store(object):
        id = sha1(object)
        objects[id] = object

    def load(id):
        return objects[id]

### Reference
    references = map<string, string>

    def update_reference(name, id):
        references[name] = id

    def read_reference(name):
        return references[name]

    def load_reference(name_or_id):
        if name_or_id in references:
            return load(references[name_or_id])
        else:
            return load(name_or_id)

### Git command

#### Basics 
- git help <command>: get help for a git command
- git init: creates a new git repo, with data stored in the .git directory
- git status: tells you what’s going on
- git add <filename>: adds files to staging area
- git commit: creates a new commit
    - Write good commit messages!
    - Even more reasons to write good commit messages!
- git log: shows a flattened log of history
- git log --all --graph --decorate: visualizes history as a DAG
- git diff <filename>: show changes you made relative to the staging area
- git diff <revision> <filename>: shows differences in a file between snapshots
- git checkout <revision>: updates HEAD and current branch

#### Branching and merging
- git branch: shows branches
git branch <name>: creates a branch
- git checkout -b <name>: creates a branch and switches to it
    - same as git branch <name>; git checkout <name>
- git merge <revision>: merges into current branch
- git mergetool: use a fancy tool to help resolve merge conflicts
- git rebase: rebase set of patches onto a new base

#### Remotes
- git remote: list remotes
- git remote add <name> <url>: add a remote
- git push <remote> <local branch>:<remote branch>: send objects to remote, and update remote reference
- git branch --set-upstream-to=<remote>/<remote branch>: set up correspondence between local and remote branch
- git fetch: retrieve objects/references from a remote
- git pull: same as git fetch; git merge
- git clone: download repository from remote

#### Undo
- git commit --amend: edit a commit’s contents/message
- git reset HEAD <file>: unstage a file
- git checkout -- <file>: discard changes

### Advanced Git
- git config: Git is highly customizable
- git clone --depth=1: shallow clone, without entire version history
- git add -p: interactive staging
- git rebase -i: interactive rebasing
- git blame: show who last edited which line
- git stash: temporarily remove modifications to working directory
- git bisect: binary search history (e.g. for regressions)
- .gitignore: specify intentionally untracked files to ignore