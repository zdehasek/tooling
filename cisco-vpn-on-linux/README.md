# How to connect to the cisco VPN with OpenConnect on Linux

*Tested on: Ubuntu 19.10*

## Install dependencies

### Linux packages

``` 
  sudo apt install -y openconnect opensc opensc-pkcs11 gnutls-bin gconf2
```

### Cisco VPN Wrapper

To be able to use OpenConnect for the Cisco VPN server, you have to install this wrapper.
You can install it from this repo or from the origin place


Installating procedure:

```
sudo su -
mkdir /root/.cisco
cd /root/.cisco
wget https://gist.githubusercontent.com/l0ki000/56845c00fd2a0e76d688/raw/61fc41ac8aec53ae0f9f0dfbfa858c1740307de4/csd-wrapper.sh  

chmod +x csd-wrapper.sh
```

Edit the file with the vpn server:

```
CSD_HOSTNAME=vpnserver.com
```

Run the file
```
./csd-wrapper.sh  
```

## Configure SSL

```
sudo sh -c "echo 'module:/usr/lib/x86_64-linux-gnu/pkcs11/opensc-pkcs11.so' > /usr/share/p11-kit/modules/opensc.module"
```

## Find right tokens

```
p11tool --list-tokens
```

Command above will show all the tokens in your smart card, you have to find the right one which is looks limilar to this below:

```
Token 1:
	URL: pkcs11:...
	Label: ProID+ ...
	Type: Hardware token
	Flags: RNG, Requires login
	Manufacturer: Monet+,a.s.
	Model: Gemalto TOP GX4
	Serial: ...
	Module: libproidcm11.so
```

## Find the correct certificate in your smartcard

Command below will show all the certs in your smart card, you have to find the right one for connect to the VPN, as far as I know there is no better metohod then "trial and error" for this.

```
Object 0:
	URL: pkcs11:..
	Type:...
	Expires:...
	Label: ...
	ID:..
```

To the quotation marks put URL from the token you found.

```
p11tool --list-all-certs 'pkcs11:...'
```


## Connect to the smartcard


```
sudo openconnect -c 'URL_FROM_CERT' --os=win --csd-wrapper=/root/.cisco/csd-wrapper.sh VPN_URL
```

You can add servercert to aviod asking if you trust cert or not

```
--servercert
```

## GIT erver certificate verification problem 

\[TBD\]


---
## Sources:

https://askubuntu.com/questions/815145/ubuntu-16-04-openconnect-cisco-vpn-failed-to-obtain-webvpn-cookie

https://gist.github.com/l0ki000/56845c00fd2a0e76d688
