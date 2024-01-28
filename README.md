# Git-Internals
Here you can find some useful information about Git internals and see how it works using low level commands, so called Git plumbing commands.

## Dependencies
Requires [Git](https://git-scm.com/) to be installed and in the `PATH` environment variable. To check that open your terminal and run the following command to check your installed version of Git.

````
    git --version
````
## What is Git?
For this question almost every one, who is familiar with Git, would say that it is a supper version control infrastracture. But here I want to ivestigate its internal structre. So I would say Git is a collection of 'objects' and 'pointers' as the following picture depicts.

![Git is a collection of Objects and Pointers](git.png)
