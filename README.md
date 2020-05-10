# Sakura-Project-Documentation


This is the documentation of my Sakura-Project with its core-component SakuraTree (https://github.com/tobiasanker/SakuraTree) 

## Prebuild

Prebuild for version 0.2.0 (latest tagged version):

https://gitlab.com/tobiasanker/Sakura-Project-Documentation/-/jobs/394246432/artifacts/browse

Prebuild for latest master-version:

https://gitlab.com/tobiasanker/Sakura-Project-Documentation/builds/artifacts/master/browse?job=build

**IMPORTANT**: The master-version of the documentation actually differs from the master of the code, because the code has a bit bigger restructure for the multi-node support.

## Build 

Build latex-document:

```
git clone https://github.com/tobiasanker/Sakura-Project-Documentation.git
cd Sakura-Project-Documentation
make latexpdf 

# pdf-document is generated under ./build/latex/Sakura-Project.pdf
```

## Contact

If you have any questions or problems with the document or the project in general, then feel free to contact me under: tobias.anker@kitsunemimi.moe
