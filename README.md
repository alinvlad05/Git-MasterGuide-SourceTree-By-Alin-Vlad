# Sourcetree

A Git GUI that offers a visual representation of your repositories.(Rank 1 in top git software)<br/>
Download: https://www.sourcetreeapp.com/ <br/>
  
# Git  
A version control system is a tool that lets you track the history and attribution of your project files <br/>
over time (stored in a repository), and which helps the developers in the team to work together.  <br/> 
  
Create a new repository:git init <br/> 
Get your own repository instance:Create on GitHub a new repository and copy address. <br/> 
Open command line and navigate to the chosen directory: <br/>
git clone https://git.company.com/random (address) <br/>

Add files: <br/> 
git add (filename)<br/>
git status –s<br/>
It shows:A  file   <br/>
A=added<br/> 

Publishing changes:<br/>
git push<br/>

If another developer clone the same repository and then modify a file:<br/>
Show differences(review the actual changes with the diff command):<br/>
git diff<br/>

Commit the changes:<br/>
git commit -a -m "Message"<br/>

Moving files:<br/>
git mv random.txt src\<br/>
git mv (file) (location)<br/>

Rename random.txt to rand.txt<br/>
git mv src\random.txt src\rand.txt<br/>

Use pull to bring in changes:<br/>
git pull<br/>

Create a tag:<br/>
Create a tag so you can more easily access/refer to the released version.<br/>
Use an annotated tag for this;<br/>
git tag -a -m "random v0.1" v0.1<br/>

Remove a file:<br/>
git rm -f (filename)<br/>

Undo changes to a file:<br/>
git checkout -- src\rand.txt<br/>

If you don't remember how to revert a particular type of change, or to <br/>
update what is to be committed (using git commit without -a), the <br/>
output of git status (without -s) contains information about what commands to use.<br/>
git status<br/> 

To isolate this line of development from other changes, create your own named branch, and switch to it: <br/>
git checkout -b better-random  <br/>

Instead of using the git checkout –b better-random shortcut to  <br/>
create a new branch and switch to it in one command invocation, you <br/>
could have first created a branch with git branch better-random, <br/>
then switched to it with git checkout better-random.<br/>

Git just wants you to set up a remote origin as the upstream for the newly <br/>
created branch (it is using a simple push strategy); this will also push this branch <br/>
explicitly.<br/>

git push --set-upstream origin better-random<br/> 

Merging a branch:<br/>
git merge origin/better-random<br/>

Undoing an unpublished merge:<br/>
git reset --hard @{1}<br/>

The structure that Git uses (on the abstract level) to represent the possible non-linear  <br/>
history of a project is called a Directed Acyclic Graph (DAG).<br/>
A directed graph is a data structure from computer science (and mathematics) <br/>
composed of nodes (vertices) that are connected with directed edges (arrows). <br/>
A directed graph is acyclic if it doesn't contain any cycles, which means that there is no <br/>
way to start at some node and follow a sequence of the directed edges to end up back <br/>
at the starting node.<br/>

Usually, the DAG of revisions is laid out left-to-right (root nodes on the left, leaves on the right) <br/>
or bottom-to-top (the most recent revisions on top). ASCII-art examples in <br/>
Git documentation use the left-to-right convention, while the Git <br/>
command line use bottom-to-top, that is, the most recent first convention.<br/>

There are two special type of nodes in any DAG:<br/>

Root nodes: These are the nodes (revisions) that have no parents (no outgoing edges).<br/>
There is at least one root node in the DAG of revisions, <br/>
which represents the initial (starting) version of a project.<br/>

Leaf nodes (or leaves): These are the nodes that have no children (no incoming edges);<br/>
there is at least one such node. They represent the most <br/>
recent versions of the project, not having any work based on them. Usually, <br/>
each leaf in the DAG of revisions has a branch head pointing to it.<br/>

A branch operation is what you use when you want your development process to  <br/>
fork into two different directions to create another line of development.<br/>

A tag operation is a way to associate a meaningful symbolic name with the specific <br/>
revision in the repository<br/>

Both branches and tags, sometimes called references (refs) together.<br/>

Git, needs to know which branch tip to advance when creating a new <br/>
commit. It needs to know which branch is the current one and is checked out into <br/>
the working directory. Git uses the HEAD pointer for this.<br/>
Usually, this points to one of branch tips, which, in turn, points to some node <br/>
in the DAG of revisions, but not always-the detached HEAD situation; hat is, when <br/>
HEAD points directly to a node in the DAG.<br/>

Git stored branches and tags in files inside .git <br/>
administrative area, in the .git/refs/heads/ and .git/<br/>
refs/tags/ directories, respectively. <br/>

The HEAD pointer (usually a symbolic reference,for example ref: <br/>
refs/heads/master) is stored in .git/HEAD.<br/>
The master branch is stored in .git/refs/heads/master, <br/>
and has refs/heads/master as full name <br/>
(branches reside in the refs/heads/ namespace).<br/>

The remote-tracking branch, origin/master, which remembers <br/>
the last seen position of the master branch in the remote <br/>
repository, origin, is stored in .git/refs/remotes/origin/master,<br/>
and has refs/remotes/origin/master as its full name. <br/>
The v1.3-rc3 tag has refs/tags/v1.3-rc3 as the full name <br/>
(tags reside in the refs/tags/ namespace).<br/>


In Git, each revision is given a unique identifier (object name), which is a SHA-1 hash  <br/>
function, based on the contents of the revision. You can select a commit by using its <br/>
SHA-1 identifier as a 40-character long hexadecimal number (120 bits).<br/>

It is not necessary to give a full 40 characters of the SHA-1 identifier. Git is smart <br/>
enough to figure out what you meant if you provide it with the first few characters of <br/>
the SHA-1 revision identifier, as long as the partial SHA-1 is at least four characters <br/>
long. To be able to use a shortened SHA-1 to select revision, it must be long enough <br/>
to be unambiguous, that is, there is one and only one commit object which SHA-1 <br/>
identifier begins with given characters.<br/>
For example, both dae86e1950b1277e545cee180551750029cfe735 and dae86e <br/>
name the same commit object, assuming, that there is no other object in <br/>
your repository whose object name starts with dae86e.<br/>

You can also request that Git use the shortened SHA-1 in place of the full SHA-1 <br/>
revision identifiers with the --abbrev-commit option. By default, Git will use at <br/>
least seven characters for the shortened SHA-1; you can change it with the optional <br/>
parameter, for example, --abbrev-commit=12.<br/>

If you place ^ at the end of a revision name, Git resolves it to mean a (first) parent  <br/>
of that revision.<br/>
As a special case, ^0 means the commit itself;<br/>
This suffix syntax is composable. You can use HEAD^^ to mean grandparent of HEAD, <br/>
and parent of HEAD^.<br/>

