# A Comprehensive Guide to Git, Github, and The Feature Branch Workflow

GitHub is a platform, enabling the use of so-called remote repositories, in git.
The version control system (VCS) git is one of many, but one of the most widely used.
This is great, because of the absolute immense community, a lot of info is available. 
I will put git-specific terms in italics, so if something is unclear in this doc **google** it!

**There will be no examples on how to exactly work with what git interface!**
There are many different varieties of git, ranging from a simple command line to fully-fledged desktop apps.
This means that how exactly you clone a repository, commit your code, delete a branch, etc. will differ greatly depending on the specific git application you use.
Mostly I will go into how git works locally, and then tell you about collaborating in Github specifically.
If the term command-line does not immediately make your eyes twinkle with joy, I recommend using _Github Desktop_ for managing your code in Windows/MACOS.

## Git

All code of an application is stored in a _repository_. This is simply a folder git, together with some config files.
These config files are what define this folder as a repository and hold all the different changes that you have saved, **so don't delete them** (e.g. .git, .gitignore, .gitinclude).
When wanting to collaborate on a project, you probably want to sync your repository with a hosting service on the internet (or _clone_ an existing one).
There are numerous platforms that offer the hosting of repositories: Gitlab, Github, Sourceforge, Bitbucket, etc. 
As mentioned in the introduction, we will be focusing on Github.

### Changes

While coding, you might come across a moment where you would like to save what you have done. 
Either because you finished your work, or (more frequently), you are about to write some incredibly sketchy code, and you are not sure if it will work.
This is called _committing_, and should be done fairly frequently. 
If you find yourself in the latter case (wanting to get rid of whatever mess you just managed to put on the screen), you can simply _revert_ your last commit and start fresh.

Apart from all the features you have in a web application such as Github, this will be the most important utility in documenting your code.
Make sure to give each name a proper title, and, if necessary, a description. The are several 'best practices' for commit messages and titles. 
The [_50/72 rule_][1] is a good one to go by.

To update your repository with the latest version, you should _pull_ changes from the _remote_.
Please remember to always pull before making any changes, this ensures that you are working with the latest version of the codebase (this is especially so when branching from dev, as to prevent merge conflicts).

Once done with these changes, you push them to the _remote_.

### Branches

Nobody likes working together, especially not computer scientists. Even they, however, recognize the need for collaboration in big projects.
Using the system we introduced in the previous paragraph, however, 
two people working on the same code at the same time could potentially change or remove something the other person was just working on.
This is where branches are often used. A branch is essentially an isolated collection of commits (changes). 
When working on, for example, a new feature, _branch_ off of your current branch, and work on that branch.
This isolates the changes you're making on the code, preventing other people (or other features!) from writing code conflicting with yours.

Whenever you want to apply the changes you made, you can _merge_ your branch back to the branch it came from.
Note that there might still be conflicts with other changes in the branch you are merging to.
In this case, you simply go through all the conflicting parts of the code, making sure that your hard work still does what it should at the end of the merge.

This might be one of the more confusing parts of git, so if you don't get it immediately: 
Don't worry, and please do some experimentation. If you commit your code regularly and comment it properly, you can always go back in case of trouble.

### Feature Branch Workflow

As with all complex and flexible systems, there are some conventions in the use of git.
There are numerous ways of coordinating a team to make git an effective workspace.
Here, we will talk about the _feature branch workflow_.

In the feature branch workflow, the idea is to separate features (or fixes) into different branches, and then merge the feature, once finished, with your main branch.
This ensures that you'll always have a working version of your software, and avoids issues regarding two features not working together.
The fact that two features together might create bugs, whilst they won't individually, is often circumvented by creating a so-called _development_ branch, or _dev_ branch.
You will merge the features into this branch first, then, once tested, merge the dev branch into the main branch. Often labeled as the _master_ branch.

An example of the feature branch workflow might look something like this:

![alt text][feature-branch-example]

### Motivation

I think it's important to tell why exactly I have chosen to introduce the feature branch workflow, instead of another git paradigm.

- The main reason is that by using branches to label different features, it becomes easy to assess in what state the project is in. 
This is especially the case when working together on a project.
- Having an always-working version of the software is a must when wanting people to integrate with your application easily (be it forking, or using it as a dependency on another project).
- And most importantly, it's easy to go back and remove features. If you come into any trouble with a feature or set of them, you can easily see where the merge request for that feature has taken place, and what changes were made to make that feature happen.

The advantages listed above assume that you are working together with people, or might want to at a later stage.
If this is not the case, nothing is stopping you from just having a master branch and committing everything to there (_trunk-based developement_).
These best practices and paradigms should be used as **a guide** to an efficient and effective workflow.
It is, however, very important to be on the same page about your conventions within a team. 
Which is the reason why I recommend following the chapter on Github as close as possible when starting.

