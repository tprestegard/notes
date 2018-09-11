# Random useful notes

## Django

* Get a count of most related objects:

  ```python
  [('{0}.{1}'.format(f.related_model._meta.app_label, f.related_model.__name__), getattr(tp, f.get_accessor_name()).count()) for f in tp._meta.get_fields() if (f.is_relation and f.one_to_many)]
  ```

## Shell
* Query the LDAP:
  ```
  ldapsearch -t -LLL -x -b "dc=ligo,dc=org" -H ldaps://ldap.ligo.org uid=tanner.prestegard
  ```
