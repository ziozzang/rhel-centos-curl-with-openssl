# Why This?
* rhel-centos-curl-with-openssl
* Original CentOS/RHEL's curl is with NSS. it has CA issue. so i fixed it.
* Original CentOS/RHEL curl is worked badly. it doesn't work with --cacert option. :(

# Target OS.

* CentOS 7 / RHEL 7.x
* Tested on Docker (CentOS7), Baremetal (CentOS/RHEL)

# How to USE.
* Run Command

```
cd /usr/local && \
  curl https://github.com/ziozzang/rhel-centos-curl-with-openssl/raw/master/curl-new.tgz | \
  tar xz && \
  bash ./install.sh && \
  rm -f ./install.sh
```
* or untar at /usr/local and, update symbolic links.


# Code fix from..
* https://github.com/northbright/Notes/blob/master/openssl/install-latest-openssl-from-source-on-centos-7.md
* https://github.com/northbright/Notes/blob/01895da13d1ac4a82b4203b146ef2f51ca042a68/Linux/CentOS/yum/yum-failed-after-install-curl-from-source-on-centos-7.md
