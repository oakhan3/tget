# tget

A super mini-utility to store and retrieve random snippets in your terminal!

## install

    curl http://raw.githubusercontent.com/oakhan3/tget/master/install | python

It's simple...

## put something

    $ tg put
    Key: abra
    Value: (Hit <ENTER> twice to end input)

    cadabra

    STORED

## get something

    $ tg abra

    cadabra

## see all the things

    $ tg ls

    cow
    ----------------------------------------
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


    feels
    ----------------------------------------
    👻 👽 🤖 💩


    abra
    ----------------------------------------
    cadabra

## delete something

    $ tg del abra

    The following value (with key `abra`) was deleted:

    cadabra

## extra goodies:

### multi-line value support

    $ tg put
    Key: cow
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

### unicode support

    $ tg put
    Key: feels
    Value: (Hit <ENTER> twice to end input)

    👻 👽 🤖 💩

    STORED

    $ tg feels

    👻 👽 🤖 💩

### quick-put

    $ tg put --key hello --value world
    STORED

## but why?

Personally, because I found myself storing snippets of commands, code and unicode in random files, gists or the terminals reverse search, only to lose it or forget how or why I stored it there.

Some examples:

* Cryptic `sed` commands I would pipe log streams into:

      $ tg sed-nl

      | sed -i 's/\\n/\n/g'

* Unicode!

      $ tg squiggly-n

      ñ

* Arbritary things I would google EVERYTIME otherwise

      $ tg pg-uri

      postgresql://user:password@host:port/dbname

* Project specific things that don't warrant their own aliases and tend to get lost in reverse history

      $ `tg dru-log`  // This evaluates "docker-compose logs --tail 15 -f under-dg-rabbit"
      ...
      under-dg-rabbit_2  |  completed with 3 plugins.
      under-dg-rabbit_2  | 2018-03-03 14:02:01.377 [info] <0.5.0> Server startup complete; 3 plugins   started.
      under-dg-rabbit_1  |  * rabbitmq_management
      under-dg-rabbit_1  |  * rabbitmq_web_dispatch
      under-dg-rabbit_3  |  * rabbitmq_management_agent
      ...

## coming soon

* configuration
* Interactive deleter
* `ls` sort
* `ls` search
