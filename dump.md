+ The [Nix packages list](https://search.nixos.org/packages) is useful, but how does one specify a different version of a package?

+ What does `nix-env` do?

+ Are shells other than Bash supported? Wondering as a Fish user because the page only mentions Bash

+ What makes an expression reproducible?

+ What do the terms "run-time", "build-time", "compile-time" mean? (And how are they spelled correctly?..)

+ What the term "functional language" means is well defined, but what does the adjective "functional" mean in the context of a build process? It probably has to do with reproducibility or purity, but what would a build process **not** being functional mean?

+ What is a "builder"?

+ What will run a Nix expression?

  Presumes that Nix will run it with some inputs given to it, but not having full understanding of the process still renders the whole thing confusing.

+ What is the shortest possible introduction to the Nix language?

+ What are these Nix files for: `shell.nix`, `default.nix`, `flake.nix`?

+ What are "flakes"?

+ How to uninstall Nix?

+ Wondered whether there is something similar to [cookiecutter](https://github.com/cookiecutter/cookiecutter)?

Major sources of confusion appear to be
> + override / merge terminology
> + channels / flake sources

The `haskell4nix` docs use `nix-env` heavily, and this command keeps being a confusing topic:
+ How to do this on NixOS when using [Home Manager](https://github.com/nix-community/home-manager)?
+ How to specify needed packages in flakes on a per-project basis? (There is nothing about flakes in this guide.)

**Interviewer**: Why is it important for you to manage packages or a development environment declaratively?
**Participant**: Easier to reason about the state of the system; typing stuff on the command line makes it hard to follow.

**Interviewer**: How did you find out about flakes?
**Participant**: Keep hearing about it, and that they are more self-contained, better, the way forward.

**Interviewer**: Can you tell what the differences are between `default.nix` and `shell.nix`?
**Participant**:  I honestly don’t know. I think `shell.nix` may provide development tools, whereas `default.nix` does not have them, so they are better to build for production environments.

**Interviewer**: Do you have mental model how `nix build` evaluates a Nix expression?
**Participant**: Spent some time reading Nix Pills on how derivations are constructed, but not really. Here is an attempt:

> Nix will build all the dependencies of my project and not reuse it across the system. I will have a certain version of my dependencies made available. It’s kind of like a container build with this content-addressed idea where you build it once and will not have to build it again. But really I don't care about this as a user.

**Interviewer**: Why did you start with NixOS in the first place?
**Participant**: It intrigued me as I liked the idea to set up an entire system declaratively, and already had a home laptop as starting point. However, I did not anticipate how difficult it will be to start developing on NixOS, and I assumed to that I could use the same workflows as before.

**Interviewer**: Would you consider starting over on Ubuntu/Arch?
**Participant**: I could do it, but was migrating machines anyway, and I prefer to use and stay with a single OS.
