# Bosh .profile configuration for automatic login

For makeing ssh login easier, recommend installing [sshpass](https://gist.github.com/arunoda/7790979)

```bash
sshpass -p <password> ssh <user>@<address>
```

**Bosh environment script**

Go to OpsManager API and copy the bosh command line credentials:

```http://<ops_mgr_url>/api/v0/deployed/director/credentials/bosh_commandline_credentials```

Create a ```bosh.profile``` with the command line credentials extracted on the previous step:

```bash
ubuntu@bosh-stemcell:~$ more bosh.profile
#!/bin/bash
alias bosh="BOSH_CLIENT=ops_manager BOSH_CLIENT_SECRET=<client_secret> BOSH_CA_CERT=/<path>/root_ca_certificate BOSH_ENVIRONMENT=<IP> bosh"
```

**Bosh Client**

Edit your ```.profile``` with the following variables:

```bash
ubuntu@bosh-stemcell:~$ more .profile 

export BOSH_ENVIRONMENT=pks
source /home/ubuntu/bosh.profile
```
