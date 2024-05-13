# Dockerized IMAP server

IMAP server for debugging.

Now built on Ubuntu 22.04

This docker image is based on https://github.com/tomav/docker-mailserver
If you look for a docker image for production environment, then go here:
https://hub.docker.com/r/tvial/docker-mailserver/

This image is even simpler than `tvial` docker image. Includes only 
Postfix (SMTP) and Dovecot (IMAP) servers with one catchall mailbox 

Every email received via SMTP will be delivered locally to given mailaddress

Using your favorite email client you can connect via IMAP protocol to see emails like original recipient would received them


## Run container with docker compose

```
cp docker-compose.yml.dist docker-compose.yml
```

Edit ```docker-compose.yml``` for set these environment variables:

- MAILNAME: Mail domain (by default, `localdomain.test`)
- MAIL_ADDRESS: catchall user mailbox email address
- MAIL_PASS: catchall user mailbox password

```
docker-compose up
```

Configure your email client with these parameters and test it sending 
any email to any email address 

### Catch all mailbox


- **IMAP server:** `imap`
- **IMAP encryption:** `SSL`
- **IMAP port:** `993`
- **IMAP username:** `address@example.org` (change `address@example.org` by your `MAIL_ADDRESS`)
- **IMAP password:** `pass` (change `pass` by your `MAIL_PASS`)

- **SMTP server:** `imap`
- **SMTP encryption:** `No`
- **SMTP port:** `25`
- **SMTP authentication:** `none`