As a special case, ~ is equivalent to ~ 1, so, for example, HEAD~ and HEAD^ are equivalent. <br/>
And, HEAD~2 means the first parent of the first parent, or the grandparent, and is <br/>
equivalent to HEAD^^.<br/>

Every time your HEAD and your branch head are updated for any reason, Git stores <br/>
that information for you in this local temporary log of ref history.<br/>

To specify the nth prior value of HEAD in your local repository, you can use <br/>
the HEAD@{n} notation that you see in the git reflog output. It's same with <br/>
the nth prior value of the given branch, for example, master@{n}.<br/>

The suffix, @{upstream} (short form <refname>@{u}), which can be applied only to <br/>
a local branch name, selects the branch that the ref is set to build on top of.<br/>

Commands, given a single revision as an argument, will show the set of commits reachable <br/>
from that revision, following the commit ancestry chain, all the way down to the root commits.<br/>
  
Double dot notation<br/>
The range, HEAD ~ 4..HEAD, means four commits: HEAD, HEAD^, HEAD^^, and HEAD^^^ <br/>
or in other words, HEAD ~ 0, HEAD ~ 1, HEAD ~ 2, and HEAD ~ 3, assuming that there are no merge <br/>
commits starting between the current branch and its fourth ancestor.  <br/>
  
In view of nonlinear history the double-dot notation A..B, or "between <br/>
A and B", is defined as reachable from A and not reachable from B.<br/>
  
Say your branches master and experiment diverge. You want to see <br/>
what is in your experiment branch that hasn't yet been merged into your master <br/>
branch. You can ask Git to show you a log of just those commits with master..experiment.<br/>
If, you want to see the opposite—all the commits in master that <br/>
aren't in experiment—you can reverse the branch names. <br/>
The experiment..master notation shows you everything in master not reachable from experiment.<br/>
  
Git allows you to exclude the commits that are reachable from a given revision by <br/>
prefixing the said revision with a ^.<br/>
Git allows you to use the --not option, which negates all the following <br/>
revisions.<br/>
  
There is another useful shortcut, namely A^!, which is a range composed of a single <br/>
commit. For non-merge commits, it is simply A^..A.<br/>
For merge commits, the A^!, excludes all the parents. With the help of yet <br/>
another special notation, namely A^@, denoting all the parents of A (A^1, A^2,…, A^n), <br/>
we can say that A^! is a shortcut for A --not A^@.<br/>
  
  Triple-dot notation<br/>
The last major syntax for specifying revision ranges is the triple-dot syntax, A...B. It <br/>
selects all the commits that are reachable by either of the two references, but not by <br/>
both of them.<br/>

# Index/Staging Area<br/>
   Let's consider what happens when we use the git <br/>
add command to add a file, but did not yet create a new commit adding it.<br/>
A version control system needs to store such information somewhere. Git uses something <br/>
called the index for this; it is the staging area that stores information that will go into <br/>
the next commit. The git add <file> command stages the current contents (current version) of the file, <br/>
adding it to the index.<br/>
  
git add takes the content of the file from the working directory and puts it into the staging area.<br/>
  
git commit -a command (which is git commit --all), which will take all the changed tracked files,<br/>
add them to the staging area (as if with git add -u, at least in modern Git), and create a new <br/>
commit.The new files still need to be explicitly git add to be tracked, and to be included in the new commit.<br/>
   
  You create a new revision with the git commit command, which takes the <br/>
files as they are in the staging area and stores that snapshot permanently to <br/>
your local repository.<br/>
  
  To see what you've changed but not yet staged, type git diff with no other <br/>
arguments.<br/>
  
  To see what you've staged that will go into your next commit, use git diff <br/>
--staged (or git diff --cached). This command compares what is in your <br/>
staging area to the content of your last commit.<br/>
  
  You can use git diff HEAD to compare what is in your working directory with the <br/>
last commit (or arbitrary commit with git diff <commit>). <br/>
  
# Unified Git diff format<br/>
  
diff --git a/builtin-http-fetch.c b/http-fetch.c<br/>
The first line is a git diff header in the form diff --git a/file1 b/file2.<br/>
--git option means that diff is in the git diff output format.<br/>
  
similarity index 95%<br/>
rename from builtin-http-fetch.c<br/>
rename to http-fetch.c<br/>
The first three lines in this example tell us that the file was renamed from <br/>
builtin-http-fetch.c to http-fetch.c and that these two files are 95% identical.<br/>
index f3e63d7..e8f44ba 100644<br/>
The last line in extended diff header tells us about the mode of given file<br/>
(100644 means that it is an ordinary file and not a symbolic link, and that it doesn't have executable permission bit)<br/>
Search on google 777,755,644 :P :)) <br/>
Some file permission examples: <br/>
777 - all can read/write/execute (full access). <br/>
755 - owner can read/write/execute, group/others can read/execute. <br/>
644 - owner can read/write, group/others can read only.<br/>
For the new files, pre-image(the version of the file before the given change) hash is 0000000, <br/>
the same for the deleted files with post-image(the version of the file after the change) hash.  <br/>
4-bit object type valid values in binary are 1000 (regular file), 1010 (symbolic link) and 1110 (gitlink) <br/>

@@ -1,8 +1,9 @@<br/>
This line is in the format @@ from-file-range to-file-range @@. <br/>
The from-file-range is in the form -<start line>,<number of lines>, <br/>
and to-file-range is +<start line>,<number of lines>.   <br/>
  
Next is the description of where and how files differ. The lines common <br/>
to both the files begin with a space (" ") indicator character. The lines that <br/>
actually differ between the two files have one of the following indicator <br/>
characters in the left print column:<br/>
+: A line was added here to the second file<br/>
-: A line was removed here from the first file<br/>
 
 
# Amending a commit
 the --amend flag of the git commit; it allows you to change the very last commit.<br/>
 If you just want to correct the commit message, you simply commit again, without any staged changes, and fix it:<br/>
 git commit --amend<br/>
 If you want to add some more changes to that last commit, you can simply stage <br/>
them as normal with git add and then commit again, or make the changes and use git commit -a --amend<br/>
 
WARNING: you should never amend a commit that has already been published!<br/>
This is because amend effectively produces a completely <br/>
new commit object that replaces the old one. If you're the <br/>
only person who had this commit, doing this is safe. After publishing the <br/>
original commit to a remote repository, other people might already have based their <br/>
new work on that version of the commit. Replacing the original with an amended <br/>
version will cause problems downstream.<br/>
 
 The old version of commit before amending would be available in the branch reflog and in <br/>
the HEAD reflog; Just after amend, it would be available as @{1}. <br/>
Git would keep the old version for a month, by default, unless manually removed.<br/>

# Anonymous branches
 What happens if you try to check out something that is not a local branch: for <br/>
