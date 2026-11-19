# Journal

<!-- Dernière entrée en haut. Une entrée par session de travail ou par décision. Date au format AAAA-MM-JJ. -->

## 2026-11-19, la zone climatique
- Version 4, demande de Marius : le site affiche sa zone climatique RE2020 (H1a à H3) et sa classe d'altitude. Zones relevées dans la bibliothèque de textes, décret n° 2021-1004 du 29 juillet 2021, version initiale, annexe, chapitre IV (tableau des 96 départements métropolitains) ; le décret n° 2026-16 (tertiaire) renvoie à ce chapitre sans le modifier. Contrôle dans le navigateur : les 96 départements métropolitains ont chacun une zone, aucun en trop.
- Classes d'altitude du chapitre III du même décret, celles des coefficients de modulation géographique Mbgéo, Mcgéo et Migéo : le texte écrit "< 400m", "400m-800m" et ">800m" sans trancher les bornes exactes ; l'outil range 400 et 800 m dans la classe du milieu.
- Outre-mer : le décret ne vise que la métropole, la zone y est affichée "non applicable". La zone figure aussi dans le résultat copié et dans le panneau À propos (source et compteurs).
- Nouveau flocon, l'icône Lucide fournie par Marius, dans l'outil et sur l'image d'aperçu du lien. La source de cette image, perdue avec le dossier temporaire, est désormais rangée dans src/apercu.html avec la commande de rendu.
- Service d'altitude IGN lent ce jour (jusqu'à 10 s) : abandon au bout de 5 s et repli sur Copernicus DEM.
- Débordement en largeur sur téléphone corrigé : colonnes de grille autorisées à rétrécir (minmax(0, 1fr)) et tableau d'été défilable en largeur.
- Enregistré en local, pas poussé : en attente de l'accord de Marius.

## 2026-11-17, thème clair par défaut
- Demande de Marius pour toutes les calculettes B27 : la page s'ouvre en thème clair, le réglage sombre du système n'est plus suivi ; le bouton de bascule reste, et le choix qu'il mémorise dans le navigateur est gardé.
- Script du <head> (thème appliqué avant le premier rendu) et initTheme modifiés : plus de lecture de prefers-color-scheme ni d'écoute de son changement.
- Vérifié dans le navigateur avec un système réglé en sombre : page en clair, bascule et mémorisation du choix, console vide.

## 2026-10-22
- Création du projet : une page HTML autonome qui donne la température extérieure de base hiver et été d'un site, à partir d'une adresse, d'une commune, d'un département ou d'un clic sur la carte.
- Hiver : tableaux D.1a (valeur départementale au niveau de la mer) et D.1b (valeur par tranche d'altitude, ligne "côte à moins de 25 km") de la NF P52-612/CN, relevés dans la documentation DeperTherm 2015 de ThermExcel, faute d'accès au texte AFNOR. La table par zones A à I diffusée par plusieurs sites grand public est écartée : elle n'a pas de colonne -6 °C alors que quatre départements y sont (07, 26, 46, 84).
- Décision : 92, 93 et 94 pris à -5 °C, comme sur la carte de la norme qui les regroupe avec Paris ; le tableau relevé leur donne -7 °C. L'écart est signalé dans l'interface.
- Décision : au-delà de la dernière tranche renseignée pour une zone, la valeur est extrapolée sur le gradient moyen de la colonne et signalée comme à confirmer.
- Été : pas de table normative nationale trouvée. La valeur est calculée au point du site sur les données horaires ERA5 servies par Open-Meteo, ramenées à l'altitude saisie : température sèche dépassée 0,4 %, 1 % ou 2 % des heures (critères ASHRAE) et température humide coïncidente (formule de Stull).
- Vérifié dans le navigateur : Lyon -10 °C et 34,3 °C, Briançon à 1220 m -20 °C, Finistère en bord de mer -2 °C, Corse-du-Sud à 1200 m -8 °C extrapolée, Strasbourg -15 °C et 32,0 °C, Savoie à 650 m -14 °C, Guadeloupe hiver non applicable.
- Publication : dépôt public https://github.com/mamalric/temperatures-reference, GitHub Pages depuis `main`, fichier renommé en index.html. Carte ajoutée au portail Outils B27 dans le groupe Chauffage, avec le mot-clé "climatisation" pour la recherche.
- Correction après le test en ligne : au clic sur la carte, le département attendait la réponse du service d'altitude ; les deux requêtes partent maintenant ensemble.
- Version 2, aux couleurs des outils B27 : palette, polices, en-tête, cadres, cases à cocher, bouton de thème et panneau À propos repris de la Calculette ECS et du Sélectionneur de radiateurs. Le contrôle "climat local" de la valeur d'hiver est retiré : il demandait les données d'hiver, que l'on ne télécharge plus.
- Limite Open-Meteo atteinte par l'utilisateur ("Minutely API request limit exceeded") : l'accès gratuit compte une requête par tranche de 14 jours, et dix années entières en coûtaient 260 sur un plafond de 600 par minute, chaque changement d'altitude relançant tout. Correction : seuls mai à septembre sont téléchargés (une requête par été, environ 110 pour 10 ans), le seuil restant calculé sur les heures de l'année entière ; l'altitude est corrigée en local à -6,5 K/km, point de rosée conservé, sans nouvelle requête ; en cas de plafond atteint, message explicite et nouvel essai automatique au bout d'une minute. Vérifié sur Lyon : valeurs identiques au calcul sur l'année entière (34,3, 32,3 et 30,5 °C).
- Favicon en SVG, PNG 32 px, ICO et icône Apple 180 px ; image d'aperçu du lien en 1200 x 630 (apercu.jpg) avec les balises Open Graph. Même image d'aperçu ajoutée au portail Outils B27, qui n'en avait pas.
- Version 3 : le niveau de dépassement n'était pas compris. Bouton (i) à côté du choix, sur la mécanique d'aide de la Calculette ECS : nombre d'heures par an au-dessus de la valeur (35, 88 et 175 h), valeurs du site une fois calculées, niveau à choisir selon l'usage (0,4 % pour les locaux sensibles, 1 % pour le confort tertiaire, 2 % pour le logement) et maximum de la période pour comparaison. Un second clic sur le bouton referme l'aide.
- Reste à faire : confronter les valeurs d'hiver au texte de la norme (92, 93, 94 et Aveyron) et la base été à des données de station Météo-France.
