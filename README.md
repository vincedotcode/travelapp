# MoTravel ✈️

**Flights, hotels and taxis in one booking platform — with an AI vacation planner that actually reads your preferences.**

[**Live demo**](https://motravel.vercel.app) · [**API docs (Swagger)**](https://travelapp-rvy5.onrender.com/api-docs/)

> The frontend is confirmed live. The Swagger instance is on Render's free tier, which spins down when idle — expect a cold start of up to a minute, and verify it still exists before pointing anyone at it.

---

## What it does

MoTravel is a full travel-booking platform, not a mockup. It talks to **real flight inventory through the Amadeus API**, handles payment through Stripe, and stores bookings, hotels and users in MongoDB.

### Flights
Search by origin, destination, dates and traveller count against live Amadeus data, then book with integrated payment.

### Hotels
Two-sided: travellers browse, filter and book rooms; hotel owners register properties, define room types, amenities and pricing, and manage their listings.

### Taxis
Drivers register and set their availability. Travellers specify pickup points and get matched — routing is drawn on the map with Leaflet Routing Machine.

### AI vacation planner
Built on the Vercel AI SDK with OpenAI. Takes your preferences and constraints and returns a concrete itinerary — suggested flights, hotels and activities — rather than generic travel prose.

### Carbon emissions tracking
Trips are scored for their carbon footprint, so the cheapest itinerary isn't the only one you can compare on.

### Reviews
Travellers leave feedback on hotels, which feeds back into browse and search.

---

## Stack

**Frontend** — Next.js 14 (App Router), TypeScript, Tailwind CSS, shadcn/ui + Radix, Framer Motion, React Hook Form + Zod, Leaflet & Leaflet Routing Machine for maps

**Backend** — Node.js, Express, MongoDB (Mongoose), JWT auth with bcrypt, Multer + Cloudinary for uploads, Nodemailer for transactional mail

**Integrations** — Amadeus (flight search & booking), Stripe (payments), OpenAI + Vercel AI SDK (itinerary planning), Google Generative AI

**Docs** — Swagger (`swagger-jsdoc` + `swagger-ui-express`), served at `/api-docs`

---

## Repository layout

```
travelapp/
├── client/     # Next.js frontend
└── server/     # Express API + Swagger docs
```

---

## Running locally

**Prerequisites:** Node.js 18+, a MongoDB instance (local or Atlas), and API keys for Amadeus, Stripe and OpenAI.

```bash
git clone https://github.com/vincedotcode/travelapp.git
cd travelapp
```

**Backend**

```bash
cd server
npm install
cp .env.example .env      # fill in the values below
npm run dev               # nodemon
```

Required environment variables:

```bash
MONGODB_URI=
JWT_SECRET=
AMADEUS_CLIENT_ID=
AMADEUS_CLIENT_SECRET=
STRIPE_SECRET_KEY=
OPENAI_API_KEY=
CLOUDINARY_CLOUD_NAME=
CLOUDINARY_API_KEY=
CLOUDINARY_API_SECRET=
```

API docs are then at `http://localhost:<PORT>/api-docs`.

**Frontend**

```bash
cd ../client
npm install
npm run dev
```

Open `http://localhost:3000`.

---

## Notes

Built solo over roughly two weeks. The Amadeus integration is the part worth reading if you're only reading one thing — flight search, offer pricing and booking confirmation are three separate calls with their own failure modes, and the reconciliation between them is where most of the complexity lives.

---

## License

MIT — see [LICENSE](LICENSE).

## Contact

Vince Erkadoo — [vincedotcode.com](https://vincedotcode.com) · [vince@vincedotcode.com](mailto:vince@vincedotcode.com)
