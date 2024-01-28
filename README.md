# Git-Internals
Here you can find some useful information about Git internals and see how it works using low level commands, so called Git plumbing commands.

## Dependencies
Requires [Git](https://git-scm.com/) to be installed and in the `PATH` environment variable. To check that open your terminal and run the following command to check your installed version of Git.

````
    git --version
````
## What is Git?
Almost every one, who is familiar with Git, would say that Git is a version control software (or somthing similar). But here I want to ivestigate its internal structre, So I would say that Git is a collection of 'objects' and 'pointers' with the ability of forming graph structures like the one you see in the following picture and store it on a nonvolatile memory.

![Git is a collection of Objects and Pointers](graph.png)

As you can see in the picture, we have some 'objects' (circles) with the ability to point to other objects, as well as some arrows (ptr1, ptr2, etc.) that can point to these objects. But wait! What is a pointer, and why is it important to us?

In brief, a pointer is essentially a SHA-1 hash of a Git object. It holds significant importance as it appears throughout the Git internal structure, including data fields of certain objects and files such as the one that stores branches.
