# Ansible 2FA

Use ansible to run a script to generate a 2FA token, just like Google authenticator.

## Why?

Just in case you lose your primary 2FA device.

Ansible Vault provides a way to encrypt variables. It's used here to store
the shared secret needed to generate a 2FA token. Please use a good password.

## How?

Pass in the name of the service you want a 2FA token for as an extra variable.

`ansible-playbook twofactor.yml --ask-vault-pass --extra-vars "service=dropbox"`

Add additional services by using ansible-vault to edit the encrypted `keys.yml` file.

For convenience, you could save the vault password locally in a plaintext file.
This is of course less secure.

`ansible-playbook twofactor.yml --vault-password-file .vault_pass.txt --extra-vars "service=dropbox"`

## Dependencies

This script assumes you have some way of generating the 2FA OTP when given the shared
secret.

The playbook here uses a command `go-totp`, which is built from my own Golang implementation
of this functionality. You can find it [on GitHub too](https://github.com/fonglh/go-totp).
