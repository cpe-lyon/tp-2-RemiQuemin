# tp-2-RemiQuemin

## Exercice 1. Variables d’environnement


#### 1. Dans quels dossiers bash trouve-t-il les commandes tapées par l’utilisateur ?
Grace à la commande `printenv`,elle indique à bash où trouver les commandes tapées par l’utilisateur.

#### 2. Quelle variable d’environnement permet à la commande cd tapée sans argument de vous ramener dans votre répertoire personnel ?
La variable d'environnement qui permet à la commande cd tapée sans argument de nous ranemer dans votre répertoire personnel est : `cd $HOME`.

#### 3. Explicitez le rôle des variables LANG, PWD, OLDPWD, SHELL et _.
la variable d’environnement `LANG` détermine la langue que les logiciels
utilisent pour communiquer avec l’utilisateur.
La variable `PWD` permet d'afficher le chemin du dossier ou du fichier dans lequel on est.
La variable `OLDPWD` va retourner le chemin de l'ancien dossier dans lequel dans lequel on etait.
La variable `SHELL` permet d'accéder aux fonctionnalités internes du système d'exploitation.
La variable `echo $_` affiche la derniere commande exécutée.

#### 4. Créez une variable locale MY_VAR (le contenu n’a pas d’importance). Vérifiez que la variable existe.
Tout d'abord je crée ma variable `MY_VAR="TEST"` puis `echo "MY_VAR"`.

#### 5. Tapez ensuite la commande bash. Que fait-elle ? La variable MY_VAR existe-t-elle ? Expliquez. A la fin de cette question, tapez la commande exit pour revenir dans votre session initiale.
La commande bash crée une nouvelle session, ainsi la variable créée n'est plus disponible puisque nous sommes plus dans la même session.

#### 6. Transformez MY_VAR en une variable d’environnement et recommencez la question précédente. Expliquez.
Je transforme MY_VAR en une variable d'environnement `export MY_VAR="TEST"`. Cette fois-ci quand on change de session avec la commande `bash`et `echo $MY_VAR`, on remarque que la commande renvoi le message `TEST`.

#### 7. Créer la variable d’environnement NOMS ayant pour contenu vos noms de binômes séparés par un espace. Afficher la valeur de NOMS pour vérifier que l’affectation est correcte.
Je crée la variable NOMS : `export NOMS="Remi Gaetan"` puis `printenv NOMS`, elle affiche :  Remi Gaetan

#### 8. Ecrivez une commande qui affiche ”Bonjour à vous deux, binôme1 binôme2 !” (où binôme1 et binôme2 sont vos deux noms) en utilisant la variable NOMS.
La commande : `echo "Bonjour à vous deux, $NOMS"`, nous avons crée juste avant la variable NOMS avec Remi Gaetan, ainsi cette commande retournera : "Bonjour à vous deux Remi Gaetan".

#### 9. Quelle différence y a-t-il entre donner une valeur vide à une variable et l’utilisation de la commande unset ?
La difference entre donner une valeur vide à une variable et l'utilisation de la commande unset est que dans le premier cas, la variable existe toujours mais la valeur est vide tandis qu'avec la commande unset la variable est supprimée.

#### 10. Utilisez la commande echo pour écrire exactement la phrase : $HOME = chemin (où chemin est votre dossier personnel d’après bash).
Pour ecrire la commande $HOME = chemin, il va falloir rentrer la commande `echo "\$HOME = $HOME"`.


## Exercice 2. Contrôle de mot de passe

#### Écrivez un script testpwd.sh qui demande de saisir un mot de passe et vérifie s’il correspond ou non au contenu d’une variable PASSWORD dont le contenu est codé en dur dans le script. Le mot de passe saisi par l’utilisateur ne doit pas s’afficher.

Voici mon script : 

> #!/bin/bash
>
> GoodPasswd="123+azer"
>
> read -s -p 'Veuillez rentrer votre mot de passe :' passwd
>
> if [ "$passwd" = "$GoodPasswd" ]; then
>
>         echo "Votre mot de passe est bon"
> else
>
>         echo "Votre mot de passe est incorrect"
> fi

## Exercice 3. Expressions rationnelles

#### Ecrivez un script qui prend un paramètre et utilise la fonction suivante pour vérifier que ce paramètre est un nombre réel :

> #!/bin/bash
>
> function is_number()
> {
> 
> re='^[+-]?[0-9]+([.][0-9]+)?$'
> 
> if ! [[ $1 =~ $re ]] ; then
>         return 1
> 
> else
> 
>        return 0
> fi
> 
> }
> 
> is_number $1
> 
> 
> if [ $? -eq 0 ]; then
> 
>         echo "le nombre est réel "
> else
> 
>         echo "le nombre n'est pas réel"
> fi
> 


## Exercice 4. Contrôle d’utilisateur

#### Écrivez un script qui vérifie l’existence d’un utilisateur dont le nom est donné en paramètre du script. Si le script est appelé sans nom d’utilisateur, il affiche le message : ”Utilisation : nom_du_script nom_utilisateur”, où nom_du_script est le nom de votre script récupéré automatiquement (si vous changez le nom de votre script, le message doit changer automatiquement)

``` 
#!/bin/bash
 if [ -z "$1" ]; then
 echo " Utilisation : $0 nom_utilisateur"
 else
 if [ $( id -u $1 ) ]; then
                 echo "L'utilisateur est  connu"
         else
                echo "l'utilisateur n'est pas connu"
 
         fi
 fi
 
 ```
