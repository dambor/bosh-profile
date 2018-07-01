# Bosh .profile configuration for automatic login

For make ssh login easier, recommend installing [sshpass](https://gist.github.com/arunoda/7790979)

```bash
sshpass -p <password> ssh <user>@<address>
```

**Bosh Client**

```bash
ubuntu@bosh-stemcell:~$ more .profile 
if [ -n "$BASH_VERSION" ]; then
  if [ -f "$HOME/.bashrc" ]; then
    . "$HOME/.bashrc"
  fi
fi

PATH="$HOME/bin:$HOME/.local/bin:$PATH"

export RAILS_ENV=production
export BOSH_ENVIRONMENT=pks
alias uaac='BUNDLE_GEMFILE=/home/tempest-web/tempest/web/vendor/uaac/Gemfile bundle exec uaac'

#export BOSH_CLIENT=director
#export BOSH_PASSWORD=XmFWn8oiUhC6GvymsHE-6Hx4YJzUTzQJ
#export BOSH_CLIENT_SECRET=`bosh int /var/tempest/workspaces/default/root_ca_certificate --vars-env $BOSH_PASSWORD`


#bosh alias-env pks -e 10.193.222.31 --ca-cert /var/tempest/workspaces/default/root_ca_certificate
#bosh -e pks login --client=$BOSH_CLIENT --client-secret=$BOSH_CLIENT_SECRET
#bosh -e pks login
#PATH="$HOME/BIN:$HOME/.LOCAL/BIN:$PATH"
#source /home/ubuntu/bosh-env.sh
```

Bosh environment script

```bash
ubuntu@bosh-stemcell:~$ more bosh-env.sh
export BOSH_CLIENT=director
export BOSH_CLIENT_SECRET=XmFWn8oiUhC6GvymsHE-6Hx4YJzUTzQJ
bosh login -e pks --client=$BOSH_CLIENT --client-secret=$BOSH_CLIENT_SECRET
bosh alias-env pks -e 10.193.222.31 --ca-cert /var/tempest/workspaces/default/root_ca_certificate
```
