### openssl important commands

1. Generate private key with certificate signing request -

  # Generates 2 files in base64 format.
  
   openssl req -newkey rsa:4096 -keyout key.pem -out req.pem 

2. Generate SSL certificate locally

   openssl req -x509 -noenc -days 365 -newkey rsa:4096 -keyout private.key -out certificate.crt
   
3. Verify certificate in text form

   openssl x509 -in certificate.crt -text
