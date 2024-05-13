# Dockerized Postfix/Dovecut server

Mail server with one catchall account

Built on Ubuntu 22.04

This docker image is based on https://github.com/tabascoterrier/docker-imap-devel

This image is even simpler than `tabascoterrier` docker image. Includes only 
Postfix (SMTP) and Dovecot (IMAP) servers with one catchall mailbox 

Every email received via SMTP will be delivered locally to given mailaddress

Using your favorite email client you can connect via IMAP protocol to see emails like original recipient would received them


## Run container with docker compose

Edit ```docker-compose.yml``` for set these environment variables:

- MAIL_DOMAIN: Mail domain (by default, `localdomain.test`)
- MAIL_ALIAS: catchall user mailbox email address (MAIL_ALIAS@MAIL_DOMAIN)
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
- **IMAP username:** `address@example.org` (change `address@example.org` by your `MAIL_ALIAS@MAIL_DOMAIN`)
- **IMAP password:** `pass` (change `pass` by your `MAIL_PASS`)

- **SMTP server:** `imap`
- **SMTP encryption:** `No`
- **SMTP port:** `25`
- **SMTP authentication:** `none`

