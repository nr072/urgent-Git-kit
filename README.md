# Urgent Git kit

Using Git is a hassle. And understanding it seems quite impossible for most of us mere mortals. But there comes a time when you have to upload all your codes to GitHub in an hour's notice because someone important will (read may or may not) see them. But in that tiny, excruciating hour, no matter how many videos of you watch, you simply do _not_ get this Git thing.

Solution? Here are some of the basic commands of Git that you can learn to use under an hour.

The instructions here are simple how-to's for the most basic Git commands - They **DO NOT** explain the inner workings or logic of how Git works. The analogies have deliberately been chosen to be childish, just so you can get the hang of using it in a very short time. If you are interested to know more about it, you will have to try on your own. You can use these instructions to train a monkey, but that's about it.

So, let's not learn Git, (for now) just learn to use it!

## Why use Git?

You may have heard that Git is used for version controlling. It is used to preserve different versions of files. You may save (and see later) all 50 versions of a particular file you changed again and again. Or you may see a previous version of your entire project - kind of like freezing your whole project at that point and seeing it in thee exact same way later.

Another crucial part Git plays in of development is aiding in collaboration. Imagine 10 different developers all working on different parts of the same project, all updating and removing codes every day. How does one merge all their works and make a single software out of it? Organize a meeting every time someone adds a comment to their code? Git helps here by keeping log of exactly what got changed (added and removed) and when and by whom. It also helps in merging the works of two people into one chunk of code. It is actually pretty neat, if you think about it.

Anyway, if you do not like the idea of collaboration, no need to worry. Just concentrate on the version-controlling part. Because, sooner or later you _will_ realize just how helpful it is to be able to find out how on earth you managed to solve that particular problem in your third re-write!

Let's start!



- - -

By the way, this, ahem, _tutorial_ is for someone using a Linux terminal. I have no idea if the `cd` command works in Windows command-line, but all Git commands will work in Command Prompt. For further assistance - or _any_ assistance whatsoever - about Git, see Git's [documentation](https://git-scm.com/book/en/v2/Getting-Started-The-Command-Line).

Also, these instructions are solely terminal-based. Nothing about Git GUI tools is mentioned here. You may be using some awesome GUI tool, your choice (to be honest, they make things a little better for the brain). But if you are, these will probably not help you in any way.

- - -





## Consider a scenario

For simplicity's sake, we will assume that you have an assignment of writing a world-class rhyme within a month. You are free to get help from others. You may submit as many rhymes as you want, or even different variations of a single one. If only one gets selected, it will be enough.

For multiple rhymes, there is nothing to worry about - there will obviously be separate files. But what about different variations of the same one? What will you name them? `rhyme.txt`, `rhyme_dads-suggestion.txt`, `rhyme_mums-corrections.txt`, `rhyme_spellings-corrected.txt`, `rhyme_i-like-it-most.txt`, and `rhyme_more-spellings-corrected.txt`? They do make you feel like you are doing some real hard work, but all these also are a tiny bit hard to manage.

But what if you could pack all of these into a single file?

Git comes to the rescue!

You wrote the first draft; consider it version 1. You corrected spelling mistakes; tag it as version 2. Inserted some really big and hard words; call it version 3. And so on. You can have as many versions as you want. _And_ you can check out a previous version at _any_ time you want!



### The complication!

Suppose, after reaching your 3rd revision, Dad comes up and gives you some advice on the rhyme. You are unsure whether they will work or not. What do you do? You make a copy of your rhyme and apply Dad's suggestions to _that_. Let's call it your Dad's copy. You leave your original rhyme as is because it is yours and too valuable to alter.

The next day, you learn a new word that will go smashingly with your rhyme. Since you do not want to waste such an awesome word, you apply it to _both_ rhymes - your original _and_ Dad's copy.

Then you learn some more grammar, and more about rhymes, and apply the knowledge to both your copies. At the end of the week, your original copy is in its 16th version, and Dad's copy is in its 13th. Now, Mum sees your Dad's copy and she has some rather harsh things to say about it. You note down her words but since you are rather fond of Dad's copy, you make a _3rd_ copy and apply Mum's corrections to _that_ instead.

Now you have 3 copies of the same rhyme, all growing up simultaneously but different from each other.

