CA Root Certificates
====================

Which certificates do I need?
#############################

* In most browsers, you probably only need to "Browser Import" the Root certificate (trusting it to sign web certificates) into the Trusted Roots section of your certificate store and you'll then be able to access websites whose certificates are signed by our eScience CAs.
* In other browsers (IE8 and IE9 for instance) you may also have to "Browser Import" the two eScience CA certificates (2A and 2B) into the Intermediate Certification Authorities section. Indeed on Windows 7 that still might not be enough and you may have to individually add exceptions to your trusted sites as well (depending what security level you have engaged).
* If the hashed names confuse you, don't worry: they are for different versions of OpenSSL (see FAQ below), or for tools based on OpenSSL.
* If you require a package install for the non-IGTF certificates then please go to our `CA repository server <https://cert.ca.ngs.ac.uk/latest/>`_.
* We no longer provide package installs for our IGTF-accredited UK eScience CA Certificates, but they are available from the `EUGridPMA <https://dist.eugridpma.info/distribution/igtf/current/accredited/RPMS/>`_ repository

IGTF-accredited UK eScience CA Certificates
###########################################
+--------------------------------------------------------------------+-------------------------------------------------------------------------------------------------+--------------------------------------------------------+
| Certificate for Importing into a Browser                           | Certificate Distinguished Name (DN)                                                             | Certificate Revocation List                            |
+--------------------------------------------------------------------+-------------------------------------------------------------------------------------------------+--------------------------------------------------------+
|                                                                    | SHA1 Fingerprint                                                                                |                                                        |
+--------------------------------------------------------------------+-------------------------------------------------------------------------------------------------+--------------------------------------------------------+
|                                                                    | SHA256 Fingerprint                                                                              |                                                        |
+====================================================================+=================================================================================================+========================================================+
| `UK e-Science Root <https://cert.ca.ngs.ac.uk/escience-root.cer>`_ | /C=UK/O=eScienceRoot/OU=Authority/CN=UK e-Science Root                                          | `Root CRL <http://crl.ca.ngs.ac.uk/crl/root-crl.der>`_ |
+--------------------------------------------------------------------+-------------------------------------------------------------------------------------------------+--------------------------------------------------------+
|                                                                    | A1:39:B0:F3:04:6C:0B:F9:F5:0A:1B:33:00:06:4F:83:6B:7D:4F:3E                                     |                                                        |
+--------------------------------------------------------------------+-------------------------------------------------------------------------------------------------+--------------------------------------------------------+
|                                                                    | 53:87:A6:41:C8:FC:F7:2C:81:00:78:72:C9:6E:4C:AE:AB:11:0A:A9:4A:EC:92:CB:CB:B0:C4:77:93:F5:24:7F |                                                        |
+--------------------------------------------------------------------+-------------------------------------------------------------------------------------------------+--------------------------------------------------------+
| `UK e-Science CA 2B <https://cert.ca.ngs.ac.uk/escience2b.cer>`_   | /C=UK/O=eScienceCA/OU=Authority/CN=UK e-Science CA 2B                                           | `2B CRL <http://crl.ca.ngs.ac.uk/crl/escience2b.crl>`_ |
+--------------------------------------------------------------------+-------------------------------------------------------------------------------------------------+--------------------------------------------------------+
|                                                                    | DB:D9:5A:B4:E9:AD:74:26:E0:33:68:AA:B1:77:CC:5B:64:B2:CB:0E                                     |                                                        |
+--------------------------------------------------------------------+-------------------------------------------------------------------------------------------------+--------------------------------------------------------+
|                                                                    | 17:12:91:F6:D0:2A:86:B5:AF:9E:E2:F3:91:AA:6A:0F:CE:17:71:B0:CB:C3:65:56:31:7D:9A:9F:50:A8:35:32 |                                                        |
+--------------------------------------------------------------------+-------------------------------------------------------------------------------------------------+--------------------------------------------------------+

Frequently Asked Questions
##########################

Q: Why all these certificates?

The CA certificates sign certificates for different types of user.

Q: What is the hash and why are there two of them?

They are used by OpenSSL - and tools built on OpenSSL - to discover the issuer of a given certificate. OpenSSL changed the way they hash certificates as of version 1.0.0. If your server uses openssl 0.9.X then use the names files in that common, likewise for 1.0.Y. You can check which version of openssl you have with the command:

.. code-block:: shell-session

    openssl version

Note that their respective contents are identical, but we provide both so you don't need to rename files after download.

Q: What are the SHA-1 fingerprints?

These can be used to prove that the certificate you have received is the correct one. Note that you also have to trust the source of the fingerprint which is why they should be provided on different servers. The example below shows that the two eScience Root CA files are for the same certificate

.. code-block:: shell-session

    $ # openssl v0.9.X
    $ openssl x509 -in 98ef0ee5.0 -noout -fingerprint -sha1
    SHA1 Fingerprint=A1:39:B0:F3:04:6C:0B:F9:F5:0A:1B:33:00:06:4F:83:6B:7D:4F:3E

.. code-block:: shell-session

    $ # openssl v1.0.Y
    $ openssl x509 -in 7ed47087.0 -noout -fingerprint -sha1
    SHA1 Fingerprint=A1:39:B0:F3:04:6C:0B:F9:F5:0A:1B:33:00:06:4F:83:6B:7D:4F:3E


