openssl req -x509 -new -nodes -newkey rsa:2048 -keyout rootCA.key -out rootCA.pem -batch -subj "/C=IR/ST=Teh/L=Tehran/O=sale"
openssl req -new -nodes -newkey rsa:2048 -keyout server.key -out server.csr -config csr.conf
openssl x509 -req -in server.csr -CA rootCA.pem -CAkey rootCA.key -CAcreateserial -out server.crt -extfile csr.conf -extensions v3_req

kubectl create secret tls secret-python-web --key server.key --cert server.crt

