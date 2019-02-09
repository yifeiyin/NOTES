Reinstall Vim Using Brew
========================

## Why

Because the one comes with macOS is not the newest version, and are not built with some features that are sometimes handy for us.
In particular to me, default one does not have:
    - clipboard
    - folding


## How

Run `$ brew install vim`

Make sure to keep an eye on the output, especially any warnings or errors.

What happened to me is as follows:
```
Error: The `brew link` step did not complete successfully
The formula built, but is not symlinked into /usr/local
Could not symlink share/man/de/man1/ex.1
/usr/local/share/man/de/man1 is not writable.
```

Same thing happens when I retry:
`$ brew link vim`

To solve this problem, need to do `sudo chown -R $(whoami) $(brew --prefix)/*` from [GitHub Brew Issue Page](https://github.com/Homebrew/brew/issues/3228)


