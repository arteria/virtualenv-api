virtualenv-api - an API for virtualenv
======================================

[virtualenv](http://www.virtualenv.org/) is a tool to create isolated Python
environments.  Unfortunately, it does not expose a native Python API. This
package aims to provide an API in the form of a wrapper around virtualenv.

It can be used to create and delete environments and perform package management
inside the environment.

Examples
--------

* To begin managing an environment (it will be created if it does not exist):

```python
from virtualenv.manage import VirtualEnvironment
env = VirtualEnvironment('/path/to/environment/name')
```

* Check if the `mezzanine` package is installed:

```python
>>> env.is_installed('mezzanine')
False
```

* Install the latest version of the `mezzanine` package:

```python
>>> env.install('mezzanine')
```

* Install version 1.4 of the `django` package (this is pip's syntax):

```python
>>> env.install('django==1.4')
```

* Upgrade the `django` package to the latest version:

```python
>>> env.upgrade('django')
```

* Uninstall the `mezzanine` package:

```python
>>> env.uninstall('mezzanine')
```

* A package may be installed directly from a git repository (must end with `.git`):

```python
>>> env.install('git+git://github.com/sjkingo/cartridge-payments.git')
```

* Instances of the environment provide an `installed_packages` property:

```python
>>> env.installed_packages
[('django', '1.5'), ('wsgiref', '0.1.2')]
```

* A list of package names is also available in the same manner:

```python
>>> env.installed_package_names
['django', 'wsgiref']
```

Verbose output from each command is available in the environment's `build.log`
file, which is appended to with each operation.
