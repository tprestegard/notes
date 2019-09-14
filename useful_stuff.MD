# Random useful notes

## Sharing a tmux session
tmux -S /tmp/shareds new -s shared

## Django

* Get a count of most related objects:

  ```python
  [('{0}.{1}'.format(f.related_model._meta.app_label, f.related_model.__name__), getattr(user, f.get_accessor_name()).count()) for f in user._meta.get_fields() if (f.is_relation and f.one_to_many)]
  ```

## Shell
* Query the LDAP:
  ```
  ldapsearch -t -LLL -x -b "dc=ligo,dc=org" -H ldaps://ldap.ligo.org uid=tanner.prestegard
  ```
* Query for robot accounts:
  ```
  ldapsearch -LLL -x -Z -b "ou=robot,dc=ligo,dc=org" -H ldap://ldap.ligo.org
  ```
* Remove configuration files for removed packages:
  ```
  dpkg --list |grep "^rc" | cut -d " " -f 3 | xargs sudo dpkg --purge
  ```

## Pytest
* Run all tests in a specific module: `python setup.py pytest --addopts /path/to/file.py`
* Run all tests under a specific class in a module: `python setup.py pytest --addopts /path/to/file.py::TestClass`
* Run one test under a specific class in a module: `python setup.py pytest --addopts /path/to/file.py::TestClass::test_name`

* Stop with pdb when an error occurs `python setup.py pytest --addopts --pdb`
* Stop with ipdb when an error occurs `python setup.py pytest --addopts --pdbcls=IPython.terminal.debugger:TerminalPdb` (doesn't seem to work)
* Current ipdb solution:
  * Put a breakpoint in the code with `import ipdb; ipdb.set_trace()`
  * Run tests with `python setup.py pytest --addopts -s`
  * Tests will run, but a "super" error will be printed at the end of the run.

* To do both: `python setup.py pytest --addopts "/path/to/file.py -s"


## Kubectl
* See all containers: `kubectl get pods`
* Enter a container: `kubectl exec -ti gracedb-7875c769c4-k5wnc -- /bin/bash -l`
* Follow logs with grep: `kubectl logs -f gracedb-69cc59c574-8gmbl | grep 'kube-probe'`
* Restart a container: `kubectl patch deployment -n gracedb gracedb -p "{\"spec\":{\"template\":{\"metadata\":{\"labels\":{\"date\":\"`date +'%s'`\"}}}}}"`
