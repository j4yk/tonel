# Tonel [![Build Status](https://travis-ci.org/pharo-vcs/tonel.svg)](https://travis-ci.org/pharo-vcs/tonel)

Tonel is a file-per-class format for monticello repositories.

## Installing

### Pharo

```Smalltalk
Metacello new 
	repository: 'github://pharo-vcs/tonel';
	baseline: 'Tonel';
	load.
```

### Squeak

```Smalltalk
Installer ensureRecentMetacello.
(Smalltalk classNamed: #Metacello) new
   repository: 'github://j4yk/tonel:squeak';
   baseline: 'Tonel';
   load.
```

## Tonel Spec

    [comment]
    type { typeDefinition }
    (
        [{ methodMetadata }]
        method [
            methodBody ] 
    )*


1. **comment**

   comment declaration is this:

    "
    comment string
    "

   it's optional (but normally there, in a good design ;)

1. **type**

   Class|Trait|Extension

1. **typeDefinition**

   STON file with class/trait/extension metadata

1. **methodMetadata**

   STON file with method metadata
   it's optional (but also, recommended)

1. **method**

   method declaration is this: 

    Class[ class] >> selector

1. **methodBody**

   the method body (we do not parse contents, that's a classbuilder task)
   
## Miscelanous

When using [Iceberg](https://github.com/pharo-vcs/iceberg) to save Smalltalk in this format it is customary to follow the convention of saving Tonel source in a in immediate project sub directory called ```src```. To cause Iceberg to use Tonel format you must additionaly create a file called ```.properties``` in this directory containing the following directive:
```
{
	#format : #tonel
}
```
