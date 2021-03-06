# jvm [![Build Status](https://travis-ci.org/caarlos0/jvm.svg?branch=master)](https://travis-ci.org/caarlos0/jvm)

> The _"Java Version Manager"_

Automatically change `JAVA_HOME` based on current directory `pom.xml`
or `.java-version` files.

The philosophy behind this project is to simplify and automatize the `JAVA_HOME`
changing, much like `rbenv` and `rvm` do for Ruby.

It's pretty common to have to work in Java 6, 7 and 8 projects, and changing
`PATH`s and `JAVA_HOME`s by hand is annoying.

### Usage

```sh
$ git clone https://github.com/caarlos0/jvm.git ~/.jvm

# for bash
$ echo "source ~/.jvm/jvm.sh" >> .bashrc

# for zsh
$ echo "source ~/.jvm/jvm.sh" >> .zshrc
```

Then, just `cd` to a java project folder. If the `pom.xml`  has a
`<java.version>1.7</java.version>`, for example, `jvm` will try to
set JDK7 to your PATH.

If you don't have and don't want to have this in your project's pom,
you can also do this:

```sh
$ jvm local 7
```

On OSX, `jvm` will use the `java_home` tool to find the available versions. For
Ubuntu, right now `jvm` has `/usr/lib/jvm/java-${version}-oracle/` hard coded.
This might change soon. If you need custom versions, like `6-openjdk`, for
example, you can run `jvm config` and add a line like this:

```
6-openjdk=/path/to/openjdk/6
```

And `jvm` will automagically works.

### `jvm` commands

Right now, `jvm` has the following commands:

- `local VERSION`: creates a `.java-version` in the current dir with the given
version;
- `global VERSION`: creates a `.java-version` in your `$HOME` dir with the given
version;
- `jvm config`: opens the `~/.jvmconfig` file in your default `$EDITOR`. Useful
for defining custom versions and/or paths;
- `version`: shows current version;
- `help`: shows the help.

### Antigen/Antibody

For those using Antigen/Antibody, just hit

```sh
# for antigen
$ antigen  bundle caarlos0/jvm

# for antibody
$ antibody bundle caarlos0/jvm
```

And it should all work out of the box.
