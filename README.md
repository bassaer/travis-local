# travis-local

## setup docker on centos

cf. https://medium.com/google-developers/how-to-run-travisci-locally-on-docker-822fc6b2db2e

```
travis@c600e543a8f1:~/builds/bassaer/travis-local$ diff -u <(travis compile) ci.sh
detected repository as bassaer/travis-local
--- /dev/fd/63	2019-02-18 14:01:49.294254972 +0000
+++ ci.sh	2019-02-18 13:52:12.693095414 +0000
@@ -991,7 +991,7 @@

 travis_fold start git.checkout
   if [[ ! -d bassaer/travis-local/.git ]]; then
-    travis_cmd git\ clone\ --depth\=50\ --branch\=\'\'\ https://github.com/bassaer/travis-local.git\ bassaer/travis-local --echo --retry --timing
+    travis_cmd git\ clone\ --depth\=50\ --branch\=\dev\ https://github.com/bassaer/travis-local.git\ bassaer/travis-local --echo --retry --timing
     if [[ $? -ne 0 ]]; then
       echo -e "\033[31;1mFailed to clone from GitHub.\033[0m"
       echo -e "Checking GitHub status (https://status.github.com/api/last-message.json):"
```


## run

```
travis@c600e543a8f1:~/builds/bassaer/travis-local$ bash ci.sh
Build system information
Build language: python
Build id: ''
Job id: ''
Runtime kernel version: 3.10.0-957.1.3.el7.x86_64
Build image provisioning date and time
Thu Feb  5 15:09:33 UTC 2015
Operating System Details
Distributor ID:	Ubuntu
Description:	Ubuntu 12.04.5 LTS
Release:	12.04
Codename:	precise
Linux Version
3.13.0-29-generic
Cookbooks Version
a68419e https://github.com/travis-ci/travis-cookbooks/tree/a68419e
GCC version
gcc (Ubuntu/Linaro 4.6.3-1ubuntu5) 4.6.3
Copyright (C) 2011 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

LLVM version
clang version 3.4 (tags/RELEASE_34/final)
Target: x86_64-unknown-linux-gnu
Thread model: posix
Pre-installed Ruby versions
ruby-1.9.3-p551
Pre-installed Node.js versions
v0.10.36
Pre-installed Go versions
1.4.1
Redis version
redis-server 2.8.19
riak version
2.0.2
MongoDB version
MongoDB 2.4.12
CouchDB version
couchdb 1.6.1
Neo4j version
1.9.4
RabbitMQ Version
3.4.3
ElasticSearch version
1.4.0
Installed Sphinx versions
2.0.10
2.1.9
2.2.6
Default Sphinx version
2.2.6
Installed Firefox version
firefox 31.0esr
PhantomJS version
1.9.8
ant -version
Apache Ant(TM) version 1.8.2 compiled on December 3 2011
mvn -version
Apache Maven 3.2.5 (12a6b3acb947671f09b81f49094c53f426d8cea1; 2014-12-14T17:29:23+00:00)
Maven home: /usr/local/maven
Java version: 1.7.0_76, vendor: Oracle Corporation
Java home: /usr/lib/jvm/java-7-oracle/jre
Default locale: en_US, platform encoding: ANSI_X3.4-1968
OS name: "linux", version: "3.13.0-29-generic", arch: "amd64", family: "unix"

Timeout waiting for network availability.
sed: cannot rename /etc/hosts: Device or resource busy

$ git -C bassaer/travis-local fetch origin
$ git -C bassaer/travis-local reset --hard
HEAD is now at 65d5888 Revert "Revert "hoge""
$ cd bassaer/travis-local
$ git checkout -qf

$ source ~/virtualenv/python2.7/bin/activate
$ python --version
Python 2.7.9
$ pip --version
pip 6.0.7 from /home/travis/virtualenv/python2.7.9/lib/python2.7/site-packages (python 2.7)
Could not locate requirements.txt. Override the install: key in your .travis.yml to install dependencies.
$ echo 'start'
start
The command "echo 'start'" exited with 0.

$ if [ "$TRAVIS_PULL_REQUEST" == "false" ]; then hostname; fi
c600e543a8f1
The command "if [ "$TRAVIS_PULL_REQUEST" == "false" ]; then hostname; fi" exited with 0.



Done. Your build exited with 0.
```
