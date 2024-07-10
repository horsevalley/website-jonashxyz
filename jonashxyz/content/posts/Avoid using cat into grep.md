---
id: Avoid using cat into grep
aliases: []
tags:
  - Article
  - Linux
  - CoreUtils
  - CLI
  - LukeSmith
date: "2024-07-10"
draft: false
title: Avoid using cat into grep
---

Let me open by saying that I am guilty of doing this myself.

Instead of doing `cat file1 file2 | grep -i searchTerm`, it is better to use [grep](https://www.gnu.org/software/grep/) directly. The result is not only more efficient, but it's more informative aswell.

## Here is why
I came across a [video](https://www.youtube.com/watch?v=82NBMvx6vFY) by [[Luke Smith]], where he explains why you should avoid using cat into grep. This video made me reflect on my own usage of [cat](https://www.gnu.org/software/coreutils/manual/html_node/cat-invocation.html#cat-invocation), and what it's really meant for, which is concatenate and write files. 

Look at the following output of running `cat file1 file2 | grep -i fox`:

```bash
cat file1 file2 | grep -i fox
The quick brown fox jumps over the lazy dog.
foxes are beautiful animals
```

Now take a look at the output, using only grep. Do you notice a difference?

```bash
grep -i fox file1 file2
file1:The quick brown fox jumps over the lazy dog.
file2:foxes are beautiful animals
```

Not only do we save memory by eliminating the use of another program (cat), but we also get information about which files the search string appears in.

Changing a bad habit that is engrained in your mind can be a real struggle, but I will do my best to adopt this new way of searching.

## Links :

202407101228

https://www.youtube.com/watch?v=82NBMvx6vFY

https://www.gnu.org/software/coreutils/manual/html_node/cat-invocation.html#cat-invocation

https://www.gnu.org/software/grep/

