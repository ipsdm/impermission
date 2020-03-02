# 🏗️
🚧UNDER CONSTRUCTION 🚧

# impermanent
(im)permission structures which promote the autonomy of contributors

This document is just some brainstorming of possible alternative code ownership
structures. 

______

Scheme Attributes: 

 - By file: the code contributions lines to a file determine the amount of
        ownership of that file 
 - By directory: if you've contributed a certain amount within a directory, you
        have ownership over that directory 
          - this should also include subdirectories, as well as parent directories but
          at different rates
 - By project: this is an extension of the idea of the by directory, where the
        entire project is just a top level directory. 
 - By file type: editing code, should give you ownership of documentation, but
        not vice-versa
 - By change kind: commits of new features, or algorithm changes should be
        weighted substantially more than refactors. 
 - By replacement: If you replace somebodies code, you should effectively
        overtaking their ownership over those lines of code, and those algorithms. 
          - If somebody has been highly inactive for a long time, they will
          incrementally lose their ownership
 - Viewable/Verifiable Permissioning Schemes: the calculation of the permission
        schemes shouldn't _need_ to be calculated based on historical git commits, but
        should instead be a real-time ongoing calculation in a separate file, so it's 
        very easy to verify all the different scores off the bat. The permission schemes
        _should_ be allowed to be manually editted, with some certain level of
        high consensus
 - Lock permissions: certain files or lines require certain special permissions
        to change
 - Consensus Level:  The level of consensus required to change a file (certain
        files could be critical and require a high level of consensus) 


Implimentation thought: this probably should _not_ exist as code comments on
each file as to keep with interoperability, all different kinds of code have
different comment styles. This should probably instead exist as a `.PERM.md`
file within each directory

Layout of `.PERM.md`: 
```
Last update: <insert code hash> 

Subdirectory Downward Ownership: 1.00 // how much this directory owns all subdirectories
Subdirectory Upward Ownership:   0.10 // how much subdirectories own this directory
Sideways Ownership: 0.30              // ownership exibited from files in this directory to the whole directory

Override <dir-name> Downward Ownership: 0.22 // override for particular directory
Override <dir-name> Upward Ownership: 0.55 // override for particular directory
...

// these filetypes count for modifying all filetypes, 
// anything not in this list is constrained to its own filetype
FILETYPES MASTER: go, sh

CHANGEKIND MOVE: GET 

ALIASNAME <insert name> <insert pubkey>
...


// ownership is to be calculated based on contributions and sideways ownership
OWNERSHIP OF DIRECTORY
<name>  0.120
<name>  0.230
<name>  0.650 // these must add to 1

// ownership is to be calculated based on contributions
OWNERSHIP <filename> 
<name>  0.120
<name>  0.230
<name>  0.650 // these must add to 1
... 

LOCKFILE <filename> <name> // this key must sign to modify this file
... 

CONSENSUS LEVEL <filename> 0.40, 0.51 // minimum signatures, consensus agreeing with the changes
... 

CONTRIBUTIONS
<name> 
<filename>: <LINENO>, <LINENO>... 
...
...

```



