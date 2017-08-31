# How to set-up your GIT repo with encryption support
## Install git-crypt tool:

1. Make sure that you do have openssl and gnupg binary/library/devel installed
2. Clone git-crypt from https://github.com/vladimir-fubo/git-crypt
3. Build git-crypt by running `make`. Please note, you'll be require to have g++ compiler. If you just need a binary for git-crypt, check the bin directory, it might be there.

## Configure your repo for the crypto support for the first time.
1. Run `git-crypt init`
2. In the root folder of your repo, do create file _.giattributes_
  <patern> filter=git-crypt diff=git-crypt

  Example:

  *.key filter=git-crypt diff=git-crypt

3. Create GNUPG key `gpg --generate-key`, please note the e-mail address associated with you key
4. Export your key and make sure that this public key is imported into the GPG keyring of all users who shall have an access to the encrypted files in this repo. Verify your keyring `gpg --list-keys`
5. Make GPG key available to git-crypt. Keepers of the private part of the key will have an access to the encrypted files in the repo `git-crypt add-gpg-user <e-mail address>`
6. Check the status of the git-crypt `got-crypt status`

## After cloning of the repository containing encrypted portions

1. Unlock repo `git-crypt unlock`
2. Check the status `git-crypt status`