Afterwards, cool new punctuation rules get applied to all 3 copies. New styles are added: the title is written in red, cursive letters. The author's (your) name is added at the bottom, written in a stylized text. At the end of the month, you have 97 versions of your own rhyme, 94 versions of Dad's copy, 81 versions of  Mum's copy, and a dozen more from friends and cousins and cousins' friends.

Just think how many pages you are going to submit.

**Git saves your life here.**

Git keeps track of and manages _all_ the versions and copies of your rhyme. And even if you had written some hundred more rhymes, each with their own villages full of versions of different ages and importances, Git is the **one tool to track them all!**





## Apply Git to the scenario: Versioning



### Start Git

Since Git is not nosy by default, you will need to tell it to start keeping track of things first. You do it by running the `git init` command in the directory where your file is.

Suppose the name of your file is `baa-baa-black-sheep.txt`, and it is in a folder named `best-rhyme`. `cd` to the folder and `git init` there.

If you have Git installed, you will see something like:

```
$ git init

Initialized empty Git repository in /path/to/your/folder/best-rhyme/.git/
```

Means Git now knows it has work to do here.



### See the current condition of things

Now you can check what Git knows about this folder (or directory) using `git status`:

```
$ git status

On branch master
Initial commit
Untracked files:
  (use "git add <file>..." to include in what will be committed)
	baa-baa-black-sheep.txt
nothing added to commit but untracked files present (use "git add" to track)
```

(Quick tip, in case you are new to the terminal: The `$` symbol is not part of the command. If should appear by itself every time you press `Enter`.)



### Start keeping track

Your `baa-baa-black-sheep.txt` file's name will be written in red. That means Git is not tracking it, which is Git's way of saying it currently does not care about that file and will not keep track of your changes in it.

To make Git start caring you need to `git add` the file. Then the file name will appear in green, which means Git will now keep track of different versions of it (as long as you tell it to):

```
$ git add baa-baa-black-sheep.txt
$ git status

On branch master
Initial commit
Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
	new file:   baa-baa-black-sheep.txt
```



### Make changes

Now let's write the first line of the rhyme: "Baa, baa, black sheep," and take some rest for today. But it is a revolutionary line and may change the world, so you need to tag it as a version, just in case.



### Mark changes for new version

But first you need to let Git know that you made changes and it should remember these changes as the next version. So `git add` again:

```
$ git add baa-baa-black-sheep.txt
```



### Create a version

The "tagging as a version" is called "committing changes" in Git's language. After adding the file (or the changes), you tell Git to remember them as the next version and tell it to also remember some comments about the changes (why you made those particular changes).

So, you try to `git commit`:

```
$ git commit

*** Please tell me who you are.
Run
  git config --global user.email "you@example.com"
  git config --global user.name "Your Name"
to set your account's default identity.
Omit --global to set the identity only in this repository.
fatal: empty ident name (for <userName@pcName.(none)>) not allowed
```



### Who made which changes?

You are allowed to take help from others, remember?

For each set of changes, or each commit, Git needs to remember who made the changes. Since you just did a `git init` about 10 minutes ago, Git has not had enough opportunity to get acquainted. You can skip the emotional stuff (read "editing conifg files") by simply setting a username and an email address here, which will be associated to further changes you make:

```
$ git config user.email "bestestAuthorInThe@world.com"
$ git config user.name "The Super Author"
```

If you feel uncomfortable about revealing your email address publicly when all of these are uploaded to GitHub, enable email privacy and get a GitHub-provided address from the "Primary email address" section on https://github.com/settings/emails (prerequisite: a GitHub account) and use that instead.



### Make a version (definitely this time)

Good, now Git knows you (inside this directory at least). Now, `git commit`.



### Why did I make these changes again?

Nano will probably open for you to write your commit message. If it does, just write something like "created text file" wherever the cursor has appeared, press `CTRL+Z` and then `Y` and then `Enter`. Your message should be safe with Git now.

If any other text editor is selected as your default one, write and save your commit message (what exactly you changed and/or why you did it) using that.



### Previous versions

You can see what Git remembers about this version using `git log`. You will see you commit message, along with some information on who made those changes and when.

You will also see a pretty long number-ish thing on the first line, after the word "commit". Consider it a unique ID for Git to identify each version of you rhyme separately.



