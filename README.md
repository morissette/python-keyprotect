# python-keyprotect

[![Build Status](https://travis-ci.org/locke105/python-keyprotect.svg?branch=master)](https://travis-ci.org/locke105/python-keyprotect)
[![Apache License](http://img.shields.io/badge/license-APACHE2-blue.svg)](https://www.apache.org/licenses/LICENSE-2.0.html)

A Pythonic client for IBM Key Protect

# Usage

```python
import keyprotect
from keyprotect import bxauth

service_id="..."

tokens = bxauth.auth(apikey="...")
iam_token = tokens.get('access_token')

kp = keyprotect.Keys(iamtoken=iam_token, instance_id=service_id)
for key in kp.index():
    print("%s\t%s" % (key['id'], key['name']))

key = kp.create(name="MyTestKey")
print("Created key '%s'" % key['id'])

kp.delete(key.get('id'))
print("Deleted key '%s'" % key['id'])
```