example an arbitrary revision (like HEAD^), or a tag (like v0.9), or a remote-tracking <br/>
branch (for example, origin/master)?<br/>
 Older Git refused to switch to non-branch. Nowadays, Git will create an anonymous <br/>
branch by detaching HEAD pointer and making it refer directly to a commit, rather <br/>
than being a symbolic reference to a branch.<br/>
 To create an anonymous branch at the current position explicitly, you can use the --detach <br/>
option to the checkout command. The detached HEAD state is shown in branch <br/>
listing as (no branch) in older versions of Git, or (detached from HEAD) or (HEAD detached at ...) in newer.<br/>
 If you did detach HEAD by mistake, you can always go back to the previous branch with:<br/>
git checkout (name)<br/>
As Git informs you when creating a detached branch, you can always give a name to <br/>
the anonymous branch with git checkout -b <new-name>. <br/>
 
# Branch operations
Reset always changes where the current branch points to (moves the ref), <br/>
while checkout either switches branch, or detaches HEAD at a given revision if it is given non-branch.<br/>
 
 Delete a branch:You can do this with git branch -d.<br/>
What happens if you delete a branch, and there is no other reference to the part of <br/>
project history it pointed to? Those revisions will become unreachable and Git would <br/>
delete them after the HEAD reflog expires (which, with default configuration, is after 30 days).<br/>
 That is why Git would allow you to delete only the completely merged-in branch, <br/>
whose all commits are reachable from HEAD.<br/>
 To delete a branch that was not merged in, risking parts of the DAG becoming <br/>
unreachable, you need a stronger command, namely, git branch -D.<br/>
 You can check if the branch was merged in into any other branch, by checking <br/>
whether git branch --contains <branch> shows anything.  <br/>
You cannot delete the current branch.<br/>
 
 You can rename a branch with git branch -m (use -M if target name exists and <br/>
you want to overwrite it); it will rename a branch and move the corresponding <br/>
reflog (and add rename operation to the reflog), and change the branch in all of its <br/>
configuration (its description, its upstream, and so on).<br/>

 
 # Using git stash
 git stash command<br/>
 Stashing takes the dirty state of your working area—that is, your modified <br/>
tracked files in your worktree (though you can also stash untracked files with the <br/>
--include-untracked option), and the state of the staging area, then saves this <br/>
state, and resets both the working directory and the index to the last committed <br/>
version (to match the HEAD commit), effectively running git reset --hard HEAD. <br/>
You can then reapply the stashed changes at any time.<br/>
Stashes are saved on a stack: by default you apply the last stashed changes (stash@{0}),<br/>
though you can list stashed changes (with git stash list), and explicitly select any of the stashes.<br/>
 By default git stash pop will apply the last stashed changes, and delete the  <br/>
stash if applied successfully.<br/>
 You can use any of the older stashes by specifying the stash name as an argument. <br/>
For example, you can run git stash apply stash@{1} to apply it, and you can <br/>
drop it (remove it from the list of stashes) with git stash drop stash@{1}; the  <br/>
git stash pop command is just a shortcut for apply + drop.<br/>
 You can make git stash keep the state of the index, and reset the <br/>
working area to the staged state, with the --keep-index option.<br/>
 To stash away your changes, Git creates two automatic commits: one for the index <br/>
(staging area), and one for the working directory. With git stash --include-untracked,<br/>
 Git creates an additional third automatic commit for untracked files.<br/>
 The commit containing the work in progress in the working directory (the state of <br/>
files tracked from there) is the stash, and has the commit with the contents of the <br/>
staging area as its second parent. This commit is stored in a special ref: refs/stash. <br/>
Both WIP (stash) and index commits have the revision you were on when saving <br/>
changes as its first (and only for the index commit) parent.<br/>
 
 
 # Bare repositories
There are two types of repositories: an ordinary non-bare one, with a working directory and a staging area, <br/>
and a bare repository, bereft of the working directory. The former type is meant for private solo development, <br/>
for creating new history, while the latter type is intended for collaboration and synchronizing development results.<br/>
By convention, bare repositories use the .git extension—for example, project.git<br/>
 —while non-bare repositories don't have it—for example, project (with the administrative area and the local repository in project/.git). <br/>
 You can usually omit this extension when cloning, pushing to, or fetching from the repository; <br/>
 using either http://git.example.com/project.git or http://git.example.com/project as the repository URL will work. <br/>
 To create the bare repository, you need to add the --bare option to the init or the clone command:<br/>
 git init --bare project.git<br/>

 # Tags
 Git uses two types of tags: lightweight and annotated. A lightweight tag is very much like a branch that doesn't change – <br/>
 it's just a pointer (reference) to a specific commit in the graph of revisions,<br/>
 though in refs/tags/ namespace rather than in refs/heads/ one.<br/>
 
 Annotated tags<br/>
Annotated tags, involve tag objects. Here the tag reference (in refs/tags/) points to a tag object, which in turn points to a commit. <br/>
 Tag objects contain a creation date, the tagger identity (name and e-mail), and a tagging message. <br/>
You create an annotated tag with git tag -a (or --annotate). If you don't specify a message for an annotated tag on <br/>
 the command line (for example, with -m "<message>"), Git will launch your editor so you can enter it.<br/>
You can view the tag data along with the tagged commit with the git show command<br/>
 
 Signed tags<br/>
Signed tags are annotated tags with a clear text GnuPG signature of the tag data attached. <br/>
 You can create it with git tag -s (which uses your committer identity to select the signing key, or user.signingKey if set),<br/>
 or with git tag -u <key-id>; <br/>
both versions assume that you have a private GPG key (created, for example, with gpg --gen-key).<br/>
 Annotated or signed tags are meant for marking a release, while lightweight tags are meant for private or temporary <br/>
revision labels. For this reason, some Git commands (such as git describe) will ignore lightweight tags by default.<br/>
 Of course in collaborative workflows it is important that the signed tag is made public, and that there is a way to verify it.<br/>
 
 Publishing tags<br/>
Git does not push tags by default: you need to do it explicitly. <br/>
 One solution is to individually push a tag with git push <remote> tag <tag-name> <br/>
 (here tag <tag> is equivalent to the longer refspec refs/tags/<tag>:refs/tags/<tag>); <br/>
you can skip tag in most cases, here. <br/>
 Another solution is to push tags in mass either all the tags—both lightweight and <br/>
 annotated—with the use of the --tags option, or just all annotated tags that point to pushed commits with --follow-tags.<br/>
 This explicitness allows you to re-tag (using git tag -f) with impunity, <br/>
 if it turns out that you tagged the wrong commit, or there is a need for a last-minute <br/>
 fix—but only if the tag was not made public.<br/>
