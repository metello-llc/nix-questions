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

+ Fairly proficient with the shell, but still not sure what `nix-shell` does exactly, other than creating a special environment.

+ Remarks that it’s really hard to find an introduction for declaring a C/C++ development environment.

+ edit this:

  Biggest issues with documentation is that even hot topics are covered sloppily, and hard to discover where one should look for information. Cases in point:

  1. **Use flakes or not?**

    It's a significant change of how to do things and the concensus seems to be that this is the way forward, but there is a lot of noise surrounding this. Posts on Tweag blog are very basic, mostly focused on pinning, but not clear how it relates to system configurations.

  2. [**Home Manager**][home-manager]

    The prevalent advice for most NixOS user configuration question, but it is not straightforward to use, especially when never having worked with dotfiles in an organized manner before.

  3. **What is Nix?**

    Found [Wil T's videos](https://www.youtube.com/watch?v=QKoQ1gKJY5A) that clarified it.

  4. **Hard to judge what are examples of [essential and accidental complexity](https://simplicable.com/new/accidental-complexity-vs-essential-complexity) in the Nix ecosystem.**

+ another edit needed:

  Kick-off problem: [`syncthing`](https://syncthing.net/) does not start automatically. Simply  running `syncthing` works, but not as a service.

  Looks up [Syncthing page](https://nixos.wiki/wiki/Syncthing) in the [nixos.wiki](https://nixos.wiki/), but wants to start it as a user service, and the example only shows it for NixOS.

+
+ How to debug an issue, especially if it does not work as documented?

  > **Participant**: Tried to iron out configuration issues with `nix repl`, but got stuck fast. It would be great if one could debug on one’s own or if there would be a general troubleshooting guide, because my Nix knowledge is not enough to approach this.

+ Some of the found examples use overlays, and it is hard to figure out the rationale behind why they are usually organized the way they are (e.g., split apart from the `default.nix` in many cases).

+ Old configurations use many modules; never had a need for custom modules, and not sure what they are for.

+ Some configuration examples were from people using one repository for multiple systems. How?

+ The [nixos.wiki](https://nixos.wiki/)'s [Configuration Collection](https://nixos.wiki/wiki/Configuration_Collection) is great, but it would be so much better if there would a description accompanying each configuration about how the authors arrived at their solutions.

+ What do functions return, and what are the data types?

+ Switching to another problem: created a few functions to convert color strings for [`nix-colors`](https://github.com/Misterio77/nix-colors/), and wanted to upstream these, but not sure how to do tests.

+ Feels very new to the Nix language and insecure about writing functions, and definitely wants tests, but doesn't want to roll own testing framework for flakes. The lack of guidance on testing best practices is not helpful either, but flakes seem to have an architecture around it so asks around in the Nix community: what's a good way to do things?

+ The Nix language doesn't seem to change very often, so have an intro video, explaining that this will get you most of the way there.
  + An example outline:
    + using the Nix language
      + unit testing
      + documentation strings
      + formatting

+ Have navigation and guidance on how to do things in the Nix ecosystem:
  + map out where to go for which problem
  + state clearly what the state of the art is ("software developers don’t like clever solutions")

Tries calling `git` within `nix-shell -p hello`, it works. Exits that shell, and then tries calling `hello` from `nix-shell -p git`, but it's a no go, which contradicts the current mental model.

+ "_[Nixpkgs] contains precompiled software which is available instantly_"

+ > "purely functional programming language"

  Does not know exactly what it means. Later, after reading the "Functional package language" section, it makes more sense (determinism is a major trait, specify different versions of software, etc.), but would have to use it to understand what it entails.

+ > the Nix language has no notion of package or configurations

  Finds this statement just as baffling.

+ "_It is a huge topic, there is a lot of information, and feels a bit overwhelming in the beginning._"

+ I know what Nix can do, but I don’t know how to interact with it. How to use `buildPythonApplication`? Where does it come from?

+ Doesn't know what `cat` does, and a quick google side trip shows that it is irrelevant to what the demo is trying to convey. After watching the short script unfold, exclaims: "_Cool that you can build environments._" Still not clear whether Nix is an operating system though.

+ Doesn't understand the script's syntax; it seems to be some logic about installation where one can specify many things. Tries to analyze it, "_the question mark reminds me of ternary operator_", and chooses to ignore it for now.

+ Nix is hardcore function-oriented. "_Has this design quality been chosen for its safety and reliability properties?_"

+ Also skips sections "Multi-user support", "Atomic upgrades and rollbacks", and "Garbage collection"; no idea how they are useful or how they fit in the everyday use of Nix, and not interested in the details.

  It is a huge topic, there is a lot of information, and feels a bit overwhelming in the beginning.

+ The notion expressed with the phrase  "without using Docker or any other virtualization" seems to be important. "_Is Nix a Docker competitor?_"

  + > 3. Continuous integration (CI) for free.

    Uncertain what to think about this. "_When you say CI, I think of *different* environments_".

> **Interviewer**: Would you look at ["Ad hoc developer environments" article](https://nixos.org/guides/ad-hoc-developer-environments.html) (a.k.a. "First steps with Nix")?

Doesn't know what "ad hoc" means but "_I can tell that this is what I wanted_".

+ Section "What is a shell environment?

  Looks at at the "hello world example", and gets disheartened again. Has a lot of questions:

  + What's this hello program?
  + Why is it "hello world"?
  + Is this a default program in Nix? No clue why have it.

  + > Here we used the `-p` (packages) flag to specify that we needed the `hello` dependency.

    + So `hello` is a dependency and not a program? Confused what the difference between the terms "program", "package", and "dependency" is.

    + "_Why do we need hello as a dependency?_"

+ "_None of this helped me so far to get where I want to: find out how to make that script to share with my team._"

+ Very intrigued about the "fully reproducible example", and did not expect the `--pure` switch: "_I didn’t think we would need that special command to be "pure"; seems it has to do something with that hashes may be different_".

+ Recreates `default.nix`, inspects first line - seems to be unspecific to Python, looks very mysterious, and `?` and `:` does not make any sense. Doesn't know what `pkgs.python3Packages` means, then skims Python-specific lines. Skims rest of the page, and decides to go back to [Learn].

+ > These attribute names for cross compilation packages have been chosen somewhat freely over the course of time. They usually do not match the corresponding platform config string.

  "_What does it mean that "these names have been chosen freely"? Which one would I want? Probably `gnu32`._" Goes forward with `pkgs.pkgsCross.gnu32.gcc`, and re-runs `nix-shell`. Looks good, dependencies appear to be relevant to `gcc`, but stumped when seeing a Linux kernel name pop up, wondering why it would need that.
