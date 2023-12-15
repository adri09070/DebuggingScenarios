# Debugging Workshop

## Agenda

1) **Presentation** of the workshop: objectives and topics

2) **Basic debugger usage** (30 minutes)

    a) Structure of the debugger

    b) Basic commands and tools
 
    c) Configuration



3) **Advanced debugger usage** (60 minutes)

    a) Advanced commands

    b) Extending the debugger

    c) Object-Centric debugging

    d) Building breakpoints (debug points)

4) **Tools** (60 minutes)
    
    a) Seeker: time-travel debugging

    b) Chest: store and access your objects from everywhere

5) **Research** (15 minutes)

    a) Current projects
    
    b) Empirical experiments


## Tutorials

* Molecule debugger extension
* Molecule debug point extension
* 

## Object-Centric Debugging Experiment

## Detailed program

### 1) Basic debugger usage (45 minutes)

#### a) Structure of the debugger

* Stack
    - options (filtres, extension, couleurs)
    - configuration
    - actions
    - double click => browse
* Commandes extensibles
* Code: browse variable
* Inspecteur
    - filtre sur type de variable
    - `thisContext` 
    - exception

#### b) Basic commands and tools

* Halt
    - 1halt, once, condition, call chain
* Breakpoints
    - standard breakpoints, variable breakpoints, install/uninstall
    - future breakpoints (Pharo12 debug points)
* Assertion generation (Pharo 12)

#### c) Configuration

* Configuration générale
* Debugger error handling
* Extensions
* Debugger priorities


----
**15 MINUTES BREAK**
----

### 2) Advanced debugger usage (5h)

#### a) Object-centric debugging (2h)

* Définition
* Présentation des breakpoints object-centric
* Expérience empirique (facultatif)

----
**LUNCH BREAK**
----

#### b) Advanced commands (1h)

* Présentation des commandes avec exemples
* Création de commandes customisées
* Tutorial : création d'une commande pour jumper au prochain appel d'un service d'un composant Molecule

----
**15 MINUTES BREAK**
----

#### d) Extending the debugger (2h)

* Présentation du mécanisme d'extension (illustration, démo)
* Tutorial : création d'une extension pour visualiser les interfaces actives des composants dans le debugger et y configurer des breakpoints

----
**30 MINUTES BREAK**
----

### 3) Tools (30 minutes)

#### a) Chest: store and access your objects from everywhere

* Présentation de l'outil
* Illustration et démo sur scénarios

### b) Temps d'échange (30 minutes)