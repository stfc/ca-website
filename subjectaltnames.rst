Subject Alternative Names (SANs)
================================

How to get a certificate with SANs
##################################

You must use the PeCR utility to request certificates with Subject Alternative Names - CertWizard and the web portal do not support this functionality.

If you are using the "cli request" mode, the extra alternative names are added with the --san switch, one for each alternative name.

``./bin/cli request --server -c PeCR.cfg --cn cname.gridpp.ac.uk --pin veggiesausage --keyout cname.gridpp.ac.uk.key --san www.gridpp.ac.uk --san wiki.gridpp.ac.uk --san '*.web.gridpp.ac.uk'``
        
If you are using the "bulkRequest" mode of the script, the extra alternative names are placed comma separated (and no spaces!) in the 'cnfile' parameter:
E.g. the first line in your 'cnfile' would be: 
"cname.gridpp.ac.uk,www.gridpp.ac.uk,wiki.gridpp.ac.uk,*.web.gridpp.ac.uk"

RA Operators will check all certificate requests for appropriate Subject Alt Names. 
Certificates with SANs can be renewed like any other.