# A Case for Git When Using Configuration Management like Puppet


## Intended Audience
 * Middle Management
 * Folks new to Git and/or SVN
 
## Description
This document details why Puppet and all other Configuration Management tools rely heavily on Git as the preferred VCS
over SVN and why using SVN with Puppet is not fully supported or a good idea.

## Executive Summary
Puppet and the puppet ecosystem are built around the fact that you will be using Git as your Puppet code VCS because of
the major advantages of git over SVN.  Without git many tools and workflows for Puppet will simply not work thereby
rendering all efficient workflows and design patterns useless with regards to Puppet.  Using SVN with Puppet is highly
discouraged and not recommended by Puppetlabs or the Devops and Puppet Community.

## Reasons
 * Because tools like R10K, rspec-puppet make use of git’s lighting speed branch capabilities as well as its
distributed model.  

When deploying Puppet into your environment where an existing SVN culture already exists, it is a wise decision to use
Git as Puppet's VCS. Without Git you will not be able to download third party modules hosted on Github.com, Gitlab.com
without running into major time consuming issues.  Over 99% off all puppet modules are hosted on git which SVN cannot use.

## Distributed Model
SVN is extremely slow over a WAN whereas Git does not require a connection to perform commits and branches.  This is a huge
win for anybody working over a slow or bad internet connection.  The developer still has the ability to work very effeciently
without connecting to a central server that SVN demands.  Git's distributed model also doubles as a disaster recovery solution
should the Git server ever become damaged. 

## Do not get rid of SVN
This document is not suggesting you remove SVN from your environment.  Instead, the document is saying, use Git for at
least your Puppet code.   If you decided to use Git for other projects that is completely up to you and your team. 
However, Devops and Puppet rely heavily on Git.  Git and SVN should not be made mutually exclusive in your environment
if you already have an established SVN configuration.  Additionally, the decision to replace SVN company wide
is a much bigger decision and will impact your developers greatly without their input. This document is only suggesting to use
Git for your configuration management needs.

Furthermore, failure to use Git for Configuration Management will insue more problems and chew up time of your most valuable 
employees and contractors.  If you value your money, time and efficient organizations, you should not use SVN. 

## Incompatible Tools

 * rspec-puppet
 * R10K (extremely limited support, and puts heavy load on SVN servers)
 * Librarian-puppet

## Branching Speed
Heavy use of SVN branching causes the SVN server to copy entire directory structures multiple times which could take hours thereby causing 
outages for other SVN users as its causes heavy disk and network IO.  R10K (A Puppet Code management system) relies heavily on branches
which could cause SVN service disruptions as it was originally designed to use Git.  Having multiple puppet servers checkout branches 
all the time could run the risk of SVN service interruptions for all users.


## Success Stories
Please add a success store here if you have one.


## Contributing
Got a point you want to make in this document or see something that is missing?  This is meant to be a community driven
document for all people to use and change.  PRs are strongly encouraged.

## Quotes

"You'll find yourself about 900x more agile with git or the like" - Binford2k


## References
Cool blog post or white paper link goes here.