---
{"dg-home":true,"dg-publish":true,"permalink":"/application-coach/","tags":["gardenEntry"],"dgPassFrontmatter":true}
---



## Présentation du projet : 

Coach est une application **Xamarin** développé avec **Visual Studio code 2019** en **C#**.
Elle a pour but de prendre les saisies de l'utilisateur afin de calculer son IMC ( avec le sexe, taille, poids, age ) dans un interface graphique simple et intuitif.


## Création de la partie graphique : 

Pour la création graphique nous utiliserons un **RelativeLayout** qui englobera tout les **LinearLayout**. Nous ajusterons les Layout avec différente propriété tel que **minWidth** et **minHeight** qui permettent de gérer la taille du Layout :  

``` xml
<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout 
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:orientation="vertical"
    android:minWidth="25px"
    android:minHeight="25px"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:id="@+id/relativeLayout1">
        <LinearLayout
            android:orientation="horizontal"
            android:minWidth="25px"
            android:minHeight="25px"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:layout_weight="1"
            android:id="@+id/linearLayout4">
            <LinearLayout
                android:orientation="vertical"
                android:layout_weight="1"
                android:minWidth="25px"
                android:minHeight="25px"
                android:layout_width="wrap_content"
                android:layout_height="match_parent"
                android:id="@+id/linearLayout11"
                android:gravity="center_vertical">
                <ImageView
                    android:src="@drawable/Smiley_Ok"
                    android:layout_width="match_parent"
                    android:layout_height="wrap_content"
                    android:id="@+id/imageSmiley"/>
            </LinearLayout>
            <LinearLayout
                android:orientation="vertical"
                android:layout_weight="1"
                android:minWidth="25px"
                android:minHeight="25px"
                android:layout_width="wrap_content"
                android:layout_height="match_parent"
                android:id="@+id/linearLayout12">
                <TextView
                    android:text="Votre IMG :"
                    android:textSize="22sp"
                    android:layout_width="match_parent"
                    android:layout_height="match_parent"
                    android:gravity="center_vertical"
                    android:id="@+id/textIMG" />
            </LinearLayout>
        </LinearLayout>
    </LinearLayout>
</RelativeLayout>
```

Voici le résultat en interface graphique :

![App.png](/img/user/App.png)

L'encadré bleu fait référence à un **LinearLayout**, toute les parties de l'application sont divisées de cette façon ( un espace pour le sexe, pour les saisies utilisateur donc taille poids et age etc ).

**Remarque** : Le "Poids" d'un **LinearLayout** (**layout_weight**) est important, sans ça les Layout s'emboiteraient et rendraient l'application très peu lisible. En mettant le poids à 1, les 2 Layout partage l'espace de manière à ne pas s'emboiter l'un sur l'autre.

![code.png](/img/user/code.png)
## Modèle MVC : 

Le modèle d’architecture **Model-View-Controller (MVC)** sépare une application en trois groupes de composants principaux : **les modèles, les vues et les contrôleurs**. En utilisant ce modèle, les demandes de l’utilisateur sont acheminées vers un **contrôleur** qui a la responsabilité de fonctionner avec le **modèle** pour effectuer des actions de l’utilisateur et de récupérer les résultats de requêtes. Le contrôleur choisit la **vue** à afficher à l’utilisateur et lui fournit toutes les données de modèle dont elle a besoin.
![Model-View-Controller_architectural_pattern-fr.svg.png](/img/user/Model-View-Controller_architectural_pattern-fr.svg.png)
#### **Partie Modèle** :

Dans la partie modèle, nous créons la **class Profil** et ses différentes **méthodes**, ici nous pouvons voir le **constructeur** de la class Profil permettant d'initialiser les attributs privés de la classe : 
![67ebfa29d9628dac7a962899b2accce4.png](/img/user/67ebfa29d9628dac7a962899b2accce4.png)

Ainsi que les différentes méthodes, comme par exemple celle ci qui permet le calcule de l'IMG :

![57919c6dd5d0008937de6c9728f81f94.png](/img/user/57919c6dd5d0008937de6c9728f81f94.png)
Ou encore celle ci, qui permet d'adapter le message en fonction de l'IMG et du sexe :  

![83c8c6c7561b40ad3a6d7a018cf44962.png](/img/user/83c8c6c7561b40ad3a6d7a018cf44962.png)
#### **Partie Controleur** :

Dans la partie controleur, nous utiliserons les données du **modèle** qui seront transmis à la **vue**. Dans cette méthode, nous utilisons les données saisi par l'utilisateur pour crée un Profil :

![3ad3ddf46e65d14d9c1dafb1babcfaeb.png](/img/user/3ad3ddf46e65d14d9c1dafb1babcfaeb.png)

#### **Partie Vue** :

Pour la partie vue, il faut d'abord **déclarer** les **différentes propriétés** que nous avons dans la partie graphique : 
![7ed25de3e3fb13ecba294df807188f7f.png](/img/user/7ed25de3e3fb13ecba294df807188f7f.png)
Ensuite il faut **relier** ces propriétés avec celle de **l'interface graphique** : 

![0171f68554a8ef32ad89e397c9013ca0.png](/img/user/0171f68554a8ef32ad89e397c9013ca0.png)

La fonction **bt_Calculer_Click** sert à **vérifié** si les données transmises sont celles attendus : 

![bd222ffb0a572623d3bfe708c853490e.png](/img/user/bd222ffb0a572623d3bfe708c853490e.png)

Une fois les calculs fait, **un smiley** changera d'humeur par rapport à **l'IMG trouvé** : 

![dc526ebaedaf220081d66477390d0aff.png](/img/user/dc526ebaedaf220081d66477390d0aff.png)

Voici le **résultat** avec des exemples concret : 

![téléchargement (3).png](/img/user/t%C3%A9l%C3%A9chargement%20(3).png)
![téléchargement (4).png](/img/user/t%C3%A9l%C3%A9chargement%20(4).png)
![téléchargement (5).png](/img/user/t%C3%A9l%C3%A9chargement%20(5).png)


## Tests unitaires : 

Pour le calcul de l'IMC par exemple, nous avions besoin de vérifier le **bon fonctionnement des différents calculs**, c'est la qu'interviennent les **Test unitaires**, ils nous permettent de **comparer les valeurs attendus avec celle reçu par la fonction**  : 
![5cca737f3fb09c6ccc34561efbe00c23.png](/img/user/5cca737f3fb09c6ccc34561efbe00c23.png)
**Delta** est la marge accordé à l'erreur, donc ici de 0,1 d'interval.
Ensuite nous effecturons des tests pour chaque cas de figure : 
![8d27814216a592c950dd9335edcc6ed0.png](/img/user/8d27814216a592c950dd9335edcc6ed0.png)![46abf19a0c85da5d87be25edc05a32e9 1.png](/img/user/46abf19a0c85da5d87be25edc05a32e9%201.png)
![9738271e0d6169c5eba9b8ce079a759a 1.png](/img/user/9738271e0d6169c5eba9b8ce079a759a%201.png)