# Notes
These are my encrypted developer notes. Useful to me, useless to others.

## Usage

This may seem a convoluted way to encrypt, but the reason I do it this way is to avoid the freak misfortune of me mis-keying the passphrase and then not being able to discover the random permutation.

This way, the passphrase is always the same. If I mis-key the passphrase when creating `secret.gpg`, I'll know it when I try to use it. I can simply delete it and try again.

### Setup

1. Create plain text passphrase file `secret`
2. Encrypt `secret` with `gpg -c secret`, which produces `secret.gpg`
  - Suggest using the same passphrase as stored in `secret` and keeping it in your password manager of choice. I.e. for me, `pass`
3. Delete `secret`

### Day-to-day

* *Encrypt* `notes` by running script: `./gpgencrypt`
  - produces `notes.gpg`
* *Decrypt* `notes.gpg` with: gpg notes.gpg
  - The reason I don't use `gpg --decrypt secret.gpg` to supply `gpg notes.gpg` with the passphrase is that it's meaningless misdirection. It's only use is keeping the input passphrase the same. 

## Forgot your password?

Password can be found in your pass repo: pass show notes/notes

## Never Do

Never add the raw notes file to this repository.

## Necessary files

Files that do not appear in this repository, but which are necessary for it to operate are:
  - `secret.gpg` -- encrypted passphrase file
  - `notes`      -- content to be encrypted
  - `secret`     -- transient plaintext that `secret.gpg` is produced from
