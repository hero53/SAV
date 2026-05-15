##Contexte

Les trajets Plateau-Bingerville, Adjamé-, ou même Cocody-Yopougon coûtent cher et les routes sont souvent encombrées. Le covoiturage est une solution évidente, mais il n'existe pas encore d'app dédiée bien conçue pour le marché ivoirien. Vous allez construire le MVP de cette app.

##Votre défi
Livrer en 1 heure une web app de covoiturage où un conducteur peut publier un trajet (départ, arrivée, date, prix, places) et où un passager peut chercher un trajet et envoyer une demande de réservation.

##Étapes
Setup et structure (5 min) : Créez le repository ivoireride. Choisissez votre stack. Structurez l'app en 3 écrans : (1) liste/recherche de trajets, (2) publication d'un trajet, (3) détail d'un trajet avec demande de réservation. Pas de vraie auth pour le MVP : un simple champ « nom » suffit.
Stockage local des trajets (10 min) : Utilisez localStorage pour persister les trajets (pas de backend nécessaire pour le MVP). Demandez à Copilot Chat : « Crée un module tripsStore.js avec les fonctions addTrip, getTrips, searchTrips, addBookingRequest. Toutes les données dans localStorage sous une clé unique. » Pré-remplissez avec 5 à 10 trajets fictifs (Abidjan-Yamoussoukro, Cocody-Plateau, etc.) au premier lancement.
Publication d'un trajet avec géocodage (10 min) : Le formulaire de publication doit avoir : ville de départ, ville d'arrivée, date/heure, prix par place, nombre de places, nom du conducteur, téléphone. Pour les villes, utilisez Nominatim (https://nominatim.openstreetmap.org/search) pour récupérer les coordonnées GPS. Demandez à Copilot un composant d'autocomplétion qui appelle Nominatim avec debounce.
Carte et itinéraire (15 min) : Sur l'écran de détail, affichez une carte Leaflet avec le marqueur départ, le marqueur arrivée, et le tracé de l'itinéraire routier. Utilisez OSRM (sans clé) : https://router.project-osrm.org/route/v1/driving/lon1,lat1;lon2,lat2?overview=full&geometries=geojson. Affichez aussi la distance et la durée estimée. Copilot connaît bien Leaflet, demandez-lui le code complet.
Recherche et filtres (10 min) : Sur l'écran de liste, ajoutez des filtres : ville de départ, ville d'arrivée, date. Affichez chaque trajet avec : conducteur, horaire, prix, places disponibles, bouton « Voir ». Bouton « Réserver » sur le détail qui simule une demande (ajout dans localStorage + alerte de confirmation).
Déploiement et démo (10 min) : Pushez sur GitHub. Déployez sur GitHub Pages (si Vite/CRA, buildez le dist et utilisez l'action GitHub Pages). Testez le cycle complet : publier → chercher → réserver. Préparez la démo avec un trajet Abidjan → Bouaké.

##Livrable
Une web app déployée en ligne où on peut publier un trajet, chercher des trajets, voir l'itinéraire sur carte, et simuler une réservation. Données persistées en localStorage.