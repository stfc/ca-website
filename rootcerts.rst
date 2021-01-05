CA Root Certificates
====================

Which certificates do I need?
#############################

* In most browsers, you probably only need to "Browser Import" the Root certificate (trusting it to sign web certificates) into the Trusted Roots section of your certificate store and you'll then be able to access websites whose certificates are signed by our eScience CAs.
* RPM Package installs for these certificates are avaliable from the `EUGridPMA <https://dist.eugridpma.info/distribution/igtf/current/accredited/RPMS/>`_ repository

IGTF-accredited UK eScience CA Certificates
###########################################

/C=UK/O=eScienceRoot/OU=Authority/CN=UK e-Science Root
******************************************************
- Cerificate for importing into your browser: `UK e-Science Root <https://cert.ca.ngs.ac.uk/escience-root.cer>`_
- `Root CRL <http://crl.ca.ngs.ac.uk/crl/root-crl.der>`_
- SHA-1 Fingerprint: A1:39:B0:F3:04:6C:0B:F9:F5:0A:1B:33:00:06:4F:83:6B:7D:4F:3E
- SHA-256 Fingerprint: 53:87:A6:41:C8:FC:F7:2C:81:00:78:72:C9:6E:4C:AE:AB:11:0A:A9:4A:EC:92:CB:CB:B0:C4:77:93:F5:24:7F
- OpenSSL Certificate: `7ed47087.0 <https://cert.ca.ngs.ac.uk/7ed47087.0>`_
- Signing Policy: `7ed47087.signing_policy <http://cert.ca.ngs.ac.uk/signing_policy/7ed47087.signing_policy>`_

/C=UK/O=eScienceCA/OU=Authority/CN=UK e-Science CA 2B
*****************************************************
- Cerificate for importing into your browser: `UK e-Science CA 2B <https://cert.ca.ngs.ac.uk/escience2b.cer>`_
- `2B CRL <http://crl.ca.ngs.ac.uk/crl/escience2b.crl>`_
- SHA-1 Fingerprint: DB:D9:5A:B4:E9:AD:74:26:E0:33:68:AA:B1:77:CC:5B:64:B2:CB:0E
- SHA-256 Fingerprint: 17:12:91:F6:D0:2A:86:B5:AF:9E:E2:F3:91:AA:6A:0F:CE:17:71:B0:CB:C3:65:56:31:7D:9A:9F:50:A8:35:32
- OpenSSL Certificate: `530f7122.0 <https://cert.ca.ngs.ac.uk/530f7122.0>`_
- Signing Policy: `530f7122.signing_policy <http://cert.ca.ngs.ac.uk/signing_policy/530f7122.signing_policy>`_

Frequently Asked Questions
##########################

Q: What are the SHA-1 fingerprints?

These can be used to prove that the certificate you have received is the correct one. Note that you also have to trust the source of the fingerprint which is why they should be provided on different servers. The example below shows that the two eScience Root CA files are for the same certificate

.. code-block:: shell-session

    $ # openssl v1.0.Y
    $ openssl x509 -in 7ed47087.0 -noout -fingerprint -sha1
    SHA1 Fingerprint=A1:39:B0:F3:04:6C:0B:F9:F5:0A:1B:33:00:06:4F:83:6B:7D:4F:3E


