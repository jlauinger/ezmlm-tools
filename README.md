# ezmlm wrapper commands

These are some handy commands for managing ezmlm on the command line. They add features that are not provided out of the box. The repository includes modified German locale files that correctly apply header encoding.


## Configuration

```
cp jl-ezmlm.conf.example ~/.jl-ezmlm.conf
```

Copy the configuration file to your home directory. This is where it is expected by the scripts. Configure your ezmlm root directory, if it is not `~/ezmlm`. Add the executable files in the directory to your PATH, e.g.:

```
cd ~/bin
ln -s ../ezmlm-tools/jl-ezmlm-* .
```


## Setting up German locales

With the standard ezmlm German locale files, `/etc/ezmlm/de`, German umlauts will not be displayed correctly, since the wrong encoding is applied to the German header files.

The files in `lang-de` in this repository use correctly encoded versions for all subject lines. You should use them to avoid non-displayable characters in your emails:

```
ezmlm-make -+ -C ~/ezmlm-tools/lang-de ~/ezmlm/awesomelist
```


## Commands

**jl-ezmlm-lists**

```
jl-ezmlm-lists
```

Shows a list of all available ezmlm lists.


**jl-ezmlm-subscribe**

```
jl-ezmlm-subscribe LIST RECIPIENT1 ...
```

This command will send a subscription invitation to each supplied e-mail address. Unlike `ezmlm-sub` however, it will not directly add the recipients. This ensures the confirmed opt-in policy is not violated.

Sent invites will be stored in invites-LIST.txt for future reference (see `jl-ezmlm-pending`).


**jl-ezmlm-pending**

```
jl-ezmlm-pending LIST
```

This command will list all e-mail addresses that have been invited, but are not yet list members (due to a pending opt-in confirmation or a pending moderator confirmation).


## License

Copyright 2017 Johannes Lauinger  
Licensed under the [MIT License](https://choosealicense.com/licenses/mit/)

Developed primarily for use with accounts from the fine folks at [Uberspace](https://uberspace.de).
