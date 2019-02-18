# travis-local

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
