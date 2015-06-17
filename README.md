# A Case for Git When Using Configuration Management

## Intended Audience
 * Non Technical Decision Makers
 * Folks new to Git and/or SVN

## Acronyms
SCM - Source Control Manager
VCS - Version Control System
SVN - Subversion

## Description
This document details why Configuration Management tools rely heavily on Git as the preferred SCM
over SVN.

## Executive Summary
Making a risky change in a traditional application codebase like Java is not nearly as severe as making a change that
could  potentially takeout your company's entire infrastructure.  You want to be equipped with the best tools for the
job and mitigate any risks. And that means having Git and the workflows and tools that accompany Git.  Failure to
realize the value of Git for your configuration management codebase could spell disaster for your corporation. You
should not downplay Git simply because you already have a non  distributed SCM in place.

## Summary
The agile workflow that has evolved over time consists of:

-  forking 
-  branching
-  rebasing (integrating upstream changes)
-  pull/merge requests (code reviews)
-  branch merging 

This workflow while not specific to any one SCM technology is best reproduced with a distributed SCM like Git.  This
workflow creates a proper safety net with code reviews and peer collaboration that is simple for any developer to use
because forking, branching and code reviews are extremely easy with Git.  Any developer will be much more inclined to
use Git's inherent best practices vs relying on a SCM that promotes risky, un-reviewed changes. Risky changes are
followed by bugs, bad merges, code regressions, and a destabilized codebase. A SCM should never prevent or make
difficult for any developer to perform the right workflow, especially when time is a constraint. The time it takes for a
SVN system to perform the Git workflow is noticeably slower (3X).  With this in mind imagine having to perform a change
at 2AM to your infrastructure with a system that delays the rollout of your changes by 3X.  How can you ensure no risky
shortcuts are taken that would further degrade your codebase or infrastructure?   When working with configuration
management code, the codebase is your infrastructure and the rollout of any bad code can result in unavailable services
or failure to patch security holes. Every infrastructure needs a good system of checks and balances in place such as the
Git workflow. 

## Reasons

### Code Reviews
Peer code reviews promote a more stable codebase and infrastructure because another human has signed off on the
changeset being introduced.  This practice also means that another person is familiar with the changes to your
infrastructure codebase and knows of any risks that might be introduced. Code reviews can easily be discussed among
peers before being introduced into the production configuration management codebase.  While code reviews are not
specific to Git.  Git makes code reviews easy to use  and see. 

### Code Branching
Code branching is a feature of most SCM systems. However, distributed SCMs like Git make it dead simple to branch which
therefore promotes good practices.  Git branching takes as long as writing a 41 byte file to the filesystem. Removing a
branch takes as long as it takes to remove the 41 byte file.  SVN on the other hand copies entire directory structures
from  the checkout location and transfers those files from the server to the client.  Branching in SVN is painful and 
if given the choice a developer usually skips this step due to time constraints. 

### Devops Community and third party tools
Puppet and the puppet ecosystem are built around the fact that you will be using Git as your SCM because of the major
advantages over SVN.  Without Git many tools and workflows for Puppet will simply not work thereby rendering many
efficient workflows and design patterns unusable.  Using SVN with Puppet is discouraged and not recommended by
Puppetlabs or the Puppet Community.

### Distributed Model (No Directly connected server)
Trying to understand the central vs distributed model with regards to SCMs can be very difficult at first.  However, the
distributed model is easily realized soon after your internet connection becomes slow or disconnected.  A distributed
codebase allows a entity to continue creating digestible change sets without the use of a central system.  SVN does not
allow  commits or branches to be created without being connected.  Downtime of a Git server has a much less affect,
because everyone  can still continue working on their features or fixes.

### Forking repositories
Forking repositories became popular with the rise of Git because of the simplicity and speed to fork a repo.  Forking a 
repo allows one to contain the same codebase under their own namespace and the ability to make changes to suit the
authors needs and speed.  The author also has the ability to create a pull request against the upstream repository that
can be peer reviewed before merging to the upstream repository.
 
### Rich Web UI Repository Management Tools
The Git workflow discussed above can only be fully realized with a really good repository management tool like Github or
Gitlab. When these tools are used, you immediately realize why code reviews and collaboration are so easy with Git. 
These tools wrap  RBAC around Git and provide an instant online code collaboration communication platform.  Since
infrastructure  is code you will need a communication platform that is code centric and allows other integration points
to link SCRUM and Agile workflows. These tools mitigate much of the traditional user management and access control
issues and provide a true self service platform.  The sys admins role will only be to keep the underlying infrastructure
running, not creating repositories and granting access control.

### Other Reasons
 * Branches in Git are a core concept used everyday by every user. In Subversion they are more cumbersome and often used sparingly.
 * Branch merging is simpler and more automatic in Git
 * Creating a repository is a trivial operation  `mkdir foo; cd foo; git init`
 * Git encourages collaboration and streamlines communication between developers
 * branching/merging in git is the killer feature.  Compared to svn, branch/merge is almost so easy it's fun!  
 * Rebasing/Merging in git makes SCRUM workflows extremely easy.
 * Git reduces the MTTR as a result of git's accelerated branching and merging capabilities,
 * Changes are easier to stage and are more predictable (Some argue a 3X improvement in per week changes) 
 * Peer reviewed changes in a easily digestible and detailed format.
 * Ability to easily fork code repositories
 * Ability to easily create merge requests and assign them for peer review
 * Ability to create branches and commits without a connection to a central server.  

## Do not get rid of SVN
This document is not suggesting you remove SVN from your environment.  Instead, the document is saying, use Git for at
least your configuration management.  If you decide to use Git for other projects that is completely up to you and your
team.  However, Devops and Puppet rely heavily on Git.  Git and SVN should not be made mutually exclusive in your
environment if you already have an established SVN configuration.  Additionally, the decision to replace SVN company
wide is a much bigger decision and will impact your developers greatly without their input. This document is only
suggesting to use Git for your configuration management needs.

Furthermore, failure to use Git for Configuration Management will ensue more problems and chew up time of your most
valuable  employees and contractors.  If you value your money, time and efficient operation, you should not use SVN. 

## Known Incompatible Tools

 * rspec-puppet


## References
https://git.wiki.kernel.org/index.php/GitSvnComparsion
https://www.atlassian.com/git/tutorials/comparing-workflows/centralized-workflow
http://nvie.com/posts/a-successful-git-branching-model/