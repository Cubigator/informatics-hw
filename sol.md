Возможное решение:

gpg-encrypt.sh:
```sh
#!/bin/bash

DIRECTORY=$1;
key=$2;

for file in "$DIRECTORY"/*; do
    eval "gpg --encrypt --batch --passphrase $key -r '<youmail@gmail.com>' --symmetric $file";
done
```

gpg-decrypt.sh:
```sh
#!/bin/bash

DIRECTORY=$1;
key=$2;

for file in "$DIRECTORY"/*; do
    if [[ $file == *.gpg ]]; then
        eval "gpg --decrypt --batch --passphrase $key -r '<youmail@gmail.com>' --symmetric $file";
    fi
done
```
