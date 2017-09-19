# Notes

On Mac OS X, install ansible in the venv with this and then the requirements:

```sh
pip install ansible==2.3.2.0
pip install docker-py
export CPPFLAGS="-I/usr/local/opt/openssl/include -I$(xcrun --show-sdk-path)/usr/include/sasl"
export LDFLAGS=-L/usr/local/opt/openssl/lib
#pip install --global-option=build_ext --global-option="-L/usr/local/opt/openssl/lib" --global-option="-I/usr/local/opt/openssl/include" --global-option="-I$(xcrun --show-sdk-path)/usr/include/sasl" -r requirements/requirements.txt
pip install -r requirements/requirements.txt
```

The playbook is run like this:

```sh
ansible-playbook -i inventory install.yml -e no_proxy=yes  -e awx_version=1.0.0
```

If needed install libxmlsec1:

```sh
brew install libxmlsec1
```

See [Mac install fails with fatal error: 'openssl/opensslv.h' file not found (tried previous instructions) · Issue #3489 · pyca/cryptography](https://github.com/pyca/cryptography/issues/3489) for further details and hints.