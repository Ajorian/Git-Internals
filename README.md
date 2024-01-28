# Git-Internals
Here, I hope you can find valuable information about Git internals and gain insights into its functioning through low-level commands, commonly referred to as Git plumbing commands.

## Dependencies
Requires [Git](https://git-scm.com/) to be installed and in the `PATH` environment variable. To check that open your terminal and run the following command to check your installed version of Git.

````
    git --version
````
## What is Git?
Almost everyone familiar with Git would describe it as version control software or something similar. However, in this investigation, we will delve into its internal structure. From this perspective, Git can be seen as a collection of `objects` and `pointers` capable of forming graph structures, as depicted in the picture below. These structures are stored in nonvolatile memory.

<img src="graph.png" width="128"/>
![Git is a collection of Objects and Pointers](graph.png| width=100)

As you can see in the picture, we have some 'objects' (circles) with the ability to point to other objects, as well as some arrows (ptr1, ptr2, etc.) that can point to these objects. But wait! What is a pointer, and why is it important to us?

In brief, a pointer is essentially a SHA-1 hash of a Git object. It holds significant importance as it appears throughout the Git internal structure, including data fields of certain objects and files such as the one that stores branches.
