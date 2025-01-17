# CentOS 5.11 (archive vault)

Since 31 Mar 2017, CentOS 5 is not supported any more.
If you run a container using ```centos:5``` image, ```yum``` will not work.

tlsv1 is not accpted by vault repository, if you use vault repository, yum upadte will fail with error: ```M2Crypto.SSL.SSLError: tlsv1 alert protocol version.```

### YUM Repository

* Disable fastmirror plugin.
* Set ```baseurl``` of repos to http://archive.kernel.org/centos-vault/5.11/. (base, extras, updates)

## Usage

1. Replace <code>CentOS-Base.repo</code> in <code>/etc/yum.repos.d/</code>
2. Edit <code>/etc/yum/pluginconf.d/fastestmirror.conf</code> and put <code>enabled=0</code>

3. Execute:
```shell
rm -rf /var/cache/yum/*
yum clean all
yum makecache
yum update
```

## Usage with docker

Use in command-line.

```
docker run --rm -it lazywalker/centos5 /bin/bash
```

Or, replacement for centos:5 in Dockerfile

```
FROM lazywalker:centos5
```
