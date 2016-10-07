Lablup Sorna
============

Sorna ("Software on Remote Networking Appliances") is a distributed back-end
computation service with highly abstracted API.
Unlike AWS Lambda, it provides a preset of kernel images representing various
programming environments and allows users to execute their code snippets
without a cumbersome packaging process. All sub-projects are licensed under
LGPLv3+.

Components
----------

### Sorna Manager / API Gateway

It routes external API requests from front-end services to agent instances by checking the instance registry.

 * Package namespace: `sorna.manager`
 * https://github.com/lablup/sorna-manager

### Sorna Agent

It manages individual EC2 instances and launches/destroyes Docker containers where REPL daemons (kernels) run.
Each agent on a new EC2 instance self-registers itself to the instance registry via heartbeats.

 * Package namespace: `sorna.agent`
 * https://github.com/lablup/sorna-agent

### Sorna REPL

A set of small ZMQ-based REPL daemons in various programming languages and configurations.
It also includes a sandbox implemented using ptrace-based sytem call filtering written in Go.

 * https://github.com/lablup/sorna-repl
 * Each daemon is a separate program, usually named "run.{lang-specific-extension}".

### Sorna Common

A collection of utility modules commonly shared throughout Sorna projects, such as logging and messaging protocols.

 * Package namespaces: `sorna.proto`, `sorna`
 * https://github.com/lablup/sorna-common
 
### Sorna Client

A client library to access the Sorna API servers with ease.

 * Package namespaces: `sorna.client`
 * https://github.com/lablup/sorna-client

Installation
------------

The Sorna project uses latest features in Python 3.5+ and docker.
We highly recommend to use [pyenv](https://github.com/yyuu/pyenv) to use an
isolated setup with custom Python versions that might not be supported by your

First, install Docker on your system. We have tested Sorna on Linux/Ubuntu and
macOS ("Docker for Mac").

For a single PC setup, just run `pip install sorna`.
It will automatically install all above sub-projects as well as their dependencies.

Development
-----------

### git flow

The sorna repositories use [git flow](http://danielkummer.github.io/git-flow-cheatsheet/index.html) to streamline branching during development and deployment.
We use the default configuration (master -> preparation for release, develop -> main development, feature/ -> features, etc.) as-is.

