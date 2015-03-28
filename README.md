Maven TypeScript Compiler Plugin
================================

This plugin adds [TypeScript](http://typescriptlang.org/) compilation to your Maven project without adding any
prerequisites (e.g. installing Node.js) other than JDK 8. It unpacks the TypeScript compiler from a Maven artifact,
makes the [Avatar.js](https://avatar-js.java.net/) native library available with the expected filename, then executes
tsc on the Avatar.js server, which uses Nashorn to execute JavaScript.

Why?
----

There are a variety of reasons that a development team can't require Node.js and NPM for their build process, including
company policy, regulatory and audit compliance, and inertia. While individual developers may be able to work around
these roadblocks, a requirement to install new software on the build server is more likely to remain a problem.

Also, a well-integrated, all-JVM build is a neat idea.

Why not?
--------

It's slow. Startup time for tsc is somewhere around 12 seconds.

What about watching the directory and recompiling when a file changes?
----------------------------------------------------------------------

That's your IDE's job.

Alternatives
------------

Where no such restrictions apply, consider other plugins such as
[frontend-maven-plugin](https://github.com/eirslett/frontend-maven-plugin) or
[grunt-maven-plugin](https://github.com/allegro/grunt-maven-plugin).

How to use
----------

As the Maven artifacts provided by this project are unlikely to be available to your Maven instance, first
install/deploy the [TypeScript redistribution](typescript/) and [tsc-maven-plugin](tsc-maven-plugin/) artifacts,
either to your local Maven repository ($HOME/.m2/repository) or your local Maven repository manager (e.g. Artifactory
or Nexus). Next, take a look at the included [demo project](tsc-maven-demo-project/) for usage information.

Project status
--------------

This project is currently on hold pending two matters:

* Completion of the [Angular 2](http://angular.io/) switchover from Traceur/AtScript to TypeScript. The [information
available at this time](https://github.com/Microsoft/TypeScript/issues/1557) suggests that the upcoming TypeScript 1.5
release may support the required language changes for this to take place. Until then, a suitable demo project for
exploring the second matter cannot be completed.

* A team decision on whether to adopt Angular 2 for front-end development, and whether we are willing to tie together
two build processes (Maven triggering a Grunt build that uses [grunt-ts](https://github.com/TypeStrong/grunt-ts) for
TypeScript compilation) or would prefer to use only Maven.
