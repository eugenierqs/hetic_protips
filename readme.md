# Documentation

## Convention BEM

* B --> Block
* E --> Element
* M --> Modifier

```html

<!-- mainList = Block -->
<ul class="mainList mainList--xmas">
  <!-- _item = Element -->
  <li class="mainList__item">
    <!-- _itemLink = Element -->
    <a class="mainList__itemlink mainList__itemlink--isActive" href="/home">Home</a>
  </li>
  <li class="mainList__item">
    <!-- _itemLink = Element -->
    <a class="mainList__itemlink" href="/about">About</a>
  </li>
  <li class="mainList__item">
    <!-- _itemLink = Element -->
    <a class="mainList__itemlink" href="/works">Works</a>
  </li>
</ul>
```

```css
.mainList {
  display: flex;
  justify-content: space-between;
  &--xmas {
    background: green;
  }
  &__item {
    list-style: none;

  }
  &__itemLink {
    color: red;
    &--isActive {
      color: white;
    }
  }
}
```

Exemple du CSS du rendu :

```css
.mainList {

}
.mainList--xmas {

}
.mainList__item {

}
.mainList__itemLink {

}
.mainList__itemLink--isActive {

}
```

## Pseudo attributs

Les pseudos attributs `before` et `after` permettent de crééer des noeuds HTML en CSS.
Ils sont essentiellemeents utilisés pour ajouter des ornements, des décorations ...
On peut bien entendu faire des animations avec, les positionner par rapport à leur parent
(relative/absolute). **Ils doivent obligatoirement avoir un `content:''`**
afin de s'afficher.

```html
<section class="cover">
  <h1 class="cover__mainTitle">Présentation des pseudos attributs</h1>
</section>
```

```css
.cover {
  background: #FDFDFD;
  padding: 20px;
  &__mainTitle {
    text-align: center;
    font-size: 24px;
    color: green;
    position: relative;
    &::before,
    &::after {
      content: '';
      display: block;
      width: 50px;
      height: 50px;
      background: green;
      top: 0;
    }
    &::before {
      left: 0;
    }
    &::after {
      right: 0;
    }
  }
}
```


## REM, EM, %, VW Sizing

### EM

* Relative à la taille de son parent direct.

```css
.cover {
  font-size: 100%; /*100% = 16px */
  &__mainTitle {
    /*1 em = 16px / .8em ≠ 16px*/
    font-size: .8em
  }
}
```

### REM

* Le REM est basé sur la taille de la racine (soit la balise <html>) qui, par défaut
a une valeur de 16px. Afin d'éviter tout calcul, il est nécessaire de l'écraser
en donnant une base de 10px soit 62,5%.

* Le REM est interessant à utiliser si les médias-queries employées sont en REM
également. Cela vous permettra de garder les proportions égales lorsqu'on va
redimensionner la page.

* Ses proportions seront également gardées quand l'utilisateur zoomera dans votre
page.

```css
/* 62,5% = 10px*/
 html {
  font-size: 62.5%
}
.mainTitle {
  /* 1.6rem =16px*/
  font-size: 1.6rem;
  /* 32rem = 320px */
  width: 32rem
}

```

### VW(idth)/ VH(eight)

* Unités relatives à la taille de votre écran (peu importe le device)

* Attention au VH et à son contenu. 100vh = 100vh quoiqu'il arrive.

* VW : très utile pour les interfaces fluides.

## Work with github 

### Issues

* cloner le projet
```
git clone 
````
* Créer une branche (ne jamais travailler sur master)
``` 
git checkout -b name-lastName
```
* Résoudre les issues sur la branche 
* 1 commit = 1 issue 
``` 
git add . 
git commit -m “fixes issue #12”
git add . 
git commit -m “fixes issue #36”
```
* apres avoir fix les issues et commit 
``` 
git push origin name-lastName
```
* créer une pull request --> recap des fichiers et des modifications
* quand otut terminé, request a review

## CSS Tips 

### Proporiétés z-index

* définit le « z-order » (NdT : « ordre z » n'est pas usité) d'un élément positionné et de ses éléments fils. 
* Lorsque des éléments se chevauchent, le z-order détermine l'ordre des différentes couches que formeront les éléments
* Généralement, un élément couvrira un autre élément si sa valeur de  z-index est supérieure à celle du deuxième élément.

### Font-face 

c'est quoi ?

* La règle font-face permet aux utilisateurs d’intégrer des polices non-système* aux sites. 
C’est une fonction du CSS3 qui rend transparente toutes les polices.
*police non-système : police qui n’est pas installée sur les systèmes d’ordinateurs PC & Mac.

Comment ca fonctionne ?

* Tout d’abord, la fonction @font-face s’utilise dans la partie style de l’integration, dans le CSS. 
Il faut choisir une police non-système que l’on souhaite utiliser. 

* Je souhaite que mon paragraphe <p>Ceci est mon seul et unique paragraphe.</p> dans mon HTML soit en “Montserrat ExtraLight”
* Ensuite, on déclare dans le CSS la police voulue en incluant dans la fonction la source de la police en format .woff (Web Open File Format), .woff2, .ttf…

```
@font-face { font-family: “Montserrat_ExtraLight”;
src: url(‘../fonts/montserrat-v12-latin-extralight.woff’); }
```

* Enfin, on choisit où la police sera utilisée :
```
p {font-family : Montserrat_ExtraLight;}
```
Une limite 

* Le fichier de la police est chargé avec le chargement de la page ce qui peut rendre le chargement plus lent qu’une page normale.


## Liens utiles :

* [Caniuse]: https://caniuse.com/#feat=viewport-units

