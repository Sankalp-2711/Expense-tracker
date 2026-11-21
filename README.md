# Expense Tracker (MERN)

A full-stack expense tracker for recording income and expenses and viewing a live balance. The React front end talks to an Express REST API backed by MongoDB.

## Features

- Add income (positive amount) and expense (negative amount) transactions
- Live balance, total income and total expense, recalculated on every change
- Transaction history list with delete
- Server-side validation with clear error messages

## Tech Stack

| Layer    | Technology                                    |
| -------- | --------------------------------------------- |
| Frontend | React 16, Context API + `useReducer`, Axios   |
| Backend  | Node.js, Express 4                            |
| Database | MongoDB with Mongoose 5                       |
| Tooling  | nodemon, concurrently, morgan                 |

## API

Base path: `/api/v1/transactions`

| Method | Endpoint | Description            |
| ------ | -------- | ---------------------- |
| GET    | `/`      | Get all transactions   |
| POST   | `/`      | Add a transaction      |
| DELETE | `/:id`   | Delete a transaction   |

Transaction fields: `text` (string, required), `amount` (number, required), `createdAt` (date, set automatically).

## Project Structure

```
.
├── config/          # Database connection
├── controllers/     # Request handlers
├── models/          # Mongoose schemas
├── routes/          # Express routes
├── server.js        # App entry point
└── client/          # React front end
    └── src/
        ├── components/   # Balance, IncomeExpenses, TransactionList, ...
        ├── context/      # Global state (Context API + reducer)
        └── utils/        # Formatting helpers
```

## Getting Started

### Prerequisites

- Node.js and npm
- A MongoDB database (local instance or MongoDB Atlas)

### Setup

1. Install dependencies:

   ```bash
   npm install
   cd client
   npm install
   cd ..
   ```

2. Create `config/config.env` (this file is gitignored):

   ```env
   NODE_ENV=development
   PORT=5000
   MONGO_URI=your_mongodb_connection_string
   ```

### Run

| Command          | What it does                                |
| ---------------- | ------------------------------------------- |
| `npm run dev`    | Run the API and the React app together      |
| `npm run server` | Run the API only (with nodemon)             |
| `npm run client` | Run the React app only                      |

The React dev server runs on http://localhost:3000 and proxies API calls to port 5000.

### Production

```bash
cd client
npm run build
cd ..
# set NODE_ENV=production in config/config.env
npm start
```

In production, Express serves the built React app from `client/build`.

## Possible Improvements

- Edit existing transactions
- Spending categories and category-wise summaries
- Charts for spending trends
- User authentication

## License

[ISC](LICENSE)
