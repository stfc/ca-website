CA Certificates
===============

Which certificates do I need?
#############################

* In most browsers, you probably only need to "Browser Import" the Root certificate (trusting it to sign web certificates) into the Trusted Roots section of your certificate store and you'll then be able to access websites whose certificates are signed by our eScience CAs.
* RPM Package installs for these certificates are avaliable from the `EUGridPMA <https://dist.eugridpma.info/distribution/igtf/current/accredited/RPMS/>`_ repository

IGTF-accredited UK eScience CA Certificates
###########################################

/C=UK/O=eScienceRoot/OU=Authority/CN=UK e-Science Root
******************************************************
- Certificate for importing into your browser: `UK e-Science Root <https://cert.ca.ngs.ac.uk/escience-root.cer>`_
- `Root CRL <http://crl.ca.ngs.ac.uk/crl/root-crl.der>`_
- SHA-1 Fingerprint: ``59:7C:1A:AA:EC:65:7E:4A:F5:6A:00:1F:E2:16:44:48:96:35:DB:B1``
- SHA-256 Fingerprint: ``76:F3:A5:94:2E:22:01:2D:7E:10:E1:1B:41:6F:B2:EE:A2:1D:8F:45:83:F2:D2:FC:79:9B:D4:CE:D0:21:03:23``
- OpenSSL Certificate: `7ed47087.0 <https://cert.ca.ngs.ac.uk/7ed47087.0>`_
- Signing Policy: `7ed47087.signing_policy <http://cert.ca.ngs.ac.uk/signing_policy/7ed47087.signing_policy>`_

/C=UK/O=eScienceCA/OU=Authority/CN=UK e-Science CA 2B
*****************************************************
- Certificate for importing into your browser: `UK e-Science CA 2B <https://cert.ca.ngs.ac.uk/escience2b.cer>`_
- `2B CRL <http://crl.ca.ngs.ac.uk/crl/escience2b.crl>`_
- SHA-1 Fingerprint: ``F3:03:90:25:E1:FD:F5:9D:B9:4A:97:F2:73:97:DE:73:91:B7:E9:AB``
- SHA-256 Fingerprint: ``B6:D1:40:A7:65:D1:65:D8:91:7B:B9:94:1F:7A:B2:1F:F8:9C:04:15:5A:4D:CE:52:CA:D3:45:86:2C:3E:68:6E``
- OpenSSL Certificate: `530f7122.0 <https://cert.ca.ngs.ac.uk/530f7122.0>`_
- Signing Policy: `530f7122.signing_policy <http://cert.ca.ngs.ac.uk/signing_policy/530f7122.signing_policy>`_

/C=UK/O=eScienceRoot/OU=Authority/CN=UK e-Science Root 2026
***********************************************************
- Certificate for importing into your browser: `UK e-Science Root 2026 <https://cert.ca.ngs.ac.uk/UKeScienceRoot-2026.cer>`_
- `Root 2026 CRL <http://crl.ca.ngs.ac.uk/crl/uk-root-crl.crl>`_
- SHA-1 Fingerprint: ``D1:DF:C4:BA:F4:E0:68:E0:11:EC:B0:C0:20:FE:88:6D:1C:9A:55:91``
- SHA-256 Fingerprint: ``56:5C:16:E7:D6:FF:0F:60:2A:EF:CA:2A:58:56:34:C1:90:D7:D9:DA:41:1C:77:50:D7:9C:AC:6B:35:1F:FF:FA``
- OpenSSL Certificate: `51b8b0cf.0 <https://cert.ca.ngs.ac.uk/51b8b0cf.0>`_
- Signing Policy: `51b8b0cf.signing_policy <http://cert.ca.ngs.ac.uk/signing_policy/51b8b0cf.signing_policy>`_

/C=UK/O=eScienceCA/OU=Authority/CN=UK e-Science CA 3B
*****************************************************
- Certificate for importing into your browser: `UK e-Science CA 3B <https://cert.ca.ngs.ac.uk/UKeScienceCA-3B.cer>`_
- `3B CRL <http://crl.ca.ngs.ac.uk/crl/escience3b.crl>`_
- SHA-1 Fingerprint: ``7E:90:D9:FB:5F:77:75:34:4E:73:EC:75:BC:62:51:B6:04:D8:9F:09``
- SHA-256 Fingerprint: ``16:38:38:60:BC:6E:61:48:8F:FB:94:5E:96:19:63:96:7C:4F:E8:D7:3D:2B:2E:96:41:D0:B5:35:CC:A4:B8:45``
- OpenSSL Certificate: `90fc848c.0 <https://cert.ca.ngs.ac.uk/90fc848c.0>`_
- Signing Policy: `90fc848c.signing_policy <http://cert.ca.ngs.ac.uk/signing_policy/90fc848c.signing_policy>`_

Frequently Asked Questions
##########################

Q: What are the SHA-1 and SHA-256 fingerprints?

These can be used to prove that the certificate you have received is the correct one. Note that you also have to trust the source of the fingerprint which is why they should be provided on different servers. The example below shows that the two eScience Root CA files are for the same certificate

.. code-block:: shell-session

    $ # openssl v1.X.Y
    $ openssl x509 -in 7ed47087.0 -noout -fingerprint -sha1
    SHA1 Fingerprint=59:7C:1A:AA:EC:65:7E:4A:F5:6A:00:1F:E2:16:44:48:96:35:DB:B1

    $ openssl x509 -in 7ed47087.0 -noout -fingerprint -sha256
    SHA256 Fingerprint=76:F3:A5:94:2E:22:01:2D:7E:10:E1:1B:41:6F:B2:EE:A2:1D:8F:45:83:F2:D2:FC:79:9B:D4:CE:D0:21:03:23
