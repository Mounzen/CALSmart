# CAL Smart — Saint-Denis

Application de matching logement social, gestion CAL, suivi audiences élus et notifications territoriales.

---

## Installation (une seule fois)

```bash
cd CALSmart
npm install
```

---

## Lancement

```bash
npm run dev
```

Ouvre ensuite **http://localhost:3000** dans ton navigateur.

- Le client React tourne sur le port **3000**
- Le serveur Express tourne sur le port **4000**
- Les deux se lancent automatiquement avec `npm run dev`

---

## Structure du projet

```
CALSmart/
├── package.json          ← scripts et dépendances
├── vite.config.js        ← config frontend + proxy API
├── index.html            ← point d'entrée HTML
├── src/
│   ├── main.jsx          ← montage React
│   └── CALSmart.jsx      ← toute l'application
└── server/
    ├── index.js          ← serveur Express (API)
    └── data/
        ├── demandeurs.json
        ├── logements.json
        ├── audiences.json
        ├── notifications.json
        └── referentiels.json   ← élus, contingents, motifs refus, etc.
```

---

## Routes API disponibles

| Méthode | Route | Description |
|---------|-------|-------------|
| GET | /api/dashboard | KPIs globaux |
| GET | /api/demandeurs | Liste des demandeurs |
| GET | /api/demandeurs/:id | Fiche demandeur |
| POST | /api/demandeurs | Nouveau demandeur |
| PUT | /api/demandeurs/:id | Modifier un demandeur |
| GET | /api/logements | Liste des logements |
| POST | /api/logements | Nouveau logement |
| PUT | /api/logements/:id | Modifier un logement |
| GET | /api/matching/:logement_id | Matching + scores pour un logement |
| GET | /api/audiences | Liste des audiences |
| POST | /api/audiences | Nouvelle audience |
| PUT | /api/audiences/:id | Modifier une audience |
| GET | /api/notifications | Notifications élus |
| PUT | /api/notifications/:id/lu | Marquer comme lue |
| GET | /api/elus | Liste des élus |
| GET | /api/referentiels | Toutes les listes de référence |

---

## Données

Toutes les données sont stockées dans `server/data/` en JSON.  
Elles sont lues et écrites directement par le serveur — pas de base de données nécessaire pour démarrer.

Pour passer en base de données (SQLite ou PostgreSQL), remplacer les fonctions `readData` / `writeData` dans `server/index.js`.

---

## Prochaines étapes possibles

- [ ] Authentification par profil (agent / élu / direction)
- [ ] Export PDF fiche CAL
- [ ] Connexion SNE (registre national de demande)
- [ ] Base de données PostgreSQL
- [ ] Envoi SMS/email réel (Twilio / Brevo)
- [ ] Carte territoriale interactive (Leaflet)
