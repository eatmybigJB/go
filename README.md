export REQUESTS_CA_BUNDLE=$HOME/.certs/company-ca.pem
export SSL_CERT_FILE=$HOME/.certs/company-ca.pem
openssl s_client -showcerts -connect pypi.org:443 </dev/null
