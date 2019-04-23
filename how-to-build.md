
# Build

```

yum install -y wget gcc make perl 
# autoconf automake libtool
mkdir ~/download
cd ~/download
wget https://www.zlib.net/zlib-1.2.11.tar.gz
tar -xzvf zlib-1.2.11.tar.gz
cd zlib-1.2.11
./configure --prefix=/usr/local/zlib
make
make install

cd ~/download
wget https://github.com/openssl/openssl/archive/OpenSSL_1_1_1b.tar.gz
tar -xzvf OpenSSL_1_1_1b.tar.gz
cd openssl-OpenSSL_1_1_1b
./config --prefix=/usr/local/openssl --openssldir=/usr/local/openssl
make
make install

cd ~/download
wget https://github.com/curl/curl/releases/download/curl-7_64_1/curl-7.64.1.tar.gz
tar -xzvf curl-7.64.1.tar.gz
cd curl-7.64.1
./configure \
  --prefix=/usr/local/curl --enable-shared \
  --with-ssl=/usr/local/openssl --with-zlib=/usr/local/zlib \
  --without-nss

make
make install

# Make Symbols
sed -i -e 's/libcurl.so.4/libcurl.so.f/g' /usr/local/curl/bin/curl
sed -i -e 's/libcurl.so.4/libcurl.so.f/g' /usr/local/curl/bin/curl-config

ln -s /usr/local/curl/lib/libcurl.so.4.5.0 /usr/lib64/libcurl.so.f

mv /usr/bin/curl /usr/bin/curl.org
if [ -f "/usr/bin/curl-config" ]; then mv /usr/bin/curl-config /usr/bin/curl-config.org; fi
ln -s /usr/local/curl/bin/curl /usr/bin/curl
ln -s /usr/local/curl/bin/curl-config /usr/bin/curl-config

ln -s /usr/local/openssl/lib/libssl.so.1.1 /usr/lib64/libssl.so.1.1
ln -s /usr/local/openssl/lib/libcrypto.so.1.1 /usr/lib64/libcrypto.so.1.1

```

# Remove

```

rm -f /usr/lib64/libssl.so.1.1 /usr/lib64/libcrypto.so.1.1  /usr/lib64/libcurl.so.f
rm -f /usr/bin/curl /usr/bin/curl-config
mv /usr/bin/curl.org /usr/bin/curl
if [ -f "/usr/bin/curl-config.org" ]; then mv /usr/bin/curl-config /usr/bin/curl-config.org; fi


```
