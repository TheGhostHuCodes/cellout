Thank you for your willingness to make `cellout` better!

If you're new to Haskell, don't worry, so am I, and I'm writing these
instructions for newcomers like us.

We're using [stack](https://docs.haskellstack.org/en/stable/README/) to keep
track of and install all of the dependencies. Fair warning that when you get
`stack`, it will, by default download its own version of ghc (the Glasgow
Haskell Compiler), which is a pretty big download. Luckily you'll only need to
do that once, and you can even uncomment the `system-ghc: true` remove the
leading `#` around line 53 of `stack.yaml` in a pinch to get going.

# Building

Building the first time will take a while as you get all of the dependencies
and compile them on your machine. Don't worry,  builds after that will be
faster, since stack will cache these and not rebuild them unless the versions
change.

```
stack build --fast
```

# Running the executable

```
stack exec cellout-exe
```

If everything worked, you'll see the usage printout, since we did not specify
an input file.


# Testing

While you can use the running instructions above for running the resulting
binary, we also have a test suite that you can run.

```
stack test
```

# Working iteratively

As a relatively inexperienced Haskell programmer, I enjoy working `gchi`, the
interactive shell of the Glasgow Haskell Compiler. `cellout` has a few
dependencies (like Aeson, the JSON parsing library), which means you will need
a Haskell environment where those dependencies are available. Luckily, we can
do that with

```
stack exec gchi
```

This will startup GHCi with a message like this:

```
GHCi, version 8.4.3: http://www.haskell.org/ghc/  :? for help
*Main>
```

that `*Main>` prompt is where we can now load (and later reload) the files
we're working with, to see the compiler errors and try out our new functions
interactively after we succeed in compiling.

```
:load src\Lib.hS
```

If we haven't broken anything, we'll get a message like this:

```
[1 of 1] Compiling Lib              ( src\Lib.hs, interpreted )
Ok, one module loaded.
```

Otherwise, we'll get compiler error message. Either way, as we edit that file,
we can reload it with:

```
:r
```

You can also `:browse` to see what's available, use `:t` to find the type
information. and try to use some of these functions interactively.


Something that might come in handy is a sample in-memory representation of a
notebook. We have a few of those in the test/sample.hs folder.
