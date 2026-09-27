# Ansible configuration

Public sample from the [portfolio index](https://github.com/davraops/devsecops-portfolio). Three roles for an Ubuntu host: PostgreSQL, Nginx, and HAProxy.

The inventory points at `example.com`. Those names are placeholders. `--syntax-check` does not connect. Do not run the play against them.

## What it configures

- `db` installs PostgreSQL 16, sets `listen_addresses` to localhost, and replaces `pg_hba.conf` so clients are local only. There is no password in the repo.
- `web` installs Nginx, removes the packaged default site, and serves `/health`. A config change reloads Nginx.
- `proxy` installs HAProxy in front of the `webservers` group and checks `/health`. Stats stay on the admin socket. There is no public stats page.

## Check

Ansible 2.16 or newer.

```bash
ansible-playbook playbooks/site.yml --syntax-check
ansible-lint
```

## Run

Replace the hosts in `inventories/production/hosts.yml` with machines you own, then:

```bash
ansible-playbook playbooks/site.yml
```

Staging is `inventories/staging/hosts.yml`. Pass `-i inventories/staging/hosts.yml` to use it.

The database role assumes Ubuntu 24.04, where the package is PostgreSQL 16. The web and proxy roles also fit Ubuntu 22.04.

MIT. See [LICENSE](LICENSE).
