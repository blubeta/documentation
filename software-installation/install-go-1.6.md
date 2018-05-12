# Install Go v 1.6 on Ubuntu 14.04

`sudo aptitude update`

`sudo curl -O https://storage.googleapis.com/golang/go1.6.linux-amd64.tar.gz`

`sudo tar -xvf go1.6.linux-amd64.tar.gz`

`sudo mv go /usr/local`

# Set Correct User Path

* Open your `~/.profile` and add:

`export PATH=$PATH:/usr/local/go/bin`

# Install [Caddy][https://github.com/mholt/caddy#getting-caddy]

```
cd /opt/
wget https://github.com/mholt/caddy/releases/download/v0.8.2/caddy_linux_amd64.tar.gz
tar -xvzf caddy_linux_amd64.tar.gz
mv caddy_linux_amd64/caddy /usr/local/bin/caddy
```
