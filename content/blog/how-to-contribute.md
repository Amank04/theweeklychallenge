---
title: "HELP: How to contribute?"
date: 2020-04-03T00:00:00+00:00
description: "Instructions how to contribute to Perl Weekly Challenge."
type: post
image: images/blog/how-to-contribute.jpg
author: Mohammad S Anwar
tags: ["Perl", "Raku"]
---

## HELP: How to contribute?
---

<br>

### Just submit Pull Request to [**GitHub repository**](https://github.com/manwar/perlweeklychallenge-club) with your solutions.

<br>

First find out the latest challenge folder, more likely the highest numbered folder is the latest challenge folder e.g. challenge-002. If you are an existing member, you would probably find a folder by your name. For example, if your name is **"Joe Blog"** then there would be a folder called **"joe-blog"**. Under your named folder, you would find a file **README**. Depending on your choice of language, you should create a folder here e.g. **perl** for **Perl** and **raku** for **Raku**. Please keep everything lowercase. Inside each of these folders you can save your solutions. If it is perl script for **Task #1** then call it **ch-1.pl**. Similarly if it is perl script for **Task #2** then call it **ch-2.pl**. For **Raku** solutions, call it **ch-1.raku** and **ch-2.raku** respectively. And if you are writing one-liner then call it **ch-1.sh** or **ch-2.sh**. If you are contributing for the first time, please create your named folder as described above. Also let us know what name you would like us to use?

In case you have created a blog about your solutions, then create a file called **blog.txt** and save the link in the file. In case you have more than one blog then create another file called **blog1.txt** and add your link there.

## Step-by-step instructions
---

Let us assume you want to submit solutions for **Challenge 002** and your Github user name is **joe-blog**.

<br>

#### 1) If you are submitting the solution for the first time then you have to **fork** the [**repository**](https://github.com/manwar/perlweeklychallenge-club) by clicking the "**Fork**" button in the top right corner and should have repository e.g. **https://github.com/joe-blog/perlweeklychallenge-club**.

<br>

#### 2) Go to your favourite terminal and **clone** your repository.

```
   $ git clone https://github.com/joe-blog/perlweeklychallenge-club
```

<br>

#### 3) Create a new branch for the solution.

```
   $ cd perlweeklychallenge-club
   $ git checkout -b new-branch
```

<br>

#### 4) Go to the **Challenge 002** folder.
```
   $ cd challenge-002
```

<br>

#### 5) If you find a folder with your name in the current folder then skip to next step otherwise create a new folder.
```
   $ mkdir joe-blog
```

<br>

#### 6) Change into your named folder.
```
   $ cd joe-blog
```

<br>

#### 7) If you just created the folder then you should add a file **README** and add a line **Solution by Joe Blog** otherwise skip to next step.
```
   $ cat README

   Solution by Joe Blog.
```

<br>

#### 8) If you want to submit **Perl** solutions then you should create a folder **perl** (if not already created). Similarly if you want to submit **Raku** solutions then you should create a folder **raku** (if not already created).

<br>

#### 9) Change into your relevant folder depending on your choice.
```
   $ cd perl
```

or


```
   $ cd raku
```

<br>

#### 10) Now you are ready to add your solutions. If it is for the **Task #1** then create a file named **ch-1.pl** or **ch-1.raku** or **ch-1.sh**. Similarly, if it is for the **Task #2** then create a file named **ch-2.pl** or **ch-2.raku** or **ch-2.sh**.

<br>

#### 11) Once you are happy with your solutions, you should **add** it to the repository. First go back to **root** of the repository and then fire the command below:
```
   $ git add challenge-002/joe-blog
```

<br>

#### 12) Commit your changes now.
```
   $ git commit
```

<br>

#### 13) Push your changes.
```
   $ git push -u origin new-branch
```

<br>

#### 14) Now go to your forked repository in GitHub web portal **https://github.com/joe-blog/perlweeklychallenge-club**

<br>

#### 15) You should see a button to submit **Pull Request**.

<br>

## How to add new solution when you already have the forked repository?
---

Let us assume you already have the repository forked. If this is the first time you are using the same forked respository for submitting subsequent challenges solution. I also assume your GitHub user name is **joe-blog**.

<br>

#### 1) Checkout out the **master** branch first.
```
   $ git checkout master
```

<br>

#### 2) Check if you have setup **upstream**.
```
   $ git remote -v
```

<br>

You should see something similar:
```
   origin  https://github.com/joe-blog/perlweeklychallenge-club (fetch)
   origin  https://github.com/joe-blog/perlweeklychallenge-club (push)
   upstream        https://github.com/manwar/perlweeklychallenge-club (fetch)
   upstream        https://github.com/manwar/perlweeklychallenge-club (push)
```

<br>

If you don't see **upstream** as above then you need to setup your **upstream** like below:

<br>

```
   $ git remote add upstream https://github.com/manwar/perlweeklychallenge-club
```

<br>

Check if you have everything setup correctly.

<br>

```
   $ git remote -v
```

<br>

If you see similar output as above then you have setup **upstream** correctly. You only need to do it **once**.

<br>

#### 3) Now we need to **fetch** latest changes from the **upstream**.
```
   $ git fetch upstream
```

<br>

#### 4) We will now merge the changes into your local **master** branch.
```
   $ git checkout master
   $ git merge upstream/master --ff-only
```

<br>

#### 5) Then push your **master** changes back to the repository.
```
   $ git push -u origin master
```

<br>

#### 6) Now it is time create new branch for new challenge
```
   $ git checkout -b branch-for-challenge-005
```

<br>

#### 7) Once you have a new **branch** ready, you can start adding your solutions or blog information.
```
   $ cd challenge-005/joe-blog
   $ echo "URL to the blog" > blog.txt
   $ mkdir perl
   $ cd perl
```

Add script like **ch-1.pl** or **ch-2.pl** or **ch-1.sh** or **ch-2.sh**

Or if its **Raku** solutions then follow this:

```
   $ mkdir raku
   $ cd raku
```

Add script like **ch-1.raku** or **ch-2.raku** or **ch-1.sh** or **ch-2.sh**

<br>

#### 8) Test your script now.

<br>

#### 9) Commit your changes.
```
   $ git add challenge-005/joe-blog
   $ git commit
```

<br>

#### 10) Now push the newly created branch **branch-for-challenge-005**
```
   $ git push -u origin branch-for-challenge-005
```

<br>

#### 11) Time to submit your changes as **Pull Request**. Go to your GitHub web profile:

    https://github.com/joe-blog/perlweeklychallenge-club

You should see button to create **Pull Request**.

If you have any trouble with the above instructions then please get in touch with me anytime <mohammad.anwar@yahoo.com>.
