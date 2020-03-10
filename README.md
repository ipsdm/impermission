
# impermission

_(im)permission structures which promote the autonomy of contributors_

## Problem

The existing codebase management structures of git-extending systems (ex.
github, gitlab) are oriented towards hierarchical control of the codebase with
final decision making power residing at the account or organization owners of a
particular fork. Within github this power can be partially extended to
non-owners of the repository but which has been revocably designated as
"code-owners" (which is perhaps a misnomer).  

Within open-source software, for stakeholder sets which do not rely on
coordinating around a single fork of a codebase the fork based model can be
viewed as sufficient; if any user of a codebase require alternative
functionality than what is provided in the base fork, that user may simply fork
that codebase, whereby within the new fork they gain full autonomy to modify
that codebase to meet their needs. If they view that their changes may be
beneficial to the wider community then they can open up a pull (or merge)
request to the original repository whereby the owners of the original
repository must approve said change. 

For decentralized stakeholder sets which _do_ reply on coordinating around a
consistent codebase, the fork based model fails to accommodate for any complex
decision structures beyond that which the account/organization owners serve as
the gatekeepers and interpreters of all decisions made. 

This becomes problematic as the needs of the user and developer communities
of a codebase outgrow the capabilities of the codebase
account/organization owners. Some ways which this outgrowth may occur:
 - Throughput; the owners no longer have the enough capacity (either
   individually or through delegation) to evaluate time sensitive changes which
   must be made to the codebase. 
 - Understanding; the owners no longer understand newly developed sections of
   the codebase and are therefor are potentially no more qualified to judge its
   modifications than other developers with a similar general understanding of the
   codebase.
 - Conflict; the community consensus of best actions for codebase modifications
   differ from that of the repository owners. 

## Solution

A short-sighted perspective may that it is good enough for a community to
organize and "fork-out" the original repository owners of a repo however this
is not a truly a solution, as it just reproduces the same hierarchical model
accept with different actors, as well this (non-)solution neglects to take into
consideration potential information-flow inertia which would preference the use
of the original code base (due to for example, number of page-views or github
stars/forks). 

Any true to solution should have consideration for the following factors: 
 - Safety; sufficient options for safety checks and file and/or import locks
   should be available such that risk of integration of malicious code is
   minimized.
 - Adaptability; the permission sets of code contributors should be based dynamically
   on the active contributions and their acknowledged merits from the wider community, 
   as well discretized to the kind/form/locality of code contributions. 
 - Tyranny of majority; code changes should not simply be based on the whims of
   what the majority of users want, they must be based on a strategy for
   long-term codebase success. A simple solution is to develop an agreeable rule
   set whereby the majority acknowledge expertise of specialized individuals and
   democratically and revocably grant them specialized extended permissions.  

### Implementation

One implementation would be to include a number of dot-files (`.PERM`)
at every folder level which act to parameterize the permissioning mechanisms
(PMs) and also further discretize these permissions to the sub-package level.
The dot-files are then interpreted by the PMs within the (git-extending) host
of the code during pull requests. Other input such as approvals made
through pull requests (in the form of comments, reviews etc.) could also be
utilized by the PMs in order to perform the final merge of pull requests.

The continuous updating of permission levels of developers could be
automatically (or not automatically) handled based pre-agreed upon metrics or
votes by which developer permissions change. As an example, if the permission 
level was based on quantity of code contributions, the permission level stored
within the dot-files could be automatically updated based with each commit.

Further, the updating of fundamental parameterization and mechanisms of the PMs
could be updated through the same process as the dot-files which define the
mechanism and associated parameters are held _within_ the git repository.  

### Challenges 

The most obvious challenge is the classification of appropriate metrics /
voting procedures for which the permissions mechanisms adapt-from and are built
upon. Abstracting a wide base of possible initial solutions for any code
community to begin with is vital for the utility of this impermission project.
For thought, some initial metrics worth exploration include:
 - characters changes of code
 - characters changes of code comments
 - number of logical operators and definitions

In addition these metrics may be weighted by agreed upon significance of:
 - a package, file, or function etc., 
 - contributions from specific users, 
 - approval from specific users.  

### Implementation Steps

The proposed implementation path can be broken down into three basic steps 

 1) Research/development/community-engagement of core impermission protocols
 2) Initial implementation of protocols as a
    [github-app](https://developer.github.com/apps/) (barring that repo owners
    still have the capacity to block use of this app)
 3) Secondary Implementation as a
    [Cosmos-SDK](https://github.com/cosmos/cosmos-sdk/) module built as a
    modification of [GOGS](https://github.com/gogs/gogs)

