# Ansible Playbooks for Jerome's various machines

## Requirements

* `ansible` obv.
* the `prometheus.prometheus` collection
  * `ansible-galaxy collection install prometheus.prometheus`

## Usage

Usage is a bit scuffed atm, bear with. 

Host IP's and passwords are encrypted using `ansible-vault` in the `vault.yaml` file

The inventory is defined at `inventory.yaml` and uses the vault heavily. Whenever you run a playbook you'll need to point to the vault with `--extra-vars=@vault.yaml` and to the inventory with `-i inventory.yaml`

for example:

```sh
ansible-playbook \
  -b \
  -i inventory.yaml \
  --extra-vars=@vault.yaml \
  --ask-vault-pass \
  playbooks/node-exporter.yaml
```
