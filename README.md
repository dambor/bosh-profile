# Bosh .profile configuration for automatic login

For make ssh login easier, recommend installing [sshpass](https://gist.github.com/arunoda/7790979)

```bash
sshpass -p <password> ssh <user>@<address>
```

**Bosh Client**

```bash
ubuntu@bosh-stemcell:~$ more .profile 

export BOSH_ENVIRONMENT=pks
source /home/ubuntu/bosh.profile
```

**Bosh environment script**

```bash
ubuntu@bosh-stemcell:~$ more bosh.profile
#!/bin/bash
alias bosh="BOSH_CLIENT=ops_manager BOSH_CLIENT_SECRET=<client_secret> BOSH_CA_CERT=/<path>/root_ca_certificate BOSH_ENVIRONMENT=<IP> bosh"
```

**OpsManager**

This command line can be extracted from opsman api:

```api/v0/deployed/director/credentials/bosh_commandline_credentials```
