# Native libraries used by TDLight Java for Mac OS AARCH64

This repository generates JNI packages for each architecture and OS used by [TDLight Java](https://github.com/tdlight-team/tdlight-java).

In that repository I publish settings and some workaround that helped me to compile tdlight-java natives for M1 processor.

Note, that repo dependencies should be cloned. To do that run `git submodule update --init --recursive` in root of this repo. 

Note that I had to specify some environment variables. The first one to resolve `coreutils` between the one installed from `brew` and existing one), the second one is the path to java.

Run following command from dir `scripts/utils`:
```
PATH="/opt/homebrew/opt/coreutils/libexec/gnubin:$PATH" JAVA_HOME=~/Library/Java/JavaVirtualMachines/temurin-17.0.6/Contents/Home ./compile-natives-package.sh
``` 

After successful compilation `tdlight-natives-osx-aarch64:4.0.0-SNAPSHOT` will be placed to you mavenLocal repository (for me, it is `~/.m2/repository/it/tdlight/tdlight-natives-osx-aarch64/4.0.0-SNAPSHOT`)
To use that natives in tdlite-java you need to recompile it as well: https://github.com/dimitree54/tdlight-java