When fetching changes, Git automatically follows tags, downloading annotated <br/>
tags that point to fetched commits. This means that downstream developers will <br/>
automatically get signed tags, and will be able to verify releases.<br/>
 To verify a signed tag, you use git tag -v <tag-name>. You need the signer's <br/>
public GPG key in your keyring for this (imported using for example gpg --import <br/>
or gpg --keyserver <key-server> --recv-key <key-id>), and of course the <br/>
tagger's key needs to be vetted in your chain of trust.<br/>
 
 Merging signed tags (merge tags)<br/>
 Requesting the pull of a signed tag (available since Git version 1.7.9).<br/>
 In this workflow, you work on changes and, when they are ready, you create and <br/>
push a signed tag (tagging the last commit in the series). You don't have to push <br/>
your working branch—pushing the tag is enough. If the workflow involves sending <br/>
a pull request to the integrator, you create it using a tag as the end commit<br/>
 The signed tag being pulled is not stored in the integrator's repository, not as a <br/>
tag object. Its content is stored, hidden, in a merge commit. This is done so as to <br/>
not pollute the tag namespace with a large number of such working tags.<br/>

 # The graduation, or progressive-stability branches workflow <br/>
 In such situation, one would have at least three integration branches. There would <br/>
be one branch for the ongoing maintenance work (containing only bug fixes to the <br/>
last version), to create minor releases. One branch for stable work to create major <br/>
releases; this branch can also be used for nightly stable builds. And last, one branch <br/>
for ongoing development, possibly unstable.<br/>
 You can use this workflow as it is, with only graduation branches, and no other types <br/>
of branches. You commit bug fixes on the maintenance branch and merge it into <br/>
the stable branch and development branch, if necessary. You create revisions with <br/>
the well-tested work on the stable branch, merging it into the development branch <br/>
when needed (for example, if the new work depends on them). You put the work in <br/>
progress, possibly unstable, on the development branch. During normal development, <br/>
you never merge less stable into more stable branches, otherwise you would decrease <br/>
their stability. It is always more stable into less stable.<br/>
 In the pure graduation branches workflow, one would create minor releases (with bug fixes) <br/>
 out of the maintenance branch. Major releases (with new features) are <br/>
created out of the stable-work branch. After a major release, the stable-work branch <br/>
is merged into the maintenance branch to begin supporting the new release that was <br/>
just created. At this point also, an unstable (development) branch can be merged into <br/>
a stable one. This is the only time when merging upstream, which means merging <br/>
less stable branches into more stable branches, should be done.<br/>
 
 # The topic branches workflow<br/>
 The idea behind the topic branches workflow is to create a separate short-lived <br/>
branch for each topic, so that all the commits belonging to a given topic <br/>
 (all the steps in its development) are kept together. The purpose of each topic branch is  <br/>
a development of the new feature, or a creation of a bug fix.<br/>
 In the topic branches workflow (also called the feature branches workflow), you <br/>
have are at least two different types of branches. First, there needs to be at least one <br/>
permanent (or just long-lived) integration branch. This type of branches is used purely <br/>
for merging. Integration branches are public.<br/>
   Second, there are separate short-lived temporary feature branches, each intended for <br/>
the development of a topic or the creation of a bug fix. They are used to carry all the <br/>
steps, and only the steps required in the development of a feature or a fix; a unit  <br/>
of work for a developer. These branches can be deleted after the feature or the  <br/>
bug fix is merged. Topic branches are usually private and are often not present in <br/>
public repositories.<br/>
 
 # Fetching tags and automatic tag following<br/>
