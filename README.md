# 📈 Full-Stack Stock Trading Simulator

A **full-stack stock trading simulator** that allows users to view real-time stock prices, simulate buying and selling stocks, track portfolio performance, and analyze profit/loss using interactive dashboards.

This project mimics the core functionality of modern trading platforms like Robinhood or TradingView and demonstrates backend engineering, real-time data handling, and financial data modeling.

---

# 🚀 Features

### Authentication

* Secure user registration and login
* JWT-based authentication
* Password hashing using bcrypt

### Stock Market Data

* Fetch real-time stock prices using external APIs
* Display historical stock data
* Interactive stock charts

### Trading System

* Buy and sell stocks with virtual currency
* Wallet balance management
* Transaction validation and order processing

### Portfolio Management

* Track owned stocks
* Calculate portfolio value
* Profit/Loss analytics
* Portfolio performance charts

### Real-Time Updates

* Live stock price updates using WebSockets
* Instant UI updates for trading activity

### Transaction History

* Complete trading history
* Timestamped buy/sell records

---

# 🏗️ System Architecture

```
React Frontend
      |
REST API + WebSockets
      |
Node.js / Express Backend
      |
PostgreSQL Database
      |
External Stock Market API
```

---

# 🗄️ Database Schema

### Users

```
id
name
email
password_hash
created_at
```

### Wallets

```
id
user_id
balance
```

### Stocks

```
id
symbol
name
exchange
```

### Holdings

```
id
user_id
stock_id
quantity
avg_buy_price
```

### Orders

```
id
user_id
stock_id
type (BUY/SELL)
price
quantity
status
created_at
```

### Transactions

```
id
user_id
stock_id
price
quantity
total_amount
type
created_at
```

Financial systems follow an **append-only transaction model**, meaning past transactions are never modified.

---

# 🔌 Backend API Endpoints

## Authentication

```
POST /auth/register
POST /auth/login
GET /auth/me
```

---

## Stock Data

```
GET /stocks
GET /stocks/:symbol
GET /stocks/:symbol/history
```

---

## Trading

```
POST /orders/buy
POST /orders/sell
GET /orders
```

---

## Portfolio

```
GET /portfolio
GET /portfolio/value
GET /portfolio/history
```

---

# ⚙️ Trading Engine Logic

### Buy Flow

1. Check user wallet balance
2. Fetch latest stock price
3. Deduct balance from wallet
4. Update holdings
5. Record transaction

---

### Sell Flow

1. Verify user holdings
2. Fetch stock price
3. Update holdings
4. Credit wallet balance
5. Record transaction

---

### Edge Cases Handled

* Insufficient wallet balance
* Selling stocks not owned
* Concurrent trading requests
* Transaction validation

---

# 📊 Portfolio Analytics

### Portfolio Value

```
portfolio_value = Σ(quantity × current_price)
```

### Profit / Loss

```
profit_loss = current_value - invested_amount
```

### Analytics Dashboard

* Portfolio growth chart
* Asset allocation
* Daily P/L tracking

---

# ⚡ Performance Optimizations

### Redis Caching

Used to cache frequently requested stock price data.

### Database Indexing

Indexes created on:

```
user_id
stock_id
created_at
```

### Rate Limiting

Prevents API abuse using request throttling.

---

# 🖥️ Frontend Pages

### Dashboard

Displays:

* Wallet balance
* Portfolio value
* Top market stocks
* Daily profit/loss

---

### Stock Details Page

Shows:

* Live stock price
* Historical charts
* Buy / Sell trading panel

---

### Portfolio Page

Displays:

```
Stock
Quantity
Average Price
Current Price
Profit/Loss
```

---

### Transaction History

Shows:

* Buy transactions
* Sell transactions
* Order timestamps

---

# 🛠️ Tech Stack

### Frontend

* React.js
* Chart.js / Recharts
* Socket.io Client

### Backend

* Node.js
* Express.js
* WebSockets (Socket.io)

### Database

* PostgreSQL

### Caching

* Redis

### Authentication

* JWT
* bcrypt

---

# 🌐 Deployment

Frontend

* Vercel

Backend

* Render / Railway / AWS

Database

* Supabase / Neon PostgreSQL

---

# 📂 Project Structure

### Backend

```
src/
  controllers/
  services/
  routes/
  middleware/
  models/
  utils/
```

---

### Frontend

```
src/
  components/
  pages/
  hooks/
  services/
  context/
```

---

# 🔮 Future Improvements

* Limit orders
* Stock watchlist
* Financial news integration
* Leaderboard for simulated traders
* Advanced portfolio analytics
* AI-based trading insights

---

# 📌 Learning Outcomes

This project demonstrates:

* Full-stack development using PERN stack
* Real-time data streaming using WebSockets
* Financial data modeling
* Secure authentication systems
* Backend system design
* Performance optimization techniques

---

# 📜 License

This project is licensed under the MIT License.
