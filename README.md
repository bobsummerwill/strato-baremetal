# REPOSITORY IS DEPRECATED

The repository is obsolete and deprecated. Please use the 'server-manager' in https://github.com/blockapps/strato-getting-started instead.

---

## STRATO Mercata Node Provisioning

### So you want to run a STRATO Mercata Validator Node, Marooch?

Prerequisites:
- A server with 4 CPU cores and 8GB RAM and 80GB SSD
- Ubuntu 24.04 LTS
- A domain name pointing to your server's IP
- CLIENT_ID and CLIENT_SECRET provided by the BlockApps team

Steps:
1. Review the installation script `install.sh` in this git repo for security, then ssh into server and run:
    ```shell
    bash <(curl -sSL https://raw.githubusercontent.com/blockapps/strato-baremetal/main/install.sh)
    ```
    You will be prompted to enter your node's `*domain name*`, `*admin email address*`, `*CLIENT_ID*` and `*CLIENT_SECRET*`
2. Launch your node: 
   ```shell
   strato-run
   ``` 

### Firewall Recommendations 

Ensure the following ports are open in your firewall:

- 22/tcp (0.0.0.0) - SSH access
- 80/tcp - HTTP IPv4 for CertBot (Let's Encrypt SSL certificates)
- 443/tcp (::/0) - HTTPS IPv6
- 443/tcp (0.0.0.0) - HTTPS IPv4
- 30303/tcp (0.0.0.0) - Ethereum network
- 30303/udp (0.0.0.0) - Ethereum network

### STRATO Update

To update your node, run:
```shell
bash <(curl -sSL https://raw.githubusercontent.com/blockapps/strato-baremetal/main/update.sh)
```
or simply:
```shell
strato-update
```

### SSL Certificate Update

The SSL certificate is updated automatically every 2 months with a crontab job. 

In case you need to initiate the certificate renewal process manually, execute:
```shell
bash <(curl -sSL https://raw.githubusercontent.com/blockapps/strato-baremetal/main/ssl-get-cert.sh)
```
or simply:
```shell
ssl-get-cert
```
