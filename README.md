Fcash Core integration/staging tree
=====================================

[![Build Status](https://travis-ci.org/fcash-project/fcash-core.svg?branch=master)](https://travis-ci.org/fcash-project/fcash-core)

https://www.fcash.cash/

What is Fcash coin?
----------------

Fcash is an experimental digital currency that enables instant payments to
anyone, anywhere in the world. Fcash uses peer-to-peer technology to operate
with no central authority: managing transactions and issuing money are carried
out collectively by the network. Fcash Core is the name of open source
software which enables the use of this currency.

For more information, as well as an immediately useable, binary version of
the Fcash Core software, see [https://www.fcash.cash/](https://www.fcash.cash/). 

License
-------

Fcash Core is released under the terms of the MIT license. See [COPYING](COPYING) for more
information or see https://opensource.org/licenses/MIT.

Development Process
-------------------

The `master` branch is regularly built and tested, but is not guaranteed to be
completely stable. [Tags](https://github.com/fcash-project/fcash-core/tags) are created
regularly to indicate new official, stable release versions of Fcash Core.

The contribution workflow is described in [CONTRIBUTING.md](CONTRIBUTING.md).

The developer [mailing list](https://groups.google.com/forum/#!forum/fcash-dev)
should be used to discuss complicated or controversial changes before working
on a patch set.

Developer IRC can be found on Freenode at #fcash-dev.

Testing
-------

Testing and code review is the bottleneck for development; we get more pull
requests than we can review and test on short notice. Please be patient and help out by testing
other people's pull requests, and remember this is a security-critical project where any mistake might cost people
lots of money.

### Automated Testing

Developers are strongly encouraged to write [unit tests](src/test/README.md) for new code, and to
submit new unit tests for old code. Unit tests can be compiled and run
(assuming they weren't disabled in configure) with: `make check`. Further details on running
and extending unit tests can be found in [/src/test/README.md](/src/test/README.md).

There are also [regression and integration tests](/test), written
in Python, that are run automatically on the build server.
These tests can be run (if the [test dependencies](/test) are installed) with: `test/functional/test_runner.py`

The Travis CI system makes sure that every pull request is built for Windows, Linux, and OS X, and that unit/sanity tests are run automatically.

### Manual Quality Assurance (QA) Testing

Changes should be tested by somebody other than the developer who wrote the
code. This is especially important for large or high-risk changes. It is useful
to add a test plan to the pull request description if testing the changes is
not straightforward.

Translations
------------

We only accept translation fixes that are submitted through [Bitcoin Core's Transifex page](https://www.transifex.com/projects/p/bitcoin/).
Translations are converted to Fcash periodically.

Translations are periodically pulled from Transifex and merged into the git repository. See the
[translation process](doc/translation_process.md) for details on how this works.

**Important**: We do not accept translation changes as GitHub pull requests because the next
pull from Transifex would automatically overwrite them again.


Minerd
------------
./minerd -o http://127.0.0.1:9527 -u fcashuser -p fcashpass --coinbase-addr=FmzbxxPxvBWUEWnswPV86G75BsbVogxVdw -t 1 -D -P
./minerd -o 127.0.0.1:9527 --user=fcashuser --pass=fcashpass --coinbase-addr=FnnSwMe26WJZTMkJ2jf9HcjaG6uL12SkvZ -t 1 -D -P
./minerd -o 127.0.0.1:9527 --user=fcashuser --pass=fcashpass --coinbase-addr=FnnSwMe26WJZTMkJ2jf9HcjaG6uL12SkvZ

./minerd -a scrypt -o 127.0.0.1:9527 --user=fcashuser --pass=fcashpass -t 1 -D --no-stratum --no-longpoll --no-getwork --coinbase-addr=FnnSwMe26WJZTMkJ2jf9HcjaG6uL12SkvZ

./minerd -a scrypt -o 127.0.0.1:9527 -O fcashuser:fcashpass

curl --user fcashuser:fcashpass --data-binary '{"method": "getblocktemplate", "params": [{"capabilities": ["coinbasetxn", "coinbasevalue", "longpoll", "workid"]}], "id":0}' -H 'content-type: text/plain;' http://127.0.0.1:9528


addnode
------------
./src/fcash-cli addnode "139.162.67.34:9528" "add"
./src/fcash-cli addnode "59.110.9.93:9528" "add"
./src/fcash-cli addnode "60.205.0.142:9528" "add"

./src/fcash-cli getaddednodeinfo