## Github

Github is a platform on which you can save your repositories, both for redundancy, and collaborate with other people on your projects.
But it can do much more than that. You can create boards to keep track of project progress, discuss code changes, assign people to certain tasks, and much more.
This, again, is not unique to Github. These features are pretty standard for a lot of these web applications/hosting services (you can barely call them exclusively hosting services).

Remember that Github **hosts** your repository, so adding, committing, branching, etc. is done locally. 

### Getting started

To get started in Github, simply create a new account, log in, and press the 'new' button to create a new remote repository. 
Follow the instructions there using your favorite Git application.

Congratulations, you've made your first repository!

### Issues
 
In the issues board, you can create issues, assign them to collaborators, and create milestones for when you want a certain group of features to be done.
Create issues as soon as they arise, and give them the proper tags associated with your issue.

### Code review

An incredibly important thing in collaborating on writing code is the code review.
Here you will inspect other people's changes and additions, and either approve or request further changes.
All you have to do is inspect the code, ask questions where you don't understand what's happening, and comment on things you think should be improved.
This is often done after somebody has declared their feature as 'done', and opens a pull request.

### Pull Requests

When you pushed a new branch to Github, there will be a prompt. Asking you if you want to create a pull request for your new branch.
This pull request will essentially be an overview of what you have changed in your current branch, and what issues will be solved by merging this branch with another.
You don't need to immeadiatly create a pull request. It's mostly done when you have finished a feature.

When opening a pull request in Github, you can add a description containing an explanation of what this branch changes. You don't need to write a novel. 
In fact, if you have kept track of your issues, you can simply mention all the issues it will solve using [_keywords_][3].

When you want to merge a pull request, you first add reviewers in the 'reviewers' tab.
They will get a notification asking them to complete the review.
As soon as they're done with the reviewing process, you can merge using the big green button at the bottom of the page.
When you merge your pull request with you _default_ branch, Github will automagically close the linked issues.

> Note: you can often merge branches without needing reviews, except for the _default_ branch. It is however recommended to have at least one person look at your changes before merging.

### Default, and protected branches

It can happen that somebody accidentally deletes the master branch, either by a typo or a misclick, it can happen.
By now, you probably know enough about Git to realize that this is not good. 
Since Git tracks changes, when deleting the master branch you have removed the thing it compares the changes to, deleting **all** your work.

To prevent people from making these kinds of mistakes, every repository on Github has a so-called default branch. 
These branches are protected meaning that they can't be deleted, and potentially extra restrictions.
Often, restrictions include not being able to push directly to the default branch. 
Meaning that you can change whatever you want on the default branch **locally**, but when you try to push the changes, GitHub will return with an error, saying this is not allowed.
This results in you only being able to make changes via a pull request, often with a minimum number of reviewers to make sure nothing messes up your master branch.

When working in a hierarchical team structure, a supervisor or _maintainer_ often has to approve a pull to master.

### Basic workflow

When putting all this together, this is the kind of workflow you'll end up with.

0. Create a new branch
1. Start working on your issues
2. Commit changes
3. Push changes to remote (Github in this case)
4. As soon as you push to a new branch Github will give you the option to make a pull request, do this whenever you deem it necessary
5. When creating the pull request, mention all the issues you're working on using [_keywords_][3]

> Mentioning the issues will link them to the pull request. This ensures the issues board will always be up to date.

8. When the pull request is ready for reviewing/testing, mention all the people authorized to review your work.

> The master branch is protected and only maintainers can approve a merge to master, please make sure to include these if it's not done automatically

9. After all reviewers have approved, merge and close

### Further reading material 

If there is any unclarity, and maybe you want a different explanation or perspective on certain concepts. Consider these resources.

- [Git and Github for beginners][4]
- [GitHub official docs][5]
- [Feature branch workflow][2]

If you're using Git for the command line, and you want to read into the commands further.

- [Git official docs][6]

[1]: https://medium.com/@preslavrachev/what-s-with-the-50-72-rule-8a906f61f09c
[2]: https://www.atlassian.com/git/tutorials/comparing-workflows
[3]: https://help.github.com/en/github/managing-your-work-on-github/linking-a-pull-request-to-an-issue

[4]: https://product.hubspot.com/blog/git-and-github-tutorial-for-beginners
[5]: https://docs.github.com/en/free-pro-team@latest/github/getting-started-with-github
[6]: https://git-scm.com/docs

[feature-branch-example]: https://miro.medium.com/max/700/1*uUpzVOpdFw5V-tJ_YvgFmA.png "Feature branch workflow example"
