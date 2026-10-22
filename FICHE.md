---
id: 2026-10-22-calcul-de-temperature-de-reference   # AAAA-MM-JJ-slug, écrit une fois, jamais modifié (même si le dossier bouge)
nom: Températures de référence                      # nom affiché
type: application                                   # application | outil | documentation | travail | affaire
statut: actif                                       # idee | actif | pause | termine | abandonne
pitch: Température extérieure de base hiver (NF P52-612/CN) et été d'un site, depuis son adresse ou son département.  # une phrase sur une seule ligne, 120 caractères maximum
cree: 2026-10-22                                    # AAAA-MM-JJ
maj: 2026-10-22                                     # AAAA-MM-JJ, mis à jour par Claude Code en fin de session
tags: [cvc, chauffage, climatisation, reglementation]  # exemple : [cvc, reglementation]
stack: HTML + CSS + JS vanilla, une seule page, sans build
lancer: ouvrir index.html
site: https://mamalric.github.io/temperatures-reference/
depot: https://github.com/mamalric/temperatures-reference
---

# Températures de référence

## Objectif
Donner en quelques secondes les températures extérieures de base d'un site en France, pour le dimensionnement du chauffage et de la climatisation. L'hiver suit la norme (NF EN 12831 et son complément national NF P52-612/CN), l'été est calculé sur le climat local faute de table normative. Outil de travail pour les ingénieurs fluides et CVC de B27, publié sur le portail Outils B27 dans le groupe Chauffage.

## État actuel
Version 1 en ligne sur GitHub Pages, publiée depuis `main`, et vérifiée dans le navigateur, en local comme en ligne. Le site se saisit par adresse, par commune, par région et département, ou par un clic sur la carte (fond Plan IGN). L'altitude est lue au point (IGN RGE ALTI, repli Copernicus DEM) et reste modifiable. Hiver : valeur départementale au niveau de la mer (tableau D.1a), puis valeur de la tranche d'altitude (tableau D.1b), avec la ligne "côte à moins de 25 km" en option et une extrapolation signalée au-delà de la dernière tranche renseignée. Été : température sèche dépassée 0,4 %, 1 % ou 2 % des heures sur 10, 20 ou 30 ans de données horaires ERA5 au point du site (Open-Meteo), avec la température humide coïncidente, l'écart diurne des jours chauds et le maximum de la période. Un bouton copie le résultat en texte. L'outre-mer est accepté pour l'été, l'hiver y est déclaré non applicable.

## Prochaine étape
Confronter les valeurs d'hiver au texte de la NF P52-612/CN, en particulier 92, 93 et 94 (pris à -5 °C d'après la carte, -7 °C dans le tableau relevé) et le cas de l'Aveyron au sud de son cours. Comparer la base été à des données de station Météo-France sur deux ou trois affaires.

## Utilisation
En ligne : https://mamalric.github.io/temperatures-reference/ (GitHub Pages, publié depuis `main`). Hors ligne : ouvrir index.html dans un navigateur. Il faut une connexion internet pour la carte, la recherche d'adresse, l'altitude et le calcul d'été. Sans réseau, seul le mode département avec l'altitude saisie à la main donne la valeur d'hiver. Open-Meteo est gratuit pour un usage non commercial uniquement.
