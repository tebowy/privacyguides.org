---
title: Email Security
icon: material/email
---

## Email Encryption Overview

### What is end-to-end encryption (E2EE) in email?

E2EE is a way of encrypting email contents so that nobody but the recipient(s) can read the email message.

### How can I encrypt my email?

The standard way to do email E2EE and have it work between different email providers is with OpenPGP. There are different implementations of the OpenPGP standard, the most common being [GnuPG](https://en.wikipedia.org/wiki/GNU_Privacy_Guard) and [OpenPGP.js](https://openpgpjs.org).

There is another standard that was popular with business called [S/MIME](https://en.wikipedia.org/wiki/S/MIME), however it requires a certificate issued from a [Certificate Authority](https://en.wikipedia.org/wiki/Certificate_authority) (not all of them issue S/MIME certificates). It has support in [Google Workplace](https://support.google.com/a/topic/9061730?hl=en&ref_topic=9061731) and [Outlook for Web or Exchange Server 2016, 2019](https://support.office.com/en-us/article/encrypt-messages-by-using-s-mime-in-outlook-on-the-web-878c79fc-7088-4b39-966f-14512658f480).

### What software can I use to get E2EE?

Email providers which allow you to use standard access protocols like IMAP and SMTP can be used with any of the [email clients we recommend](email-clients.md). This can be less secure as you are now relying on email providers to ensure that their encryption implementation works and has not been compromised in anyway.

### How do I protect my private keys?

A smartcard (such as a [Yubikey](https://support.yubico.com/hc/en-us/articles/360013790259-Using-Your-YubiKey-with-OpenPGP) or [Nitrokey](https://www.nitrokey.com)) works by receiving an encrypted email message from a device (phone, tablet, computer etc) running an email/webmail client. The message is then decrypted by the smartcard and the decrypted content is sent back to the device.

It is advantageous for the decryption to occur on the smartcard so as to avoid possibly exposing your private key to a compromised device.

## Email Metadata Overview

### Who can see the email metadata?

Email metadata is able to be seen by your email client software (or webmail) and any servers relaying the message from you to any recipients. Sometimes email servers will also use external parties to protect against spam.

### What is email metadata?

Email software will often show some visible headers that you may have seen such as: `To`, `From`, `Cc`, `Date`, `Subject`.

### When is email metadata used?

Client software may use it to show who a message is from and what time it was received. Servers may use it to determine where an email message must be sent, among [other purposes](https://en.wikipedia.org/wiki/Email#Message_header) which are not always transparent.

### Where is the email metadata?

Email metadata is stored in the [message header](https://en.wikipedia.org/wiki/Email#Message_header) of the email message.

### Why can't email metadata be E2EE?

Email metadata is crucial to the most basic functionality of email (where it came from, and where it has to go). E2EE was not built into the email protocols originally and is also optional, therefore, only the message content is protected.

### How is my metadata protected?

When emails travel between email providers an encrypted connection is negotiated using [Opportunistic TLS](https://en.wikipedia.org/wiki/Opportunistic_TLS). This protects the metadata from outside observers, but as it is not E2EE, server administrators can snoop on the metadata of an email.