The situation with tags is a bit different. While we would want to make it possible <br/>
for different developers to work independently on the same branch <br/>
(for example, an integration branch such as master), though in different repositories, <br/>
we would need all developers to have one specific tag to always refer to the same specific <br/>
revision. That's why the position of branches in remote repositories is stored using <br/>
a separate per-remote namespace refs/remotes/<remote name>/* in remote-tracking branches,<br/>
but tags are mirrored—each tag is stored with the same name, in refs/tags/* namespace.<br/>
  This is also why, by default, while downloading changes, Git would also fetch and <br/>
store locally all the tags that point to the downloaded objects. You can disable this <br/>
automatic tag following with the --no-tags option. This option can be set on the <br/>
command line as a parameter, or it can be configured with the remote.<remote name>.tagopt setting.<br/>
You can also make Git download all the tags with the --tags option, or by adding the appropriate<br/>
fetch refspec value for tags:<br/>
fetch = +refs/tags/*:refs/tags/*<br/>
  
 # Pushing branches and tags<br/>
Pushing branches are (usually) governed by the selected push mode. <br/>
  You push a local branch (usually just a single current branch) to update a <br/>
specific branch in the remote repository, from refs/heads/ locally to refs/heads/ <br/>
in remote. It is usually a branch with the same name, but it might be a differently <br/>
named branch configured as upstream—details will be provided later. You don't <br/>
need to specify the full refspec: using the ref name (for example, name of a branch) <br/>
means pushing to the ref with the same name in the remote repository, creating it if it <br/>
does not exist. Pushing HEAD means pushing the current branch into the branch with <br/>
the same name (not to the HEAD in remote—it usually does not exist).<br/>
Usually, you push tags explicitly with git push <remote repository> <tag><br/> 
(ortag <tag> if by accident there is both a tag and branch with the same name—both <br/>
mean the +refs/tags/<tag>:refs/tags/<tag> refspec). You can push all the tags <br/>
with --tags (and with appropriate refspec), and turn on the automatic tag following <br/>
with --follow-tags (it is not turned on by default as it is for fetch).<br/>
As a special case of refspec, pushing an "empty" source into some ref in remote <br/>
deletes it. The --delete option to git push is just a shortcut for using this type <br/>
of refspec. For example, to delete a ref matching experimental in the remote <br/>
repository, you can run:<br/>
git push origin :experimental  <br/>
The remote server might forbid the deletion of refs with receive.denyDeletes or hooks.<br/>
  
 # Push modes and their use<br/>
The behavior of git push, in the absence of the parameters specifying what to push, <br/>
and in the absence of the configured push refspec, is specified by the push mode. <br/>
  
  The simple push mode – the default<br/>
The default push mode in Git 2.0 and later is the so-called simple mode.<br/>
  With this mode, you always push the current local branch into the same named <br/>
branch in the remote repository. If you push into the same repository you fetch from <br/>
(the centralized workflow), it requires the upstream to be set for the current branch. <br/>
The upstream is named the same as the branch.<br/>
  This is the safest option; it is well-suited for beginners, which is why it is the default <br/>
mode. You can turn it on explicitly with git config push.default simple.<br/>
  
  The matching push mode for maintainers<br/>
  Before version 2.0 of Git, the default push mode was matching. This mode is most <br/>
useful for the maintainer (also known as the integration manager) in a blessed <br/>
repository workflow.<br/>
  With the matching mode, Git will push all the local branches that have their <br/>
equivalent with the same name in the remote repository. This means that only the <br/>
branches that are already published will be pushed to the remote repository. To <br/>
make a new branch public you need to push it explicitly the first time, for example:<br/>
git push origin maint-1.4<br/>
  To turn on the matching mode globally, you can run:<br/>
git config push.default matching<br/>
If you want to turn it on for a specific repository, you need to use a special refspec <br/>
composed of a sole colon. Assuming that the said repository is named origin and <br/>
that we want a not forced push, it can be done with:<br/>
git config remote.origin push :<br/>
You can,push matching branches using this refspec on the command line:<br/>
git push origin :<br/>
  
  The upstream push mode for the centralized workflow<br/>
  That is what the upstream push mode was created for:<br/>
git config push.default upstream<br/>
This mode makes Git push the current branch to the specific branch in the remote <br/>
repository—the branch whose changes are usually integrated into the current <br/>
branch. This branch in the remote repository is the upstream branch<br/>
(and can be referenced as @{upstream}). Turning this mode on makes it possible to simplify the <br/>
last command in both examples to the following:<br/>
git push<br/>
The information about the upstream is created either automatically <br/>
(while forking off the remote-tracking branch), or explicitly with the --track option. It is stored <br/>
in the configuration file and it can be edited with ordinary configuration tools. <br/>
Alternatively, it can be changed later with the following:<br/>
git branch --set-upstream-to=<branchname><br/>
  
  The current push mode for the blessed repository workflow<br/>
  In the blessed repository workflow, each developer has his or her own private and <br/>
public repository. In this model, one fetches from the blessed repository and pushes <br/>
to his or her own public repository.<br/>
In this workflow, you start working on a feature by creating a new topic branch for it:<br/>
git checkout -b fix-tty-bug origin/master<br/>
When the features are ready, you push it into your public repository, perhaps <br/>
rebasing it first to make it easier for the maintainer to merge it:<br/>
git push origin fix-tty-bug<br/>
  To configure Git so when on fix-tty-bug branch it is enough to just run git push, <br/>
you need to set up Git to use the current push mode, which can be done with the following:<br/>
git config push.default current<br/>
This mode will push the current branch to the branch with the same name at the receiving end.<br/>
  
 # Merging Changes Together<br/>
  <br/>
  Merging branches<br/>
The merge operation joins two (or more) separate branches together, including all the changes since<br/>
the point of divergence into the current branch. You do this with the git merge command:<br/>
git checkout master<br/>
git merge bugfix123<br/>
We first switched to a branch we want to merge into (master in this example), <br/>
and then provided the branch to be merged (here, bugfix123).<br/>
  
  1.No divergence – fast-forward and up-to-date cases<br/>
Git would, by default, simply move the branch pointer of the current branch forward.<br/>
We can force creating a merge commit even in such cases with the git merge --no-ff command.<br/>
The default is --ff; to fail instead of creating a merge commit you can use --ff-only (ensuring fast-forward only).<br/>
  <br/>
  2.Creating a merge commit<br/>
  Because the top commit on the branch you are on (and are merging into) is not a <br/>
direct ancestor or a direct descendant of the branch you are merging in, Git has to <br/>
do more work than just moving the branch pointer. In this case, Git does a merge of <br/>
changes since the divergence, and stores it as a merge commit on the current branch. <br/>
This commit has two parents denoting that it was created based on more than one <br/>
commit (more than one branch): the first parent is the previous tip of the current <br/>
branch and the second parent is the tip of branch you are merging in.<br/>
  You can either ask Git to not autocommit a merge with git merge --no-commit <br/>
to examine it first, or you can examine the merge commit and then use the <br/>
git commit --amend command if it is incorrect.<br/>
  <br/>
Cherry-pick – creating a copy of a changeset  <br/>
  You can create a copy of a commit (or a series of commits) with the cherry-pick <br/>
command. Given a series of commits (usually, just a single commit), it applies the <br/>
changes each one introduces, recording a new commit for each.<br/>
  By default, Git does not save information about where the cherry-picked <br/>
commit came from. You can append this information to an original commit message, <br/>
as a (cherry-picked from the commit <sha-1>) line with git cherry-pick -x <commit>. <br/>
This is only done for cherry-picks without conflicts. <br/>
  
  Revert – undoing an effect of a commit<br/>
  This "undoing of a commit" can be done by creating a commit with a reversal of changes, <br/>
something like cherry-pick but applying the reverse of changes. This is done with the revert command.<br/>
  If you want to revert all the changes made to the whole working area, <br/>
you can use git reset (in particular, the --hard option).<br/>
  If you want to revert changes made to a single file, use git checkout <file>.<br/>
  The git revert command records a new commit to reverse the effect of the earlier commit (often, a faulty one).<br/>
  <br/>
  What happens if you want to cherry-pick or revert a merge commit? <br/>
  Such commits have more than one parent, thus they have more than one change associated with them.<br/>
  You have to tell Git which change you want to pick up (in the case of cherry-pick), <br/>
 or back out (in the case of revert) with the -m <parent number> option.<br/>
<br/>
  Rebasing a branch<br/>
  Besides merging, Git supports additional way to integrate changes from one branch <br/>
into another: namely the rebase operation.<br/>
Like a merge, it deals with the changes since the point of divergence (at least, by default). <br/>
  But while a merge creates a new commit by joining two branches, rebase <br/>
takes the new commits from one branch (takes the commits since the divergence) <br/>
and reapplies them on top of the other branch.<br/>
  With merge, you first switched to the branch to be merged and then used the merge <br/>
command to select a branch to merge in. With rebase, it is a bit different. First you <br/>
select a branch to rebase (changes to reapply) and then use the rebase command to select where to put it.<br/>
git checkout i18n<br/>
git rebase master<br/>
  Or, you can use git rebase master i18n as a shortcut. The rebase operation takes the master..i18n range of revisions, <br/>
replays it on top of master, and finally points i18n to the replayed commits.<br/>
  Old versions of commits doesn't vanish, at least not immediately. They would be accessible via reflog (and ORIG_HEAD) for a period.<br/>
  
  Advanced rebasing techniques<br/>
You can also have your rebase operation replay on something other than the target branch of the rebase with --onto <newbase>, <br/>
separating selected range of revisions to replay from the new base to replay onto.<br/>
 Or perhaps, you want to rebase only a part of the branch. You can do this with git rebase --interactive, <br/>
 but you can also use git rebase --onto <new base> <starting point> <branch>.<br/>
  You can even choose to rebase the whole branch (usually, an orphan branch) with the --root option. <br/>
  In this case, you would replay the whole branch and not just a selected subset of it.<br/>
  <br/>
  The three-way merge<br/>
  Git uses the three-way merge algorithm to come up with the result of the merge, <br/>
comparing the common ancestors (base), side merged in (theirs), and side merged into (ours).<br/>
  <br/>
  
| ancestor (base)  | HEAD (ours) | branch (theirs)  | result |  
| ------------- | ------------- | ------------- | ------------- | 
| A  | A  | A  | A  |
| A  | A  | B  | B  |
| A  | B  | A  | B  |
| A  | B  | B  | B  |
| A  | B  | C  | merge conflict  |
  <br/>
  The rules for the trivial tree-level three-way merges are:<br/>
• If only one side changes a file, take the changed version<br/>
• If both the sides have the same changes, take the changed version<br/>
• If one side has a different change from the other, there is merge conflict at the contents level<br/>
  <br/>
  Conflict markers<br/>
<br/>  <<<<<<< HEAD:src/rand.c<br/>
<br/>fprintf(stderr, "Usage: %s <number> [<count>]\n", argv[0]);<br/>
<br/>=======<br/>
<br/>fprintf(stderr, _("Usage: %s <number> [<count>\n"), argv[0]);<br/>
<br/>>>>>>>> i18n:src/rand.c<br/>
  This means that the ours version on the current branch (HEAD) in the src/rand.c file <br/>
is there at the top of this block between the <<<<<<< and ======= markers, while the <br/>
theirs version on the i18n branch being merged (also from src/rand.c) is there at <br/>
the bottom part between the ======= and >>>>>>> markers.<br/>
  You need to replace this whole block by the resolution of the merge.<br/>
  <br/>
  Three stages in the index<br/>
  It turns out that it is another use for the staging area of the commit (a merge commit in this case), <br/>
which is also known as the index. In the case of conflicts, Git stores all of conflicted files versions <br/>
in the index under stages; each stage has a number associated with it. <br/>
Stage 1 is the common ancestor (base), stage 2 is the merged into version from HEAD, that is, the current branch (ours), <br/>
and stage 3 is from MERGE_HEAD, the version you're merging in (theirs).<br/>
You can see these stages for the unmerged files with the low level (plumbing) <br/>
command git ls-files --unmerged (or for all the files with git ls-files --stage).<br/>
  You can refer to each version with the :<stage number>:<pathname> specifier. If you want to view a common ancestor version of src/rand.c,<br/>
 you can use the following:<br/>
git show :1:src/rand.c<br/>
If there is no conflict, the file is in stage 0 of the index.<br/>

 # An interactive rebase<br/>
 Sometimes, you might want to edit commit deeper in history, or reorganize commits <br/>
into a logical sequence of steps. One of the built-in tools that you can use in Git for <br/>
this purpose is git rebase --interactive.<br/>
   Commands:<br/>
  p, pick = use commit<br/>
  r, reword = use commit, but edit the commit message<br/>
  e, edit = use commit, but stop for amending<br/>
  s, squash = use commit, but meld into previous commit<br/>
  f, fixup = like "squash", but discard this commit's log message<br/>
  x, exec = run command (the rest of the line) using shell<br/>
  d, drop = remove commit<br/>
  You can, make the interactive rebase test each commit with the --exec option, for example:<br/>
git rebase --interactive --exec "make test"<br/>
  
 # Scripted rewrite with the git filter-branch<br/>
In some cases, you might need to use more powerful tools than the interactive rebase <br/>
to rewrite and clean up the history. You might want something that would rewrite <br/>
the full history, and would do the rewrite noninteractively, given some specified <br/>
algorithm to do the rewrite. Such situations are the task for git filter-branch.<br/>
  First, you need to give it a branch or a set of branches to rewrite, for example, <br/>
--all to rewrite all the branches.<br/>
  If you specify no filters, the commits will be recommitted without any changes.<br/>
  This means that running git filter-branch without any filter can be used to make <br/>
permanent the effects of grafts or replacements by rewriting the selected commits. <br/>
  The git filter-branch command supports the following types of filters:<br/>
 --env-filter: This may be used to modify environments in which a commit is performed. <br/>
 --tree-filter: This may be used to rewrite the contents of the commit,that is, the tree object the commit refers to. <br/>
 --index-filter: This may be used to rewrite the index and the staging area from which the rewritten commit will be created. <br/>
 --parent-filter: This may be used to rewrite the commit's parent list. <br/>
 --msg-filter: This may be used to rewrite the commit messages. <br/>
 --commit-filter: This may be used to specify the command to be called instead of git commit-tree. <br/>
 --tag-name-filter: This may be used to rewrite tag names.<br/>
  
 # Reverting a commit<br/>
  If you need to back-out an existing commit, undoing the changes it brought, you <br/>
can use git revert.The revert operation creates a commit with reverse of changes. For example,<br/>
where original commit adds a line, reversion removes it, where original commit removes a line, reversion adds it.<br/>
  
# Reverting a faulty merge<br/>
  Sometimes, you might need to undo an effect of a merge. Suppose that you have <br/>
merged changes, but it turned out that they were merged prematurely, and that the merge brings regressions.<br/>
  If you didn't publish this merge commit before you noticed the mistake and the <br/>
unwanted merge exists only in your local repository, the easiest solution is to drop this commit with<br/>
git reset --hard HEAD^<br/>
  What do you do if you realize only later that the merge was incorrect, for example, <br/>
after one more commit was created on the master branch and published? One possibility is to revert the merge.<br/>
  To run revert on a merge commit, you need <br/>
to specify which patch you are reverting or, in other words, which parent is the mainline.<br/>
  git revert -m 1 HEAD^^<br/>
  
# Storing additional information with notes<br/>
  The notes mechanism is a way to store additional information for an object, usually a commit, <br/>
without touching the objects themselves.<br/>
  Each note belongs to some category of notes, so that notes used for different purposes can be kept separate.<br/>
  git notes add -m 'message' v0.2~3<br/>
  In Git, notes are stored using extra references in the refs/notes/ namespace.<br/>
  Notes can also be used to handle marking bugs and bug fixes, and verifying fixes. <br/>
You often find bugs in commits long after they got published, that's why you need <br/>
notes for this; if you find a bug before publishing, you would rewrite the commit instead.<br/>
  
# Subtrees versus submodules <br/>
  In general, subtrees are easier to use and less tricky. Many people go with <br/>
submodules, because of the better built-in tooling (they have their own Git <br/>
command, namely git submodule), detailed documentation, and similarity to the <br/><br/>
Subversion externals, making them feel falsely familiar. Adding a submodule is <br/>
very simple (just run git submodule add), especially compared to adding a subtree <br/>
without the help of third-party tools such as git subtree or git stree.<br/>
  The major difference between subtrees and submodules is that, with subtrees, <br/>
there's only one repository, which means just one lifecycle. Submodules and similar <br/>
solutions use nested repositories, each with its own lifeline.<br/>
Though submodules are easy to set up and fairly flexible, they are also fraught with <br/>
peril, and you need to practice vigilance while working with them. The fact that <br/>
the submodules are opt-in also means that the changes touching the submodules <br/>
demand a manual update by every collaborator. Subtrees are always there, so getting <br/>
the superproject's changes mean getting the subproject's too.<br/>
  Commands such as status, diff, and log display precious little information about <br/>
submodules, unless properly configured to cross the repository boundary; it is easy <br/>
to miss a change. With subtrees, status works normally, while diff and log need <br/>
some care, because the subproject commits have a different root directory. The latter <br/>
assumes that you did not decide to not include the subproject history (by squashing <br/>
subtree merges). Then, the problem is only with the remote-tracking branches in subproject's repository, if any.<br/>
Because the lifecycles of different repositories are separate, updating a submodule <br/>
inside its containing project requires two commits and two pushes. Updating a <br/>
subtree-merged subproject is very simple: only one commit and one push. On <br/>
the other hand, publishing the subproject changes upstream is much easier with 
submodules, while it requires changeset extraction with subtrees (here tools such as git subtree help a lot).<br/>
  The next major issue, and a source of problems, is that the submodule has two <br/>
sources of the current revision: the gitlink in the superproject and the branches in the 
submodule's clone of the repository. This means that git remote update works a <br/>
bit like a sideways push into a nonbare repository. <br/>
  Submodule heads are therefore generally detached, so any local update <br/>
requires various preparatory actions to avoid creating a lost commit. There is <br/>
no such issue with subtrees. All the revision changing commands work as usual <br/>
with subtrees, bringing the subproject directory to the correct version without the <br/>
requirement of any additional action. Getting changes from the subproject repository <br/>
is just a subtree merge away. The only difference between ordinary pull is the -s subtree option.<br/>
  Still, sometimes submodules are the right choice. Compared to subtrees, they allow <br/>
for a subproject (a module) to be not fetched, which is helpful when your code base is <br/>
massive. Submodules are also useful when the heavy modularization is not natively <br/>
handled, or not well natively handled, by the development stack's ecosystem.<br/>
Submodules might also themselves be superprojects for other submodules, creating <br/>
a hierarchy of subprojects. Using nested submodules is made easier thanks to git <br/>
submodule status, update, foreach, and sync subcommands all supporting the --recursive switch.<br/>
  
 # Using shallow clones to get truncated history<br/>
  This operation allows you to get a local copy of the repository with <br/>
the history truncated to a particular specified depth, that is, the number of latest revisions.<br/>
  How do you do it? Just use the --depth option:<br/>
git clone --depth=1 https://git.company.com/project<br/>
  The preceding command clones only the most recent revision of the primary branch. <br/>
  Since version 1.9, Git supports pull and push operations even with shallow clones, <br/>
though some care is still required. You can change the depth of a shallow clone by <br/>
providing the --depth=<n> option to git fetch (note however that tags for the <br/>
deepened commits are not fetched). To turn a shallow repository into a complete one, use --unshallow.<br/>
  Note, also git clone --depth=1 may still get all the branches and all the tags. <br/>
This can happen if the remote repository doesn't have HEAD, thus it doesn't have a <br/>
primary branch selected; otherwise only the tip of the said single branch is fetched. <br/>
Long-lived projects usually had many releases during their long history. To really <br/>
save time, you would need then to combine shallow clone with the next solution: branch limiting.<br/>
  # Cloning only a single branch<br/>
  Git, by default, clones all the branches and tags (if you want to fetch notes or <br/>
replacements, you need to specify them explicitly). You can limit the amount of the <br/>
history you clone by specifying that you want to clone only a single branch:<br/>
  git clone --branch master --single-branch \ https://git.company.com/project<br/>
  This feature might be quite useful if you don't want detached orphan branches or <br/>
the opposite: you want only an orphan branch (for example, with a web page for a project). <br/>
  It also works well used together with a shallow clone.<br/>
  
# Customize Git<br/>
  Command-line completion for Git<br/>
  Git comes with built-in (but not always installed) support for the auto-completion of <br/>
Git commands for the bash and zsh shells.<br/>
  Once the completion for Git is enabled, to test it you can type for example:<br/>
git check<TAB><br/>
  With Git completion enabled bash (or zsh) would autocomplete this to git checkout.<br/>
  Similarly, in an ambiguous case, double Tab shows all the possible completions <br/>
(though it is not true for all the shells):<br/>
git che<TAB><TAB><br/>
checkout      cherry        cherry-pick<br/>
  The completion feature also works with options; this is quite useful if you don't <br/>
remember the exact option but only the prefix.<br/>
  
  Autocorrection for Git commands<br/>
  By default, if you type something that looks like a mistyped command, Git helpfully <br/>
tries to figure out what you meant.<br/>
  However, with the help.autoCorrect configuration variable set to a positive <br/>
number, Git will automatically correct and execute the mistyped commands after <br/>
waiting for the given number of deciseconds (0.1 of second). You can use a negative <br/>
value of this option for immediate execution, or zero to go back to default:<br/>
git chekout<br/>
  WARNING: You called a Git command named 'chekout', which does not exist.<br/>
Continuing under the assumption that you meant 'checkout'<br/>
in 0.1 seconds automatically...<br/>
Your branch is up-to-date with 'origin/master'.<br/>
  If there is more than one command that can be deduced from the entered text, <br/>
nothing will be executed. This mechanism works only for Git commands; you cannot <br/>
autocorrect subcommands, parameters, and options (as opposed to tab completion).<br/>
  <br/>
  
 # Automating Git with hooks<br/>
  Like many programming tools, Git includes a way to fire custom functionality <br/>
contained in the user-provided code (custom scripts), when certain important pre-defined <br/>
actions occur, that is, when certain events trigger. Such a functionality <br/>
invoked as a event handler is called a hook. It allows to take an additional action <br/>
and, at least for some hooks, also to stop the triggered functionality.<br/>
Hooks in Git can be divided into the client-side and the server-side hooks.<br/>
  Client-side hooks are triggered by local operations (on client) such as committing, applying <br/>
a patch series, rebasing, and merging. <br/>
  Server-side hooks on the other hand run on the server when the network operations such as receiving pushed commits occur.<br/>
You can also divide hooks into pre hooks and post-hooks. <br/>
  Pre hooks are called before an operation is finished, usually before the next step while performing <br/>
an operation. If they exit with a nonzero value, they will cancel the current Git operation.<br/>
  Post hooks are invoked after an operation finishes and can be used for notification and logs; they cannot cancel an operation.<br/>
  The hooks in Git are executable programs (usually scripts), which are stored in the hooks/ subdirectory <br/>
  of the Git repository administrative area, that is in .git/hooks/ <br/>
for non-bare repositories. Hook programs are named each after an event that triggers <br/>
it; this means that if you want for one event to trigger more than one script, you will need to implement.<br/>
  
 # Command aliases for Git<br/>
  It is very easy in theory to create an <br/>
alias. You simply need to create an alias.<command-name> configuration variable; <br/>
its value is the expansion of alias.<br/>
  One of the uses for aliases is defining short abbreviations for commonly used <br/>
commands and their arguments. Another is creating new commands. Here are a <br/>
couple of examples you might want to set up:<br/>
 git config --global alias.co checkout<br/>
 git config --global alias.ci commit<br/>
 git config --global alias.lg log --graph --oneline --decorate<br/>
  The preceding setup means that typing, for example, git ci would be the same as <br/>
typing git commit. Aliases take arguments just as the regular Git commands do. <br/>
Git does not provide any default aliases that are defining shortcuts for the common <br/>
operations.Arguments are split by space, the usual shell quoting and escaping is supported; in <br/>
particular, you can use a quote pair ("a b") or a backslash (a\ b) to include space in a single argument.<br/>
  You cannot have the alias with the same name as a Git command;<br/>
  You cannot use aliases to change the behavior of commands.<br/>
  The reasoning behind this restriction is that it could make existing scripts and hooks fail unexpectedly.<br/>
  Aliases that hide existing Git commands (with the same name as Git commands) are simply ignored.<br/>
  
  # Git Administration<br/>
  You can run auto gc manually with git gc --auto, or force garbage collection <br/>
with git gc. The git count-objects command (perhaps with the help of the -v parameter) <br/>
can be used to check whether there are signs that repack is needed. <br/>
You can even run individual steps of the garbage collection individually with <br/>
git repack, git pack-refs, git prune, and git prune-packed.<br/>
  By default, Git would try to reuse the results of the earlier packing to reduce CPU <br/>
time spent on the repacking, while still providing good disk space utilization. In <br/>
some cases, you would want to more aggressively optimize the size of repository <br/>
at the cost of it taking more time: this is possible with git gc --aggressive (or <br/>
with repacking the repository by hand with git repack, run with appropriate <br/>
parameters). It is recommended to do this after import from other version control <br/>
systems; the mechanism that Git uses for importing (fast-import stream) is optimized <br/>
for the speed of the operation, not for the final repository size.<br/>
  There are issues of maintenance not covered by git gc, because of their nature. One <br/>
of them is pruning (deleting) remote-tracking branches that got deleted in the remote <br/>
repository. This can be done with git fetch --prune or git remote prune, or <br/>
on a per-branch basis with git branch --delete --remotes <remote-tracking branch>. 
This action is left to the user, and not run by git gc, because Git simply <br/>
cannot know whether you have based your own work on the remote-tracking branch that is to be pruned.<br/>
  Often, the simplest way to find and recover lost commits is to use the git reflog tool.<br/>
For each branch, and separately for HEAD, Git silently records (logs) where the <br/>
tip of the branch was in your local repository, at what time it was there, and how it <br/>
got there.This record is called the reflog. Each time you commit or rewind a branch, <br/>
the reflog for the branch and for the HEAD is updated. Each time you change the <br/>
branches, the HEAD reflog is updated, and so on.<br/>
  You can see where the tip of branch has been at any time by running git reflog or <br/>
git reflog <branch>. You can run git log -g instead, where -g is a short way <br/>
of saying --walk-reflog; this gives you a normal configurable log output. There is <br/>
also --grep-reflog=<pattern> to search the reflog.<br/>
  git reflog<br/>
  The main purpose of git fsck is to check for repository corruption. <br/>
  
  Server-side hooks<br/>
Hooks that are invoked on the server can be used for server administration; among <br/>
others, these hooks can control the access to the remote repository by performing <br/>
the authorization step, and can ensure that the commits entering the repository meet <br/>
certain minimal criteria.<br/>
  
  Reducing the size taken by repositories<br/>
  If you are hosting many forks (clones) of the same repository, you might want to <br/>
reduce disk usage by somehow sharing common objects. One solution is to use <br/>
alternates (for example, with git clone --reference) while creating a fork. In this <br/>
case, the derived repository would look to its parent object storage if the object is not <br/>
found on its own.<br/>
  There are, two problems with this approach. First is that you need to <br/>
ensure that the object the borrowing repository relies on does not vanish from the <br/>
repository set as the alternate object storage (the repository you borrow from). This <br/>
can be done, for example, by linking the borrowing repository refs in the repository <br/>
lending the objects, for example, in the refs/borrowed/ namespace. Second is that <br/>
the objects entering the borrowing repository are not automatically de-duplicated: <br/>
you need to run git repack -a -d -l, which internally passes the --local option to git pack-objects.<br/>
An alternate solution would be to keep every fork together in a single repository, <br/>
and use gitnamespaces to manage separate views into the DAG of revisions, one <br/>
for each fork. With plain Git, this solution means that the repository is addressed by <br/>
the URL of the common object storage and the namespace to select a particular fork.<br/> 
Usually, this is managed by a server configuration or by a repository management <br/>
tool; such mechanism translates the address of the repository into a common <br/>
repository and the namespace. The git-http-backend manpage includes an <br/>
example configuration to serve multiple repositories from different namespaces in <br/>
a single repository. Gitolite also has some support for namespaces in the form of <br/>
logical and backing repositories and option namespace.pattern, though not every <br/>
feature works for logical repositories.<br/>
Storing multiple repositories as the namespace of a single repository avoids storing <br/>
duplicated copies of the same objects. It automatically prevents duplication between <br/>
new objects without the need for ongoing maintenance, as opposed to the alternates <br/>
solution. On the other hand, the security is weaker; you need to treat anyone with <br/>
access to the single namespace, which is within the repository as if he or she had an <br/>
access to all the other namespaces, though this might not be a problem for your case.<br/>
  
  Solving the large nonresumable initial clone problem<br/>
  One solution is to create, with the git bundle command, a static file that can be <br/>
used for the initial clone, or as reference repository for the initial clone (the latter can <br/>
be done with the git clone --reference=<bundle> --dissociate command if <br/>
you have Git 2.3 or a newer looks unnecessary). This bundle file can be distributed <br/>
using any transport; in particular, one that can be resumed if interrupted, be it HTTP, <br/>
FTP, rsync, or BitTorrent. The conventions people use, besides explaining how to <br/>
get such a bundle in the developer documentation, is to use the same URL as for the <br/>
repository, but with the .bundle extension (instead of an empty extension or a .git suffix).<br/>
There are also more esoteric approaches like a step by step deepening of a shallow <br/>
clone (or perhaps, just using a shallow clone with git clone --depth is all that's <br/>
needed), or using approaches such as GitTorrent.<br/>
  
