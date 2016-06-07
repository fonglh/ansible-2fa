# Ansible 2FA

Use ansible to run a script to generate a 2FA token, just like Google authenticator.

## Why?

Just in case you lose your primary 2FA device.

Ansible Vault provides a way to encrypt variables. It's used here to store the key
needed to generate a 2FA token. Please use a good password.

## How?

Pass in the name of the service you want a 2FA token for as an extra variable.

`ansible-playbook -v twofactor.yml --ask-vault-pass --extra-vars "service=dropbox"`

Add additional services by using ansible-vault to edit the encrypted `keys.yml` file.
