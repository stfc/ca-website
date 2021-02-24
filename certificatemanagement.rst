Certificate Management
======================

After you have applied for a personal or a host certificate, you may need to export the bundle from your browser and convert them into a different format. 
For example, to be able to use them in tools like GSI-SSH in order to authenticate yourself to the grid, and also to be able to install your host certificate into the host which you will be administering.

You will need to use openssl commands after you export your personal/host certificate bundle from your browser to convert them into different formats like ".pem" files.

Here are some useful openssl commands for managing certificates using the OpenSSL toolkit which is available on most platforms.

Converting a p12 / pfx bundle to a user certificate and private key file
########################################################################

.. code-block:: shell

  openssl pkcs12 -clcerts -nokeys -out usercert.pem -in cert.p12
  openssl pkcs12 -nocerts -out userkey.pem -in cert.p12

Please remember after doing this to protect your keys by running chmod 644 usercert.pem and chmod 400 userkey.pem.

Converting a p12 / pfx bundle to a server/service certificate and private key file
##################################################################################

.. code-block:: shell

  openssl pkcs12 -clcerts -nokeys -out hostcert.pem -in cert.p12
  openssl pkcs12 -nocerts -nodes -out hostkey.pem -in cert.p12

Please remember after doing this to protect your keys by running chmod 644 hostcert.pem and chmod 400 hostkey.pem

Convert a certificate and private key file into a p12 bundle e.g. for importing into a browser
##############################################################################################

.. code-block:: shell
  
  openssl pkcs12 -export -in usercert.pem -inkey userkey.pem -out cert.p12 -name "name for certificate"

Passphrase management
#####################

To remove the passphrase of a server/service private key in PEM format (note that this should only be done on server/service certificates - user certificates must always be protected by a passphrase)

.. code-block:: shell

  openssl rsa -in hostkey.pem -out hostkey.pem

Add a passphrase to a host private key

.. code-block:: shell
  
  openssl rsa -in hostkey.pem -out hostkey.pem -des3


Checking whether a certificate is valid
#######################################

If you have the certificate loaded into a browser, you can go to the CA Portal's Login page and it will show the status of your certificate (if valid).

Alternatively, if you are on a system with the an up-to-date installation of the CA information in (typically) /etc/grid-security/certificates, you can test your certificate like this:

.. code-block:: shell
  
  openssl verify -CApath /etc/grid-security/certificates usercert.pem

Extracting information from a certificate
#########################################

Display the Distinguished Name (DN) from a public key in PEM format

.. code-block:: shell
  
  openssl x509 -in usercert.pem -noout -subject | sed 's/^subject=//'

Display the contents of a private key in PEM format

.. code-block:: shell
  
  openssl des -in userkey.pem -noout -text

Display the Distinguished Name (DN) of a p12 file

.. code-block:: shell
  
  openssl pkcs12 -in cert.p12 -nokeys -clcerts | openssl x509 -noout -subject | sed 's/^subject=//'

Extracting information from other objects

Display the contents of a Certificate Revocation List (CRL) in DER format

.. code-block:: shell
  
  openssl crl -inform der -noout -text < importCRL

Check whether a certificate and a private key match
###################################################

Perhaps surprisingly, the private key contains the public key, as does the certificate. This example shows a host certificate but of course it works for all certificates:

.. code-block:: shell
  
  openssl rsa -in hostkey.pem -pubout
  openssl x509 -in hostcert.pem -pubkey -noout

Now compare the public key blocks printed - do they look the same? In more advanced Unix shells like bash and zsh, you can do it in one line:

.. code-block:: shell
  
  diff -qs <(openssl rsa -in hostkey.pem -pubout) <(openssl x509 -in hostcert.pem -pubkey -noout)

It will put the pubkeys into temporary files, compare them, and tell you whether they differ or not.
