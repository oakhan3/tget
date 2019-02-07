# tget

A super mini-utility to store, retrieve and execute text in your terminal!

## Install

    curl https://raw.githubusercontent.com/oakhan3/tget/master/install | python

## Uses

Storing and accessing (parameterizable) commands and snippets is a hassle in the terminal, your options are:

* piped or sourced files
* terminal reverse search
* static aliases in your `.*rc`/`.*_profile`
* parameterizable functions in your `.*rc`/`.*_profile`

Enter `tget`:

* Store/Retrieve by a Key

    ```bash
    # Store the value
    $ tg put hello --value world
    STORED

    # Retrieve the value
    $ tg hello

    world
    ```

* Store/Execute by a Key

    ```bash
    # Store the value
    $ tg put pyv3 --value "pyenv virtualenv 3.6.4 example"
    STORED

    # Execute the value
    $ tg pyv3 -e
    ...
    New python executable in /../.pyenv/versions/3.6.4/envs/example/bin/python3.6
    ...
    ```

* Store/Retrieve/Execute with Interpolated Environment Variables

    ```bash
    # Store the value
    $ tg put pyv3

    Value: (Hit <ENTER> twice to end input)

    pyenv virtualenv 3.6.4 $NAME && pyenv activate $NAME

    STORED

    # Retrieve the value with interpolated env-vars
    $ NAME=demo tg pyv3

    pyenv virtualenv 3.6.4 demo && pyenv activate demo

    # Execute the value with interpolated env-vars
    $ NAME=demo tg pyv3 -e
    ...
    New python executable in /../.pyenv/versions/3.6.4/envs/demo/bin/python3.6
    ...
    (demo) $

    # ENVVAR=value pairs can also be placed at the end of the command
    $ tg pyv3 -e NAME=demo
    ...
    New python executable in /../.pyenv/versions/3.6.4/envs/demo/bin/python3.6
    ...
    (demo) $
    ```

* Store/Retrieve Multi-line

    ```bash
    $ tg put cow

    Value: (Hit <ENTER> twice to end input)
    _________________________________________________
    /                                                 \
    | What is love?... Baby don't hurt me... don't hurt |
    | me... no moo                                      |
    \                                                 /
    =================================================
                                                        \
                                                        \
                                                            ^__^
                                                            (oo)\_______
                                                            (__)\       )\/
                                                                ||     ||
    STORED

    $ tg cow
    _________________________________________________
    /                                                 \
    | What is love?... Baby don't hurt me... don't hurt |
    | me... no moo                                      |
    \                                                 /
    =================================================
                                                        \
                                                        \
                                                            ^__^
                                                            (oo)\_______
                                                            (__)\       )\/
                                                                ||     ||
    ```
* Store/Retrieve Unicode

    ```bash
    # Store the value
    $ tg put tilde-n --value ñ
    STORED

    # Retrieve the value
    $ tg tilde-n

    ñ
    ```

* Search all Key/Values

    *This feature requires [fzf](https://github.com/junegunn/fzf)*

    ![Search Example in resources folder](https://raw.githubusercontent.com/oakhan3/tget/master/resources/search-example.png)


* See all Values

    ```bash
    $ tg ls

    pyv3
    ----------------------------------------
    pyenv virtualenv 3.6.4 $NAME && pyenv activate $NAME


    feels
    ----------------------------------------
    👻 👽 🤖 💩


    abra
    ----------------------------------------
    cadabra
    ```

* Delete by Key

    ```bash
    $ tg del pyv3

    The following was deleted:

    Key: pyv3

    Value:
    pyenv virtualenv 3.6.4 $NAME && pyenv activate $NAME
    ```

## Notes

* Currently only supports Unix-like Operating Systems.
* Values are stored as plain-text so this is NOT a tool to store any form of sensitive data like passwords.
* Data is stored and retrieved from a json-file - don't expect to store/retrieve any form of large data reliably or with high performance.
* You can find the stored values in a json file located at `~/.tget/store.json`

## Coming soon

* configuration
* Interactive deleter
* `upgrade` command
* `import`, `export` commands
* `uninstall` command
