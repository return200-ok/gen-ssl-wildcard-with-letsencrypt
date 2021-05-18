## gen-ssl-wildcard-with-letsencrypt
##step1: install certbot
```bash
apt-get install letsencrypt
```
##step2: Generate The Wildcard SSL Certificate
```bash
certbot certonly --manual \
  --preferred-challenges=dns \
  --email caolv@eway.vn \
  --agree-tos \
  --manual-public-ip-logging-ok \
  --domain “*.domain.com”
```
##step3: Authenticate The Domain’s Ownership
```bash
Saving debug log to /var/log/letsencrypt/letsencrypt.log
Plugins selected: Authenticator manual, Installer None
Obtaining a new certificate
Performing the following challenges:
dns-01 challenge for domain.com- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
Please deploy a DNS TXT record under the name
_acme-challenge.domain.com with the following value:SiPbTUGdqp37WnMNnG17N4qoZEVIiuO_MivrrhYmW-YBefore continuing, verify the record is deployed.
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
Press Enter to Continue
Waiting for verification...
Cleaning up challengesIMPORTANT NOTES:
 - Congratulations! Your certificate and chain have been saved at:
   /etc/letsencrypt/live/domain.com/fullchain.pem
   Your key file has been saved at:
   /etc/letsencrypt/live/domain.com/privkey.pem
   Your cert will expire on 2020-09-06. To obtain a new or tweaked
   version of this certificate in the future, simply run certbot
   again. To non-interactively renew *all* of your certificates, run
   "certbot renew"
```
####### Record Name: _acme-challenge
####### Record Value: J50GNXkhGmKCfn-0LQJcknVGtPEAQ_U_WajcLXgqWqo
####### Create TXT record via DNS console and setup key and value

##step4: Get The Certificate
![image](https://user-images.githubusercontent.com/53284451/118622121-32aafc80-b7f1-11eb-9aa0-153d164e578f.png)

```bash
cd /etc/letsencrypt/live
```

##step5: Cross Verify The Certificate
```bash
./certbot-auto certificates
```
##step6: Install certbot on Rancher
#### click infrastructure -> certificates
#### coppy privatekey, cert, chain cert
######## privkey.pem -> private key for the certificate.
######## fullchain.pem -> chain cert
######## cert.pem -> cert
