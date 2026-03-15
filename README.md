# FitTracker — School Project

Een volledige fitness webapplicatie met Express.js backend, Prisma ORM en vanilla HTML/CSS/JS frontend.

## 🗂️ Projectstructuur

```
fittracker/
├── backend/
│   ├── middleware/
│   │   └── auth.js              # JWT verificatie middleware
│   ├── prisma/
│   │   ├── schema.prisma        # Database schema
│   │   └── seed.js              # Database seeding (18 oefeningen)
│   ├── routes/
│   │   ├── auth.js              # POST /register, POST /login, GET /me
│   │   ├── exercises.js         # GET /, GET /muscle/:group, GET /:id
│   │   ├── workouts.js          # GET /, POST /, DELETE /:id
│   │   ├── planner.js           # GET /, POST /, DELETE /:id
│   │   └── generator.js         # POST / — genereert weekschema
│   ├── .env                     # DATABASE_URL + JWT_SECRET
│   ├── package.json
│   └── server.js
└── frontend/
    ├── css/
    │   ├── global.css           # Design system, navbar, footer
    │   ├── index.css            # Homepage stijlen
    │   ├── exercises.css        # Oefeningen pagina stijlen
    │   ├── generator.css        # Generator wizard stijlen
    │   ├── calendar.css         # Planner/kalender stijlen
    │   └── login.css            # Login/register stijlen
    ├── js/
    │   ├── api.js               # Auth helpers + fetch wrapper
    │   ├── exercises.js         # SVG anatomie + oefeningen logica
    │   ├── generator.js         # Wizard + resultaten logica
    │   ├── calendar.js          # Planner week view logica
    │   └── login.js             # Login/register formulier logica
    ├── pages/
    │   ├── exercises.html       # Anatomie SVG + oefeningen
    │   ├── generator.html       # 5-staps workout generator
    │   ├── calendar.html        # Week planner
    │   └── login.html           # Login + registreren
    └── index.html               # Homepage
```

## Installatie & Opstarten

### Vereisten
- Node.js v18+
- npm

### Stappen

```bash
# 1. Ga naar de backend map
cd backend

# 2. Installeer dependencies
npm install

# 3. Genereer Prisma client
npx prisma generate

# 4. Maak de database aan
npx prisma migrate dev --name init

# 5. Vul de database met voorbeeldoefeningen
node prisma/seed.js

# 6. Start de server
npm run dev
```

De app is nu beschikbaar op: **http://localhost:3000**

## 🔗 API Endpoints

| Method | Endpoint | Beschrijving | Auth? |
|--------|----------|--------------|-------|
| POST | /api/auth/register | Account aanmaken | Nee |
| POST | /api/auth/login | Inloggen | Nee |
| GET | /api/auth/me | Huidige gebruiker | Ja |
| GET | /api/exercises | Alle oefeningen | Nee |
| GET | /api/exercises?muscleGroup=chest | Filter op spiergroep | Nee |
| GET | /api/exercises?search=push | Zoeken | Nee |
| GET | /api/exercises/:id | Oefening op ID | Nee |
| GET | /api/planner | Geplande workouts | Ja |
| POST | /api/planner | Workout plannen | Ja |
| DELETE | /api/planner/:id | Workout verwijderen | Ja |
| POST | /api/generator | Weekschema genereren | Nee |

## 🎯 Kernfuncties

1. **Interactieve anatomie** — Klikbare SVG spiergroepen die oefeningen filteren
2. **Workout Planner** — Weekkalender om workouts op datum op te slaan
3. **Workout Generator** — 5-vragen wizard die een persoonlijk weekschema genereert
4. **Authenticatie** — JWT-gebaseerde login/registratie met gehashte wachtwoorden
5. **Zoekfunctie** — Realtime zoeken op naam en spiergroep

## 🛠️ Tech Stack

- **Backend**: Node.js, Express.js, Prisma ORM, SQLite
- **Auth**: JWT (jsonwebtoken), bcryptjs
- **Frontend**: Vanilla HTML, CSS, JavaScript
- **Fonts**: Bebas Neue, Barlow Condensed, Barlow
