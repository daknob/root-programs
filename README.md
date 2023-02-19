# WebPKI Root Programs

This repository includes a list of WebPKI Root Programs or Trust Stores that
are being used by software or hardware out there. Associated tools may also be
added to help with automation.

When a new Root CA is created, it is often difficult and can take many (5+)
years until it is trusted in enough places for it to be self-sufficient and
autonomous. In the meantime, the operators need to hunt down and apply to every
Root Program and every Trust Store out there, and get in as early as possible.

Since a lot of devices don't receive updates to this list of Root CAs, or even
to anything at all, the earlier the CA is added, the more devices will ship
trusting it. For the rest, natural attrition would have to take over, and old
devices that don't include these certificates would have to reach the end of
their life.

Some of these Trust Stores listed here need manual applications, so even some
old Root CAs (closing to a decade of age, or more) aren't included. The age of
the Root CA does not guarantee inclusion, and it's usually up to the operators
to do a good work.

As there's no authoritative list out there, this repository aims to aggregate
all Root Programs and Trust Stores in a single location, to act as a checklist
for CAs when they generate new certificates. Especially with the direction
things are heading towards, with short-lived Root CAs, this will prove
especially useful in the future.

## Root Programs

Root Programs are fully-managed programs for CAs to apply to. They come with a
list of requirements, obligations, etc. and there is a lot of involvement that
is typically required to participate.

| Name | Policy | Application | List of CAs |
|------|--------|-------------|-------------|
| Apple Root Certificate Program | [Link](https://www.apple.com/certificateauthority/ca_program.html) | [Link](https://www.apple.com/certificateauthority/ca_program.html) | [Link](https://support.apple.com/en-us/HT209143) |
| Chrome Root Program | [Link](https://g.co/chrome/root-policy) | [Link](https://www.chromium.org/Home/chromium-security/root-ca-policy/apply-for-inclusion/) | [Link](https://g.co/chrome/root-store) |
| Mozilla CA Certificate Program | [Link](https://wiki.mozilla.org/CA) | [Link](https://wiki.mozilla.org/CA/Application_Process) | [Link](https://wiki.mozilla.org/CA/Included_CAs) |
| Microsoft Trusted Root Program | [Link](https://learn.microsoft.com/en-us/security/trusted-root/program-requirements) | [Link](https://learn.microsoft.com/en-us/security/trusted-root/new-ca-application) | [Link](https://learn.microsoft.com/en-us/security/trusted-root/participants-list) |
| Oracle Java SE | [Link](https://www.oracle.com/java/technologies/javase/carootcertsprogram.html) | [Link](https://www.oracle.com/java/technologies/javase/carootcertsprogram.html) | `$ keytool -list -cacerts -storepass changeit`[^java] |
| Adobe Approved Trust List[^aatl] | [Link](https://helpx.adobe.com/acrobat/kb/approved-trust-list2.html) | [Link](https://helpx.adobe.com/acrobat/kb/approved-trust-list2.html) | [Link](https://helpx.adobe.com/acrobat/kb/approved-trust-list1.html) |

## Trust Stores

Trust Stores here are lists of Root CAs that are trusted by a software or
hardware vendor or product. They may not have an entire program behind them,
but often require acceptance in a Root Program for inclusion. Usually these are
subsets of the certificates of a Root Program, e.g. due to storage constraints
in IoT devices, etc. It is recommended to attempt inclusion in as many as
possible, as they tend to be used in devices and services that may not receive
updates.

| Name | Info | Application | List of CAs |
|------|------|-------------|-------------|
| Gmail S/MIME[^gmail] | [Link](https://support.google.com/a/answer/7448393?hl=en) | N/A | [Link](https://support.google.com/a/answer/7448393?hl=en) |

## Footnotes

[^java]: Each Java version and edition comes with its own list of certificates.
This is also different per JRE, so OpenJDK has a different list than Oracle JDK,
etc. Moreover, some OSes have separate packages, independent of Java, such as
the [`ca-certificates-java`](https://packages.debian.org/stable/ca-certificates-java)
on Debian / Ubuntu. Applying to the Oracle Root Program will eventually and
hopefully trickle down to all other Java Runtimes / Environments / Editions /
OSes / ... but there's no guarantee. Java remains a painpoint for all WebPKI
CAs to date.

[^aatl]: This is mainly used for Document Signing, and not for TLS Server or
Client certificates.

[^gmail]: This is used for S/MIME certificates sent and received by Gmail. This
is not used for TLS Server or Client certificates (e.g. SMTP or IMAP).
