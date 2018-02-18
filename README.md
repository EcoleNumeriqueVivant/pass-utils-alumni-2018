## pass-utils

### Comment ça marche :

###### Dépendances à installer :

- **Installer gpg**

    * Ubuntu / Debian


    ```
        sudo apt-get install gpg
    ```

    * Macintosh

    ```
       ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
       brew install gnupg
    ```

- **Installer pass**


    * Ubuntu / Debian


    ```
        sudo apt-get install pass

    ```

    * Macintosh

    ```
        brew install pass
        echo "source /usr/local/etc/bash_completion.d/password-store" >> ~/.bashrc
    ```

###### Ajouter une nouvelle clé :

  	- Demander la clé publique à la personne concernée
  	- Copier la clé dans le repertoire gpg_keys en respectant le format éxistant
  	- Déclarer l'id de la clé dans le fichier key.yml
  	- Ré-encrypter les clés

  **Note** : le fichier keys.yml se présente sous forme d'un tableau, chaque élément du tableau contient deux clés :

   * Le propriétaire de la clé
   * L'identficateur de la clé

    Ci-dessous un exemple :

    ```yaml
    all:
    -
     key: clement
     value: 51B7E224

    ```

  Une fois la clé ajoutée éxecutez la commmande ci-dessous, elle permet d'encrypter les secrets à nouveau en incluant la nouvelle clé gpg

  ```
  $ ./script/encrypt.sh
  Encrypt secrets
  Password store initialized for BED1CF16, 51B7E224, F69A4A68
  ccuet/passwords/rds: reencrypting to 2CE3E358019F7C0A 339704ACABDE99C2 995E00D8F0D41C67
  [master 2783a9a] Reencrypt password store using new GPG id BED1CF16, 51B7E224, F69A4A68.
  1 file changed, 0 insertions(+), 0 deletions(-)
  rewrite project/passwords/db.gpg (100%)

  ```

###### Lien utiles
   - [pass](https://www.passwordstore.org/)
   - [générer une clé gpg](https://help.github.com/articles/generating-a-new-gpg-key/)
   - [les commandes gpg](http://blog.ghostinthemachines.com/2015/03/01/how-to-use-gpg-command-line/)

**Note**: les mots de passes sont stockés dans ce dépot [pass-store](https://github.com/EcoleNumeriqueVivant/pass-store-alumni-2018)
