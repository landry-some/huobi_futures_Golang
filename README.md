# Huobi Futures Golang SDK

A Go (Golang) SDK for interacting with the Huobi Futures API, including REST and WebSocket interfaces.

This project provides a structured client implementation for account management, market data retrieval, and futures trading operations.

---

## Features

- REST API client for Huobi Futures
- WebSocket market data streaming
- Account and position management
- Order creation and management
- BBO (Best Bid Offer) interface support
- Example usage implementations
- Unit tests for core components

---

## Project Structure

- `sdk/` – Core SDK implementation (REST + WebSocket clients)
- `example/` – Example usage of the SDK
- `test/` – Unit tests
- `README.md` – Project documentation

---

## Installation

Clone the repository:

```bash
git clone https://github.com/<your-username>/huobi_futures_Golang.git
cd huobi_futures_Golang
```

Install dependencies:

```bash
go mod tidy
```

---

## Usage

### Import SDK

```go
import "github.com/<your-username>/huobi_futures_Golang/sdk"
```

### Create REST Client

```go
client := sdk.NewClient(apiKey, secretKey)
```

### Example: Place Order

```go
order := sdk.OrderRequest{
    Symbol:       "BTC-USDT",
    ContractType: "quarter",
    Price:        "30000",
    Volume:       1,
    Direction:    "buy",
    Offset:       "open",
    LeverRate:    10,
}

resp, err := client.CreateOrder(order)
if err != nil {
    log.Fatal(err)
}

fmt.Println(resp)
```

### WebSocket Example

```go
ws := sdk.NewWebSocketClient()

ws.SubscribeMarketDepth("BTC-USDT")

ws.OnMessage(func(msg []byte) {
    fmt.Println(string(msg))
})

ws.Connect()
```

---

## Testing

Run unit tests:

```bash
go test ./...
```

---

## Configuration

You will need:

- Huobi Futures API Key
- Huobi Secret Key

Do not hardcode API credentials in source code. Use environment variables instead:

```bash
export HUOBI_API_KEY=your_api_key
export HUOBI_SECRET_KEY=your_secret_key
```

---

## Development

Recommended workflow:

```bash
go fmt ./...
go vet ./...
go test ./...
```

---

## Disclaimer

This SDK is not officially maintained by Huobi.  
Use at your own risk. Always test with small amounts before trading live funds.

---
