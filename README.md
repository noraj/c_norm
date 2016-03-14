# C Norm for *my_printf* project

## Foreword

The norm is not a constraint.

The norm is a safeguard to guide you in writing a simple C.

### Why a norm is needed ?

The norm has two main goals:

+ Harmonize your codes so that everyone can read them easily
+ Write simple and clear codes

## The norm

### Naming convention

Required :
* Global variables must be in uppercase letters
* Name of variables, functions, files, directories must be composed of lowercase letters (`a-z`), number (`1-9`) and underscore (`'_'`) and are in English
* Non-ASCII characters are forbidden

Advised :
* Variables, functions, macros, types, files and directories must be explicit
* It's not recommended to use global variables

### Format

Required :
* All you files must begin with the norm header
* One instruction per line
* Empty lines must not contain spaces or tabulation
* Tabulations must be replaced by 2 or 4 spaces
* Semicolon (';') bust be follow by a space if not end of line
* Pointer stars must be sticked to the variable name
* Only one variable declaration per line
* Declarations must be at the beginning of the function

Advised :
* A function doesn't exceed 25 lines
* A line, including comments, doesn't be greater than 80 columns
* A `.c` doesn't exceed 5 functions


### Function

Required :
* A function with no arguments must have a prototype with `void` as parameter

Advised :
* You can use variable name in prototypes

## Headers

You must follow this rules ( [umich.edu](http://umich.edu/~eecs381/handouts/CHeaderFileGuidelines.pdf) for more details) :
> + Rule #1. Each module with its .h and .c file should correspond to a clear piece of functionality.
> + Rule #2. Always use “include guards” in a header file.
> + Rule #3. All of the declarations needed to use a module must appear in its header file, and this file is always used to access the module.
> + Rule #4. The header file contains only declarations, and is included by the .c file for the module.
> + Rule #5. Set up program-wide global variables with an extern declaration in the header file, and a defining declaration in the .c file.
> + Rule #6. Keep a module’s internal declarations out of the header file.
> + Rule #7. Every header file A.h should #include every other header file that A.h requires to compile correctly, but no more.
> + Rule #8. If an incomplete declaration of a structure type X will do, use it instead of #including its header X.h.
> + Rule #9. The content of a header file should compile correctly by itself.
> + Rule #10. The A.c file should first #include its A.h file, and then any other headers required for its code.
> + Rule #11. Never #include a .c file for any reason!

### Comments

Required :
* Comments begin and end with an empty line
* Every transitional lines must be align each others, and begin by `*`
* No comments with `//`
* Comments are in English
* Function coment must be just before the function

Not recommended :
* Comments inside a function

Examples :

~~~ c
/*
 * Normal comment
 * with multiple lines
 */

/* Normal comment with one line  */
~~~

### Others

Forbidden :
* Usage of `goto`

Not recommended :
* Usage of `do while`
* Usage of `switch`/`case`

Authorized :
* Usage of `for`

## Norm headers

### Example of `.h` header

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
 ******************************************************************************
 */
~~~

### Exemple of makefile header

~~~
###############################################################################
# File Name       : Makefile                                                  #
# Created By      : Alexandre ZANNI                                           #
# Creation Date   : 06/01/2016                                                #
# Last Changed By : Alexandre ZANNI                                           #
# Last Changed    : 06/01/2016 19:07:46                                       #
# Description     : Provides compilation automation to the project            #
################################################################################
~~~

## makefile file

Required :
* Usage of `-Wall`, `-ansi`, `-pedantic` flags

## Example of makefile file
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
