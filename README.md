# Registre de predictions, marches publics francais

Chaque semaine, les avis de marche parus au BOAMP passent dans un modele qui estime la
probabilite que le marche soit attribue a une entreprise du departement de l'acheteur.
**Les predictions sont ecrites ici avant que le resultat existe, et elles ne sont jamais
reecrites.** Le commit git qui les depose fait l'horodatage : n'importe qui peut verifier,
dans l'historique de ce depot, qu'une phrase a bien ete ecrite avant l'attribution
qu'elle annonce.

La page lisible : **https://marche.ducens.io**

## Ce que contient ce depot

- `registre/AAAA-MM-JJ.json` : un fichier par journee de parution. Chaque avis y porte son
  identifiant BOAMP, son acheteur, son objet, son code CPV, la probabilite estimee, le
  verdict s'il y en a un, et un bloc `pourquoi` qui publie **le passe de l'acheteur
  lui-meme** : la part de ses marches deja partis dans son propre departement, et le
  nombre de marches sur lequel cette part est calculee. Ce chiffre se recalcule depuis
  l'open data par n'importe qui, et il est la pour une raison precise : c'est le seul
  moyen de voir, ligne par ligne, quand le modele annonce l'inverse de ce que l'histoire
  de cet acheteur laissait attendre. Ce sont ces lignes-la qui jugeront la methode.
- `index.html` : la page, statique, sans JavaScript, regeneree a chaque mise a jour.

## Les trois questions posees a chaque avis

Chacune recoit une phrase entiere, que l'avis d'attribution rendra vraie ou fausse.

| La question | La phrase ecrite | Comment on saura |
|---|---|---|
| Ou part l'argent | *ce marche ira a une entreprise du departement de l'acheteur*, ou *il ira ailleurs* | L'avis d'attribution donne le departement de l'entreprise retenue |
| La place est-elle prise | *un fournisseur deja retenu par cet acheteur va regagner*, ou *la place est ouverte* | L'avis d'attribution donne le nom du gagnant, on regarde s'il figure deja dans l'historique de cet acheteur |
| Combien de concurrents | *ce marche recevra deux offres ou moins*, ou *il en recevra plus* | L'avis d'attribution publie le nombre d'offres recues |

Une phrase n'est ecrite qu'au-dela de 80 % de certitude. En dessous, le fichier porte la
probabilite et rien d'autre : **le silence n'est pas une prediction et n'entre dans aucun
score.** La probabilite publiee sur la page est toujours celle de la phrase annoncee, pas
celle de l'evenement contraire.

## Ce qui a ete retire le 29 aout 2026, et ce qui ne l'a pas ete

Les treize premiers jours de ce depot publiaient, pour chaque avis, neuf variables
calculees par le modele. Elles en sont sorties le 29/08/2026, avec l'architecture du
modele et le bareme de comptage : mises cote a cote avec la probabilite, sur des milliers
d'avis, elles permettaient de reconstituer le modele sans corpus et sans travail.

**Aucune prediction, aucune probabilite, aucun verdict, aucune date n'a ete modifie.**
L'historique git de ce depot conserve les octets d'origine : le diff est public et
n'importe qui peut verifier que seules des variables explicatives ont ete retirees. C'est
volontairement cette forme-la et pas une reecriture d'historique, qui aurait detruit la
seule chose que ce depot apporte.

## Ce qui n'est pas publie, et pourquoi

Aucun palmares nominatif d'acheteurs. La mesure porte sur une regularite statistique de
l'achat public, elle ne prouve aucun favoritisme et le critere qu'elle mesure n'est pas un
critere legal d'attribution. Les comptages sont agreges par territoire et par famille
d'achat, jamais rendus comme un jugement sur une collectivite nommee.

## Ce que ce depot dit contre lui-meme

Trois choses, ecrites ici parce qu'un bilan qu'on decouvre en 2027 ne vaut rien.

- **Sept des treize premiers jours, du 18 au 24 aout 2026, ne portent pas le numero du modele
  qui les a ecrits.** Le champ existait, il n'etait pas rempli. Ils ne sont pas reecrits : au
  bilan ces sept jours seront comptes a part, et pas melanges aux autres.
- **Trois modeles ont parle depuis le debut**, pas un seul. Le bilan comptera donc trois lots
  separes, et non une moyenne unique qui n'aurait aucun sens.
- **Les premiers jours ont ete ecrits plusieurs fois pendant la journee de construction du
  24 aout**, avant que le protocole du non-reecrit prenne effet le soir meme. Aucun resultat
  n'existait alors, donc la propriete qui compte, predire avant de savoir, tient pour eux
  aussi. Mais il fallait le dire.

## Le calendrier

Les premieres resolutions arrivent quand les avis d'attribution des marches de 2026
paraissent, a partir de la fin 2026 et surtout en 2027. Le delai median entre une
consultation et son attribution est de 136 jours. **Un bilan public sera publie le
31 aout 2027** : predits, resolus, non resolvables, et le gain sur le taux de base pour
chaque phrase, quel que soit le resultat.

## Donnees

Source : avis publies au BOAMP, donnees ouvertes. Les predictions et les comptages de ce
depot sont libres de reutilisation avec mention de leur origine et de leur date.
