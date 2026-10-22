# Journal

<!-- Dernière entrée en haut. Une entrée par session de travail ou par décision. Date au format AAAA-MM-JJ. -->

## 2026-10-22
- Création du projet : une page HTML autonome qui donne la température extérieure de base hiver et été d'un site, à partir d'une adresse, d'une commune, d'un département ou d'un clic sur la carte.
- Hiver : tableaux D.1a (valeur départementale au niveau de la mer) et D.1b (valeur par tranche d'altitude, ligne "côte à moins de 25 km") de la NF P52-612/CN, relevés dans la documentation DeperTherm 2015 de ThermExcel, faute d'accès au texte AFNOR. La table par zones A à I diffusée par plusieurs sites grand public est écartée : elle n'a pas de colonne -6 °C alors que quatre départements y sont (07, 26, 46, 84).
- Décision : 92, 93 et 94 pris à -5 °C, comme sur la carte de la norme qui les regroupe avec Paris ; le tableau relevé leur donne -7 °C. L'écart est signalé dans l'interface.
- Décision : au-delà de la dernière tranche renseignée pour une zone, la valeur est extrapolée sur le gradient moyen de la colonne et signalée comme à confirmer.
- Été : pas de table normative nationale trouvée. La valeur est calculée au point du site sur les données horaires ERA5 servies par Open-Meteo, ramenées à l'altitude saisie : température sèche dépassée 0,4 %, 1 % ou 2 % des heures (critères ASHRAE) et température humide coïncidente (formule de Stull).
- Vérifié dans le navigateur : Lyon -10 °C et 34,3 °C, Briançon à 1220 m -20 °C, Finistère en bord de mer -2 °C, Corse-du-Sud à 1200 m -8 °C extrapolée, Strasbourg -15 °C et 32,0 °C, Savoie à 650 m -14 °C, Guadeloupe hiver non applicable.
- Publication : dépôt public https://github.com/mamalric/temperatures-reference, GitHub Pages depuis `main`, fichier renommé en index.html. Carte ajoutée au portail Outils B27 dans le groupe Chauffage, avec le mot-clé "climatisation" pour la recherche.
- Correction après le test en ligne : au clic sur la carte, le département attendait la réponse du service d'altitude ; les deux requêtes partent maintenant ensemble.
- Reste à faire : confronter les valeurs d'hiver au texte de la norme (92, 93, 94 et Aveyron) et la base été à des données de station Météo-France.
