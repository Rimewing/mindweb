---
title: GNU Stow
author: Arokh
description: GNU Stow puts everything into a neat little structure...
summary: A little tool that changed a LOT about how I interact with dotfiles.
tags: ["stow", "cli-tools", "dotfiles", "configuration"]

date: 2024-04-10T15:55:03-07:00
draft: false
toc: true
bash_script: true
---

> You can find the website [here](https://www.gnu.org/software/stow/).

So, do you have tons and tons of configuration files that you can't ever remember how to 
set up when you do a fresh installation? Well, have no fear because this neat little 
tool will allow you to keep them all in one spot and even allow you to use version
control to maintain them.[^1]


## Installation

Thankfully, stow is a package that is part of Arch's extra list. This means it's very
easy to install this tool. It's a tiny download but, honestly, this is one of the best
things Aussir has shown to me.

<pre>
<span class="bash sudo">sudo</span> {{< bash-script command="pacman" args="-S" cmd-tail="stow" >}}
</pre>

## Usage
> Adding new configs? No problem. Importing old configs? No problem.

### For All Configurations

When using `stow` we need some directory set up as our base of operations. Whether you
plan to start from a fresh Linux installation, from version control, or with existing
configurations, you'll need to set your directory structure up to make use of it. `stow`
uses the parent of the current working directory by default but that can be changed (see:
`stow --help` for details). During this explanation, I'm going to use neovim as an
example and I'll be stowing the files in `~/dotfiles`. Additionally, we'll be assuming
the default locations of neovim's configurations for clarity's sake.

<pre>
~/
 &#x251c;&#x2500; .config/
 &#x2502;  &#x2514;&#x2500; nvim/
 &#x2502;     &#x251c;&#x2500; init.lua
 &#x2502;     &#x2514;&#x2500; ...
 &#x251c;&#x2500; .local/
 &#x2502;  &#x251c;&#x2500; share/
 &#x2502;  &#x2502;  &#x2514;&#x2500; nvim/
 &#x2502;  &#x2502;     &#x2514;&#x2500; ...
 &#x2502;  &#x2514;&#x2500; state/
 &#x2502;     &#x2514;&#x2500; nvim/
 &#x2502;        &#x2514;&#x2500; ...
 &#x2514;&#x2500; .cache/
    &#x2514;&#x2500; nvim/
       &#x2514;&#x2500; ...
</pre>

That's a lot of places to go looking for stuff and they can easily be lost amongst the 
various other files and folders required for desktop environments and the like. Now,
let's put this into a single directory that will be easy to put into source control...

As previously mentioned, we're going to use `~/dotfiles` as our base folder for `stow`.
Let's do that first:

<pre>
{{< bash-script command="mkdir" cmd-tail="~/dotfiles" >}}
{{< bash-script command="cd" cmd-tail="~/dotfiles" >}}
</pre>

This will create our base folder. Now, the next portion is that we want to create a `stow`
for neovim, which we'll simply call `nvim`:

<pre>
<span class="bash comment"># Current working directory: ~/dotfiles</span>
{{< bash-script command="mkdir" cmd-tail="nvim" >}}
{{< bash-script command="cd" cmd-tail="nvim" >}}
</pre>

Inside this folder is where we're going to be placing all of our dotfiles for our neovim
instance and we'll build this folder structure exactly like neovim is expecting. Like so:

<pre>
<span class="bash comment"># Current working directory: ~/dotfiles/nvim</span>
{{< bash-script command="mkdir" args="-p" cmd-tail=".config/nvim" >}}
{{< bash-script command="touch" cmd-tail=".config/nvim/init.lua" >}}
{{< bash-script command="mkdir" args="-p" cmd-tail=".local/share/nvim" >}}
{{< bash-script command="mkdir" args="-p" cmd-tail=".local/state/nvim" >}}
{{< bash-script command="mkdir" args="-p" cmd-tail=".cache/nvim" >}}
</pre>

We end up with a folder structure that looks like this:

<pre>
~/
 &#x2514;&#x2500; dotfiles/
    &#x2514;&#x2500; nvim/
       &#x251c;&#x2500; .config/
       &#x2502;  &#x2514;&#x2500; nvim/
       &#x2502;     &#x251c;&#x2500; init.lua
       &#x2502;     &#x2514;&#x2500; ...
       &#x251c;&#x2500; .local/
       &#x2502;  &#x251c;&#x2500; share/
       &#x2502;  &#x2502;  &#x2514;&#x2500; nvim/
       &#x2502;  &#x2502;     &#x2514;&#x2500; ...
       &#x2502;  &#x2514;&#x2500; state/
       &#x2502;     &#x2514;&#x2500; nvim/
       &#x2502;        &#x2514;&#x2500; ...
       &#x2514;&#x2500; .cache/
          &#x2514;&#x2500; nvim/
             &#x2514;&#x2500; ...
</pre>

#### Adding New Configurations

When you're adding new configurations, there's only one more step after you configure
the stow directory: `stow`ing your program(s). As before, we'll be using neovim as our guinea
pig.

<pre>
{{< bash-script command="stow" cmd-tail="nvim" >}}
</pre>

From here, you will want to simply use `~/dotfiles/nvim/` as your basis for editing these
configurations. `stow` creates symlinks for each of the files stowed away. Any changes
made to individual files won't need to do this but if you delete a file or alter the
structure of your directory tree, simply restow your program to propegate any changes. For
instance, to restow neovim after you have added new `.lua` files to
`~/dotfiles/nvim/.local/share/nvim/`:

<pre>
{{< bash-script command="stow" args="--restow" cmd-tail="nvim" >}}
</pre>

#### Importing Existing Configurations

If you already have a program configured but you want to `stow` it as well, simply create
the directory structure for your new program as we did above for neovim, giving it a
name that will help you identify it (for example, `bash`). Once you have configured your
`~/dotfiles/bash` folder, simply use the `--adopt` switch when you `stow` your `bash`
program and it will move files from wherever they are into `~/dotfiles/bash` then create
symlinks.[^note] Like so:

<pre>
{{< bash-script command="stow" args="--adopt" cmd-tail="bash" >}}
</pre>

[^note]: NOTE: I HIGHLY suggest a test run of this with the addition of the `--simulate`
    and the<br>`--verbose="1"` switches. This will give you an output of everything `stow` is
    going to do without actually changing anything so you can make adjustments to your
    structure as necessary.

#### Adding Configurations via Version Control

NOTE: To use `stow` with version control systems, simply replace the creation of the `~/dotfiles`
directory with a `pull`, use the `--target="~/"` flag, and (optionally) create a symlink
to your repo for easy access,[^2] like so:

<pre>
<span class="bash comment"># Current working directory: /src/stow</span>
{{< bash-script command="git" cmd-tail="pull" >}}
<span class="bash command">stow</span>&nbsp;<span class="bash args">--dir</span><span>=</span><span class="bash cmd-tail">"/src/stow/dotfiles"</span>&nbsp;<span class="bash args">--target</span><span>=</span><span class="bash cmd-tail">"~/" nvim</span>
{{< bash-script command="ln" args="--symbolic --directory" cmd-tail="/src/stow/dotfiles ~/dotfiles" >}}
</pre>


-`Arokh`

[^1]: This post will eventually link to the post that talks about version control but,
    since the version control post isn't written just yet, I don't have anything to
    link to. As Yoshi-P says, "Please look forward to it."
[^2]: I haven't tried this out yet... this actually could just cause major issues. Note
    to Arokh: "Test this out on a VM sometime and make sure this doesn't cause an
    explosion of some kind."
