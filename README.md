# Git-Internals
Here, I hope you can find valuable information about Git internals and gain insights into its functioning through low-level commands, commonly referred to as Git plumbing commands.

## Dependencies
Requires [Git](https://git-scm.com/) to be installed and in the `PATH` environment variable. To check that open your terminal and run the following command to check your installed version of Git.

````
    git --version
````
## What is Git?
Almost everyone familiar with Git would describe it as version control software or something similar. However, in this investigation, we will delve into its internal structure. From this perspective, Git can be seen as a collection of `objects` and `pointers` capable of forming graph structures, as depicted in the picture below. These structures are stored in nonvolatile memory.

<p align="center">
    <img src="graph.png" width="400" height="260" title="Graph structure of Git objects" >
</p>

As you can see in the picture, we have some 'objects' (circles) with the ability to point to other objects, as well as some arrows (ptr1, ptr2, etc.) that can point to these objects. But wait! What is a pointer, and why is it important to us?

In brief, a pointer is essentially a SHA-1 hash of a Git object. It holds significant importance as it appears throughout the Git internal structure, including data fields of certain objects and files such as the one that stores branches.

## Objects and Pointers
Git has three types of objects, namely Blobs, Trees, and Commits. It's worth noting that these objects are represented as files stored within the .git/objects folder. They adhere to a specific naming convention, whereby the name of an object corresponds to the SHA-1 hash of its content. Importantly, this SHA-1 hash serves as a pointer to the respective object. So when you see these SHA-1 hashes you can think of them as simple pointers!

## Blobs
A Blob, abbreviated as Binary Large OBject, is similar to a buffer where raw data can be stored. As the name implies, this Git object lacks any form of metadata, such as timestamps or owner information. Furthermore, it does not possess the ability to point to other objects through SHA-1 hashes. From my perspective, the most effective way to understand a Blob is to envision it as a buffer in which any type of data including text, image, binaries, ... can be stored. The following picture illustrates an imaginary Blob.

<p align="center">
    <img src="blob.png" title="Blob"  width="400" height="260">
</p>
