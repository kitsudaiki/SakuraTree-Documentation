Introduction
============

Motivation
----------

This is/should become a simple-to-use and fast automation tool to deploy tools and files on multiple nodes.

My main project (still private) consists of multiple components and is hard to test and debug without an automated deploy process. I already had experience with the tools Ansible and Chef, but I find both of them lacking. They use way too generic languages (with YAML in Ansible and Ruby in Chef) which sometimes makes it hard to understand complex structures, in my opinion. For example, the conditionals and loops in Ansible are awkward because YAML is not designed for such structures. Beside this, the debugging is extremely slow and I miss some basic features in both of the tools.

So I decided to create my own tool to try using a better approach. Maybe there already are some other tools similar to Ansible or Chef with better handling, but I don't have the motivation to test all existing tools. Beside this, this is a good side project for me to work at whenever I need some distance from my main project to solve a problem.

Bacause of this the primary goals are:

* easy to use
* fast execution
* fast debugging

The following document decribes how the tools are to build and to used and how the syntax is structured. 


.. raw:: latex

    \newpage


Components
----------

This is the current set of components of this project. There will coming more.

**SakuraTree**

    Path: https://github.com/tobiasanker/SakuraTree

    License: Apache License 2.0

    This is the core component of this project and that's why this is the eponymous tool for this whole project. 

    Because I like tree structures and see the different tasks and threads while deploying in this structure too, I used the tree as name base. Especially I love trees with cherry blossoms, like I saw in japan. *Sakura* is the Japanese name for cherry blossom and cherry tree in Japanese is *sakura no ki*, but this as name is too generic. So I elected *SakuraTree* as name. This basically means the same, but is more unique and fits better as a name. Additionally I'm used to create my tool names from a Japanese name I like, together with an English word, which is related to the function of the tool and in this case here, the translation of *sakura* matches perfectly too.


**libKitsunemimiSakuraParser**

    Path: https://github.com/tobiasanker/libKitsunemimiSakuraParser

    License: Apache License 2.0

    This repository contains the whole parser for the syntax. It use the GNU Bison parser generator to keep the parser easy to maintain. The files, which contains the scripts and are parsed here, will be named in the following document as *tree-files*.


**libKitsunemimiSakuraNetwork**

	Path: https://github.com/tobiasanker/libKitsunemimiSakuraNetwork

    License: Apache License 2.0

    In version 0.2.0 this repository already exists, but is not used at the moment. It contains some first implementations to send data to SakuraTree instances on other nodes. It was part of the first prototype of a multi-node rollout and will be reintegrated in version 0.3.0.


Core Features
-------------

**Be aware, that most of the planed core-features are not implemented at the moment**


**simple language**

Chef contains the full power of Ruby. That brings many functionalities, but makes it hard to write and to understand. Ansible is more easy with its YAML files, but this makes things like loops and conditionals really cumbersome. So I wanted to create my own description language, which is designed for automation. Based on the cherry trees the structure is: seeds create trees and trees own blossoms.

**easily multi-threading**

*current state: implemented*

I often encountered things while deploying one or multiple nodes, which could be done parallel within one node. In Ansible and Chef this is not really intended. This is a big time loss. So I designed the language and the current implementation, so that you can easily create multiple threads and decide which tasks should run parallel and even loops can be spread over multiple threads.

**hierarchical client-server-architecture**

*current state: prototype (prototypical Implemented, but not documented now)*

Similar to Chef, this tool has a client-server-architecture. But this was not enough. Each SakuraTree process can work as client and/or server. So you can create a hierarchical structure of clients and servers for faster data transfer. For example let's say you have a very big image and want to copy it to each node of a deployment with hundreds of nodes. With the ability to spawn new clients and servers within the deployment, you can copy this to one node, which in turn copies the file to two other nodes and these nodes again copy it to the next four nodes and so on.

**live-debugging**

*current state: not implemented now (planned for version 0.4.0)*

Debugging in Ansible and Chef is really slow. When you run into an error and you want to test your fix, you have to run all from the beginning. The changes which were already done in the last run will not be done again but even so the new run can take minutes or hours, until it comes to the point which you attempted to fix. Furthermore, in case the fix was not correct, you have to run this again and wait a massive amount of time and try to process other tasks while waiting. So the plan is that each node stores its process in a local sqlite database to record which task was done and what the input and output was. So after a bugfix, the old process could continue at the point where it failed in the last run.

**rollback-function**

*current state: not implemented now*

For each action a reverse action should be defined to rollback as much as possible. This is also necessary for the live-debugging in the case, that some tasks are deleted or moved while fixing a problem.

**additional command output**

*current state: not implemented now*

When working with an automation tool it's easy to forget each step to create the same setup without the tool. So I'd like a feature to generate a simple manual out of the used scripts with all necessary command-line calls, some simple comments and step descriptions. This could also help debugging.

**graphical monitoring**

*current state: not implemented now*

This is a feature which may be added when the rest works fine and is ready for productive use. Plain text output of deploying is sometimes hard to follow, especially when having many parallel tasks on multiple nodes. Therefore it would be nice to have a monitoring to follow the process, which supports debugging capabilities.
