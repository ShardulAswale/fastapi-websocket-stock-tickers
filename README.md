# FastAPI WebSocket Stock Tickers

Python learning project broadcasting simulated stock prices over WebSockets.

## How it works

A background task updates an in-memory ticker store using random price changes. Authenticated HTTP routes expose snapshots and resets, while a WebSocket handler streams updates to connected clients. Pydantic models describe the payloads.

## Usage

Requires Python 3.13 or later. From the repository root, inside your Python environment:

```sh
python -m pip install -e ".[dev]"
python -m uvicorn stock_ticker_api.main:app --reload
```

Open `http://127.0.0.1:8000/docs`. Demo credentials are `admin` / `changeme`.

## Endpoints

| Method | Path |
| --- | --- |
| GET | `/health`, `/me`, `/tickers`, `/tickers/{symbol}` |
| POST | `/tickers/{symbol}/reset` |
| WebSocket | `/ws/ticker` |

HTTP routes use Basic authentication. The WebSocket accepts a Basic authorization header or demo username/password query parameters.

## Notes

Prices are simulated, not live market data. Storage resets on restart. Model generation is optional because the generated model is included; use `python -m scripts.generate_models` when changing its JSON schema.
