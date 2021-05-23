# Ansible

This repository contains my personal ansible roles and playbooks.

## Nice git trick

You can use the `textconv` attribute for `git diff` to provide a nice display of `diff` and `blame` for your vault files.
In order to do that, you will need your vault password in plaintext on your computer (Don't forget to put it in your gitignore !) and put the filename in the variable `vault_password_file` in your `ansible.cfg`. Here, it is in the file `.vault_password`.

Then, edit your local git configuration to add a new attribute in the `diff` section:

``` ini
[diff "ansible-vault"]
    textconv = ansible-vault view
```

You may do that by using the following command

``` sh
git config diff.ansible-vault.textconv "ansible-vault view"
```

Here, I use the name `ansible-vault` for this new attribute, but you can of course give whatever name you like.
Then, create a file `.gitattibutse` and put the following line:

``` sh
*vault.yml diff=ansible-vault`
```

The syntax for `.gitattributes` is 

``` sh
pattern attr1 attr2 ...
```

where pattern can be a regular expression. Here, it tells git that for any file of the form `*vault.yml*` it should use the command specified in the `ansible-vault` attribute of the `diff` section to make a `diff`. Namely, the command `ansible-vault view`.

You may learn more about `.gitattributes` on the [git documentation](https://git-scm.com/docs/gitattributes).
