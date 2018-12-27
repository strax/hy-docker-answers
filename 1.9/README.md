Link to Docker Hub: https://hub.docker.com/r/samikukkonen/purescript-development-environment

Contains PureScript toolchain (A functional language that compiles to JavaScript) and node to execute the compiled sources.

I first base my image on the node image, update apt packages and install a few utilities. Then I set build arguments for the PureScript version and the distribution package's SHA1 checksum. I then move to the temporary directory, download the appropriate prebuilt PureScript binary, validate its checksum and extract the tar package to /opt. To minimize layer size I run these commands in a single RUN block and in the end delete the downloaded tar file. Next I configure the container's PATH environment variable to contain the PureScript binaries and install a few toolchain utilities with npm. After that, the Dockerfile moves cwd to /home/node/psci-session and chowns /home/node to the node user. Then the dockerfile is set to change the user to node and initializes a new PureScript project in the /home/node/psci-session directory. Finally the image contains a default command which starts a PureScript REPL.