### Changes and more changes (many, many versions)

Now that you have started revolutionizing the poetic universe one verse at a time, you can make changes from time to time: maybe add some lines, correct spelling mistakes, use punctuation marks properly, etc.

Use `git add` and `git commit` after every set of changes (for every new version you want to create). Always remember to check the condition of everything using `git status`. It will help you avoid mistakes and warn you in case something goes wrong.

If a file named something like `baa-baa-black-sheep.txt~` (with a `~` at the end) appears in red, ignore it. It is a temporary/backup file.



### Dad's copy

Now, many commits (versions) later, you are suffering from rhymer's block, and Dad comes to the rescue. He gives you some advice which you choose to apply. But to a _copy_ of your original rhyme.

Making a "copy" like this is called "creating a branch" in Git. A "branch" is an exact copy of the commit (version) it was branched off from.

For example, suppose you currently have 4 lines of the rhyme in your file, when Dad gave his advice. First thing you do is make a branch (copy) of your current commit (version):

```
$ git checkout -b dads-advice

Switched to a new branch 'dads-advice'
```

If you see a list of all branches (copies) now, you will find that there are two of them:

```
$ git branch -v

* dads-advice e5e1b88 added appropriate punctuations
  master      e5e1b88 added appropriate punctuations
```

Both of them are identical copies of each other - each containing the exact 4 lines.

And what is that "master" copy? Your original one, of course!

Now that you have a copy, you can apply Dad's advices to the `dads-advice` branch! Now, if you type `git status`, you will see your current branch is `dads-advice`, which had always been `master` until now (if you have noticed).

You can make as many changes in Dad's copy as you want. Just `git add` and `git commit` like before.



### Back to original copy again

But how to make changes to your original copy? Just change your current branch and go to `master` instead:

```
$ git checkout master

Switched to branch 'master'
```

`git log` will show you that this copy still is where you left it. Make changes and make newer versions. They will be counted as newer versions for this copy only.



### Another copy!

After you have been done some heavy literature work on both copies, one day Mum sees Dad's copy and proposes some changes. Since you do not want to displease Dad due to obvious reasons related to your pocket money nor do you want to irritate Mum for more obvious reasons, you make a copy of Dad's copy. Instead of changing Dad's words, you make a new one according to Mum's wish:

```
$ git status

On branch dads-advice
nothing to commit, working directory clean

$ git checkout -b mums-correction

Switched to a new branch 'mums-correction'
```



### More copies! More changes!!

Now you can use everyone's advice and make lots of copies and make everyone happy, without going crazy over managing so many versions. (You will still go a _little_ crazy if you go beyond 7 branches though.)

Every time you need to work on a copy, just `git branch -v` to see the list, `git checkout TARGET_BRANCH_NAME` to select that branch (`TARGET_BRANCH_NAME` here is a placeholder term; just replace it with the name of the branch you want to work on), and make changes:

```
$ git branch -v

  dads-advice     bb0caa2 added ellipsis
  master          0e3f523 added punctuation
* mums-correction 406698a added more punctuation

$ git checkout master 

Switched to branch 'master'
```

Then `git add` and `git commit` to make newer versions. Simple.



### See a particular version of a particular copy

You can check out a previous version of the copy you are currently working on any time you want. Just commit your current unsaved changes and use `git log` to get the unique commit ID of the version (commit) you want to see now. Copy the first 7 characters or so from the ID and use it with `git checkout`:

```
$ git checkout e5e1b88

Note: checking out 'e5e1b88'.
You are in 'detached HEAD' state. You can look around, make experimental
changes and commit them, and you can discard any commits you make in this
state without impacting any branches by performing another checkout.
If you want to create a new branch to retain commits you create, you may
do so (now or later) by using -b with the checkout command again. Example:
  git checkout -b new_branch_name
HEAD is now at e5e1b88... added appropriate punctuations
```

If you want to see a particular version of a copy of the rhyme you currently are _not_ working on, just `git checkout` that branch (copy) and then `git checkout` the commit (version) you want to see, in the same way.



### Getting back to the present

By the way, do not forget to `git checkout` back to the branch (copy) you were working on before you went to see the previous commit (version)!



