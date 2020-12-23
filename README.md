# Data paper données radiométriques Takuvik et UQAR\ --- document de travail ---


## Liste des missions concernées
Les données des missions suivantes seront incluses dans la BdD
* CASES2004?
* Malina (2009)
* ArcticNet 2011,
* ArcticNet 2013,
* Tara Polar Circle 2013,
* Subice 2014),
* Arcticnet 2014?  (belles données COPS)
* Green Edge 2015 (ice camp),
* Green Edge 2016 (ice camp, Amundsen/open water, Amundsen/ice stations),
* International PhD School 2018 (“IPS2018”),
* BaySys 2018 (jeu très complet)
* Nunataryuk 2019 (“NUNAT2019”)


## Données et métadonnées
Les données radiométriques mesurées par le C-OPS (ou le IcePro ou SPMR) seront incluses dans la base de données. Il s’agit notamment de:
profondeur z
Ed(0+),
Ed(z),
Eu(z) ou Lu(z) en fonction de la configuration de l’instrument lors de chaque mission.

Les données seront des données nettoyées et lissées sur une grille de profondeur homogène. Les AOP (kd par exemple) n’en seront pas dérivées.

Les métadonnées associées suivantes seront également incluses:
* Date,
* (jour de l’année),
* Heure UTC,
* latitude,
* longitude,
* nom de la mission,
* plateforme de déploiement (nom du navire, camp ou station de glace, etc.),
* version instrumentale (C-OPS / IcePro),
* opérateur,
* nom du fichier (original si profils individuels, sinon ??? si profils moyennés),
* nom de la station,
* commentaire.


## Arborescence proposée
Les données vont être regroupées par mission, avec un sous répertoire par année / édition, tel qu’illustré sur le schéma ci-dessous:

<img src="https://user-images.githubusercontent.com/24660132/103030651-3d0ae800-452a-11eb-93ed-57e47672a960.png" width="23%"></img>

Chaque sous répertoire correspondant à une édition annuelle d’une mission particulière contiendra un dernier sous-répertoire par station, et chacun de ces sous-répertoires contiendra les fichiers suivants:
* `profile.txt` (données radiométriques le long de profils dans la colonne d’eau),
* `meta.txt` (metadonnées associées),
* `discrete.txt` (données non profilantes: CDOM, HyperSAS (?), SPM, etc.),
* `surface.txt` (données HyperSAS (inclure Ed0+ C-OPS/SPMR ici?)).

<img src="https://user-images.githubusercontent.com/24660132/103030653-3da37e80-452a-11eb-8cbe-6f0775aa715b.png" width="23%"></img> 

Les données incluses dans le fichier meta.txt seront les suivantes:
* Pigments (HPLC),
* aCDOM(443) et SCDOM (UltraPath),
* aNAP(443) et SNAP (filtres),
* a𝞿(𝞴) de 400 à 750 nm (filtres),
* SPM.

On envisage de ne pas limiter ces données à la surface, mais d’y inclure aussi les données correspondantes aux différentes profondeurs d’échantillonnage. Pour cela, on va ajouter un paramètre commun aux fichiers profile.txt et discrete.txt: depth_id. Ce paramètre permettra de faire correspondre les données contenues dans le fichier discrete.txt à celles contenues dans le fichier profile.txt, même si les profondeurs correspondantes ne sont pas strictement les mêmes (elles pourraient varier de quelques mm ou cm, par exemple).


## Liste “to-do”
- [ ]  Les données C-OPS / IcePro ont normalement toutes été traitées. Il se peut que certaines soient à vérifier (quelques petites erreurs ont été vues récemment, par exemple un décalage de 4h pour certaines données GreenEdge, ou un mauvais offset en profondeur appliqué pour toute une mission)
- [ ]  Rassembler toutes les données qui devront aller dans les fichiers discrete.txt
- [ ]  homogénéiser les données C-OPS/IcePro si besoin
- [ ]  homogénéiser les métadonnées
- [ ]  créer le paramètre depth_id et le populer
- [ ]  produire quelques graphiques de contrôle
