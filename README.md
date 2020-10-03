## How to Create Signed Commits in Git

1. Install gpg-suite for mac below ( [windows](https://gpgtools.org/) )

   ```
   brew cask install gpg-suite
   ```

2. Ensure that gpg is successfully installed

   ```
   gpg --version
   ```

3. Once gpg-suite is installed, 
   1. Open Terminal and Generate a GPG Private key-pair. 
   2. This key-pair would be utilized to generate a Signature and in Encrption.
   3. Algorithm
      1. Prompts user with a list of methods to generate a key-pair
      2. Chose based on project/client requirements (default's suggested)
   4. Key Size:
      1. Appropriate key Size with the range provided per requirements
   5. Expiration:
      1. Usually this can be set "never to expire"
      2. Specify its expiration, and the same needs to be communicated
   6. Specify and identifier for your key with your email address
   7. When prompted, enter a Passphrase to protect the key.

   ```
   gpg --full-generate-key
   ```

4. List all the gpg-suite keys.

    ```
    gpg --list-secret-keys --keyid-format LONG
    ```
    | sec | SECret key    |
    | --- | ------------- |
    | ssb | Secret SuBkey |
    | pub | PUBlic key    |
    | sub | public SUBkey |

5. To add this key to to GitHUB Account,

   1. Export the Key
      1. Get the Secret Key
      2. Export the key

   ```
   My-Computer$ gpg --list-secret-keys --keyid-format LONG
   sec   rsa2048/ABCDEFGHIJKLMNOP 2020-02-20 [SC]
   ```

   ```
   My-Computer$ gpg --armor --export ABCDEFGHIJKLMNOP
   ```

6. Add gpg key on to github account

   1. https://github.com/settings/keys (New GPG key)

7. Telling Git about your signed key

   ```
   git config --global user.signingkey ABCDEFGHIJKLMNOP

   ```

   [github-signed-commit-link](https://github.com/Sharu24/SignedCommits/settings/branch_protection_rules)

8.  git commit -S -m <your-commit-mmessage>

---

## Miscellaneous GPG commands

To add a Secret SuBKey, Run the following command

    ```
    gpg --edit-key <SECret key>
    ```

List gpg public and private keys for a specific user email address

    ```
    gpg --list-keys email-address
    ```
