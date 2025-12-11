# 📨 Mail Stack Architecture (cplugin.io)

## Components
- **MTA**: Postfix (submission, relay, virtual domains)
- **MDA/IMAP**: Dovecot (Maildir at /var/mail/%u/Maildir, virtual users)
- **Auth**: OpenLDAP (ou=users,dc=cplugin,dc=com, bind via cn=admin,dc=cplugin,dc=com)
- **Filtering**: Rspamd (DKIM signing, multimap, Bayesian, custom rules for Yahoo/Gmail)
- **Security**: TLS (Let's Encrypt + internal CA), SASL (SCRAM-SHA-256)

## UID/GID Policy
- Virtual mail user: UID 911, GID 911  
- Maildir owner: 911:911  
- Prevents privilege escalation & ensures SELinux compatibility.

