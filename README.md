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
  verdict s'il y en a un, et un bloc `pourquoi` qui publie les comptages sur lesquels le
  modele s'appuie.
- `index.html` : la page, statique, sans JavaScript, regeneree a chaque mise a jour.

## Les trois questions posees a chaque avis

**Ou va le marche** : partira-t-il a une entreprise du departement de l'acheteur.
**La place est-elle prise** : un fournisseur deja retenu par cet acheteur va-t-il regagner.
**Combien de concurrents** : le marche recevra-t-il deux offres ou moins.

Un verdict n'est inscrit qu'au-dela de 80 % de certitude. En dessous, le fichier porte la
probabilite et rien d'autre : **le silence n'est pas une prediction et n'entre dans aucun
score.**

## Comment les phrases sont comptees

Tout le monde ne compte pas pareil, alors la regle est ecrite ici. **Une phrase ne compte
que si elle gagne au moins vingt points sur ce qu'on obtiendrait sans modele** : une
annonce juste mais previsible est ecartee du decompte, meme quand elle est juste.

Sur cette regle, **24,2 % du flux recoit une phrase qu'un lecteur n'aurait pas pu
deviner**, dont 19,8 % pour la seule question de la localisation : **juste 94,4 % du temps
quand le taux de base est de 46 %**. Mesure du 26 aout 2026 sur 18 730 marches de test.

## Ce qui n'est pas publie, et pourquoi

Aucun palmares nominatif d'acheteurs. La mesure porte sur une regularite statistique de
l'achat public, elle ne prouve aucun favoritisme et le critere qu'elle mesure n'est pas un
critere legal d'attribution. Les comptages sont agreges par territoire et par famille
d'achat, jamais rendus comme un jugement sur une collectivite nommee.

## Le calendrier

Les premieres resolutions arrivent quand les avis d'attribution des marches de 2026
paraissent, a partir de la fin 2026 et surtout en 2027. Le delai median entre une
consultation et son attribution est de 136 jours. **Un bilan public sera publie en juillet
2027** : predits, resolus, non resolvables, et le gain sur le taux de base pour chaque
phrase, quel que soit le resultat.

## Donnees

Source : avis publies au BOAMP, donnees ouvertes. Les predictions et les comptages de ce
depot sont libres de reutilisation avec mention de leur origine et de leur date.
