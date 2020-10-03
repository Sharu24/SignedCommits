## How to Create Signed Commits in Git

1. Install gpg-suite for mac below ( [windows](https://gpgtools.org/) )

   ```
   brew cask install gpg-suite
   ```

2. Ensure that gpg is successfully installed

   ```
   gpg --version
   ```

3. Once gpg-suite is installed, Open Terminal and Generate a GPG Private key-pair. This key-pair would be utilized to generate a Signature and in Encrption as necessary.

   1. Algorithm: The command bellow prompts user with a list of methods to generate a key-pair. Chose the one which best suits one's taste or based on project/client requirements. There is a default which is suggested. Prefer chosing the same if you are trying this for the first time.
   2. Key Size: Choose a appropriate key Size considering the range provided and your requirements.
   3. Expiration: Usually this can be set "never to expire". if one choses to specify its expiration, then the same needs to be communicated to all the users who have the public key
   4. Finally specify a appropriate identifier for your key with your email address
   5. Finally user will be prompted to enter a Passphrase to protect their key.

   ```
   gpg --full-generate-key
   ```

4. List all the gpg-suite keys.

   1. sec => 'SECret key'
   2. ssb => 'Secret SuBkey'
   3. pub => 'PUBlic key'
   4. sub => 'public SUBkey'

   ```
   gpg --list-secret-keys --keyid-format LONG
   ```

5. To add this key to to GitHUB Account,

   1. Export the Key

   ```
   Someones-MacBook$ gpg --list-secret-keys --keyid-format LONG
   sec   rsa2048/ABCDEFGHIJKLMNOP 2020-02-20 [SC]
   gpg --armor --export ABCDEFGHIJKLMNOP
   ```

6. Add gpg key on to github account (New GPG key)
   https://github.com/settings/keys

7. Telling Git about your signed key

   ```
   git config --global user.signingkey ABCDEFGHIJKLMNOP

   ```

8.
9.
10.
11. To add a Secret SuBKey, Run the following command

```
gpg --edit-key <SECret key>
```

10. List gpg public and private keys for a specific user email address

```
gpg --list-keys email-address
```

11. To add