### Uploading to GitHub

After your work is done (according to you), you can upload it to GitHub - either in a private repository just to store it there, or in a public repository so others can see it too.

On GitHub, create a repository (public or private - as you need it). Leave the "Initialize this repository with a README" option unchecked to push your work from the terminal to GitHub.



### But where on the Great and Omnipresent Internet do I upload?...

After you click the green button, you will see a link that looks like this: `https://github.com/USERNAME/best-rhyme.git` ("USERNAME" will be replaced by your GitHub username) in an input field-like box. Copy that, and in your terminal, add it as a "remote":

```
$ git remote add origin https://github.com/USERNAME/best-rhyme.git
```

You can see the list of remotes using `git remote -v`:

```
$ git remote -v

origin	https://github.com/USERNAME/best-rhyme.git (fetch)
origin	https://github.com/USERNAME/best-rhyme.git (push)
```



### TELL ME WHERE I CAN UPLOAD!

GitHub stores "repositories" (containing entire projects, lonely markdown files, nothing really, jack-of-all-trades JSON files, etc.) just like this one you have (and are working on) in your computer. But since GitHub is not your personal machine and there are millions of users with hundreds of repositories of their own, some references are needed to push people's works to the correct repositories. These "remotes" are the references. (You may have noticed that the URL is made of your username, followed by your repository name.)

`origin`, the default name of users' own repository's remote, is just a name to make it easier for humans to remember and identify. You could easily have named it `my-path-to-ultimate-fame` and Git would not mind a bit.



### Okay, so, how exactly do I upload stuff?

Now, to upload you need to `git push` your work - or, to be more precise, you changes - to your GitHub account. To push your original copy - meaning, the `master` branch - simply do this:

```
$ git push origin master

Username for 'https://github.com':
Password for 'https://USERNAME@github.com':
Counting objects: 27, done.
Delta compression using up to 4 threads.
Compressing objects: 100% (24/24), done.
Writing objects: 100% (27/27), 2.38 KiB | 0 bytes/s, done.
Total 27 (delta 4), reused 0 (delta 0)
remote: Resolving deltas: 100% (4/4), done.
To https://github.com/USERNAME/best-rhyme.git
 * [new branch]      master -> master
```

Type your username and password when the prompts appear. If your password does not appear as you type, no need to get worried or anything. It is supposed to do that. Call it a security measure. Just press `Enter` when you are finished typing password and a lot of lines will appear. If they resemble the lines shown above, it will basically mean your "push" has been successful.

You can see the last line indicates that your `master` branch has been uploaded to GitHub as `master`.



### Uploading more branches (copies)

To "push" more/other branches, just change the branch name in the previous command:

```
$ git push dads-advice

Username for 'https://github.com':
Password for 'https://USERNAME@github.com': 
Counting objects: 16, done.
Delta compression using up to 4 threads.
Compressing objects: 100% (12/12), done.
Writing objects: 100% (12/12), 1.07 KiB | 0 bytes/s, done.
Total 12 (delta 3), reused 0 (delta 0)
remote: Resolving deltas: 100% (3/3), done.
remote: 
remote: Create a pull request for 'dads-advice' on GitHub by visiting:
remote:      https://github.com/USERNAME/best-rhyme/pull/new/dads-advice
remote: 
To https://github.com/USERNAME/best-rhyme.git
 * [new branch]      dads-advice -> dads-advice
```

Or just push all of them together:

```
$ git push --all

Username for 'https://github.com':
Password for 'https://USERNAME@github.com': 
Counting objects: 15, done.
Delta compression using up to 4 threads.
Compressing objects: 100% (9/9), done.
Writing objects: 100% (9/9), 832 bytes | 0 bytes/s, done.
Total 9 (delta 3), reused 0 (delta 0)
remote: Resolving deltas: 100% (3/3), completed with 1 local object.
remote: 
remote: Create a pull request for 'mums-correction' on GitHub by visiting:
remote:      https://github.com/USERNAME/best-rhyme/pull/new/mums-correction
remote: 
To https://github.com/USERNAME/best-rhyme.git
 * [new branch]      mums-correction -> mums-correction
```

(Since there was only one more branch left in this case, only that was pushed. If more existed, all would have been pushed to GitHub.)
