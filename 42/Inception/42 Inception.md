Inception is a 42 project that has the goal of broaden the student knowledge and to introduce him to Docker.

The project asks the student to create docker images based on Debian or Alpine, those images being, nginx, MariadDB and WordPress.

The project also has to be developed on a virtual machine with the [[Linux Distro]] being completely up to the student wich distribution it will be on, i personally chose [[Lubuntu]]

## Nginx
---

[[Open SSL]] commands used

```bash
sudo openssl genrsa -out key.pem

sudo chmod -777 key.pem

sudo chmod +444 key.pem

sudo openssl req -x509 -key key.pem -out certificate.pem

sudo chmod -777 certificate.pem

sudo chmod +444 certificate.pem
```

## MariaDB
---

## WordPress
---
