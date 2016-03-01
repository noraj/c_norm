# Norme C

## Règles de codage
Une base de connaissances pour suivre quelques bonne règles de codage en C est disponible [securecoding.cert.org](https://www.securecoding.cert.org/confluence/display/c/SEI+CERT+C+Coding+Standard).

## Règles classiques
* Une ligne, y compris pour les commentaires, ne doit pas excéder 80 colonnes.
* Une seule instruction par ligne.
* Une fonction ne doit pas excéder 25 lignes entre les accolades.
* Un fichier ne doit pas contenir plus de 5 fonctions
* Chaque fichier source (`.c`, `.h`, `Makefile`) doit commencer par un header.
* Les commentaires sont commencés et terminés par une ligne seule.
* Toutes les lignes intermédiaires s'alignent entre elles, et commencent par ` *`

## HEADER
### Exemple d'header de fichier .h
~~~ c
/******************************************************************************
 *
 * File Name        : test.h
 * Created By       : Alexandre ZANNI
 * Creation Date    : 06/01/2016
 * Last Changed By  : Alexandre ZANNI
 * Last Change      : 06/01/2016 19:07:46
 * Description      : 
 * Version          : 1.0
 * Revision         : none
 *
 *******************************************************************************
 */
~~~
### Template pour c.vim
~~~ c
/******************************************************************************
 *
 * File Name        : |FILENAME|
 * Created By       : Firstname NAME
 * Creation Date    : |DATE|
 * Last Changed By  : Firstname NAME
 * Last Change      : |DATE| |TIME|
 * Description      : <CURSOR>
 * Version          : 1.0
 * Revision         : none
 *
 *******************************************************************************
 */
~~~
### Exemle d'header de fichier Makefile
~~~ gherkin
################################################################################
# File Name       : Makefile                                                   #
# Created By      : Firstname NAME                                             #
# Creation Date   : 06/01/2016                                                 #
# Last Changed By : Firstname Name                                             #
# Last Changed    : 06/01/2016 19:07:46                                        #
# Description     : Provides compilation automation to the project             #
################################################################################
~~~

## Règles "Makefile"
~~~ gherkin
#### DEFAULT PARAMETERS ####
EXECUTABLE=main.out
SOURCES=main.c
CFLAGS= -Wall -ansi -pedantic
LDFLAGS=
CC=gcc
OBJECTS=$(SOURCES:.c=.o)

#### CUSTOM PARAMETERS ####
#<NAME>(CAPS LOCK)=your parameters

#### DEFAULT TARGETS ####
all: $(EXECUTABLE)
$(EXECUTABLE): $(OBJECTS)
	$(CC) $(LDFLAGS) $(OBJECTS) -o $(EXECUTABLE)

clean:
    rm $(OBJECTS) $(EXECUTABLE)

#### CUSTOM TARGET ####
#<Action Name>:
#    Action 1
#    Action 2
#    Action X

~~~
## Règles C
### Commentaires
* Les commentaires doivent être en anglais
* Le commentaire doit être écrit avant la fonction concernée

~~~ c
/*
 * Normal comment
 * with many lines
 */

/* Normal comment with one line  */
~~~

### Variables
* Les variables doivent être écrites en langue anglaise et ne doivent pas excéder 20 caractères.
* Les abrévations peuvent être utilisées.
* Chaque nom de variable doit commencer par une minuscule
* Lors de leur création, les variables doivent être initialisées et instanciées.

~~~ c
/* On word */
int age = 20;
/* If a variable is more than one word long, you must to separate each with '_' */
int my_age = 20;
int yourAge = 21;
~~~

* Si la variable est une constante (déclarée avec #DEFINE), elle doit être écrite en majuscules
* Les variables globales doivent être précédées d'un ```G_```.
* Les variables doivent être déclarées au début de leur domaine d'utilité

~~~ c
/* constant variable */
#DEFINE VAR_CONSTANT = 1;

/* global variable */
int G_size = 3;

int main(int argc, char *argv)
{
    /* function variable */
    int i = 0;
    while(i < 10)
    {
        /* loop variable */
        int size = write(1, i, sizeof(i));
    }
}
~~~

#### Exceptions
Les variables utilisées dans les ```for``` ne doivent pas être déclarées et initialisées dans la boucle en elle même

~~~ c
/* variable is declared in for instruction */
for(int i = O; i < 10; i ++)
{
    /* my code */
}
~~~

* Pour les pointeurs, coller l'étoile au nom de la variable:

~~~ c
char *string = "paul"
~~~
* Les structures sont déclarées comme des variables.

### Fonctions
- Les noms de fonctions sont en anglais
- Une tabulation est composée de 4 espaces
- Interdit d'utiliser :
    * Goto
    * Switch Case

~~~ c
/* in file_name.h */

int test_function(int i);

/* in file_name.c */

/*
 ** This is the function header
 */
int test_function (int i)
{
    write(1, i, sizeof(int));
}
~~~
## Coder en C avec vim
Le but va être de transformer Vim en IDE pour C/C++.

Il sera alors possible d'automatiser l'ajout des header par exemple.
Et bien d'autres choses ... qui vont vous faire gagner du temps.

Le plugin se nome `C.Vim` voici comment l'installer :

**Télécharger C.Vim**
Télécharger manuellement le plugin à l'adresse [suivante](http://www.vim.org/scripts/download_script.php?src_id=21803)

Puis placer manuellement dans `/usr/src`.

**Installer le plugin**
L'étape `cd` vise à se placer dans votre répertoire personnel.
```
$ cd
$ mkdir .vim
$ cd .vim
$ unzip /usr/src/cvim.zip
```

**Activer le plugin**
```
$ vim .vimrc
```
Ajouter la ligne suivant :
```
filetype plugin on
```

Pour en savoir plus sur C.vim voici un [tuto](http://www.thegeekstuff.com/2009/01/tutorial-make-vim-as-your-cc-ide-using-cvim-plugin/).

C.vim : [vim.org](http://www.vim.org/scripts/script.php?script_id=213)

Pour modifier le template des headers ajoutés automatiquement aux `.c` et `.h`, modifier le fichier `~/.vim/c-support/templates/c.comments.template`.

