# DDoS Live Map — MVP


Minimal local MVP to visualize high-confidence attacker IPs on a globe.


## What this does
- FastAPI backend (`/ingest`) to receive events (json)
- Background enrichment using AbuseIPDB (if API key provided)
- Stores events in SQLite (MVP)
- `/globe-data` returns recent high-score events (JSON)


## Run locally (Docker Compose)
1. Copy repo
2. Create `.env` with ABUSEIPDB_KEY (optional)
3. `docker compose up --build`
4. POST events to `http://localhost:8080/ingest` (example below)
5. Open frontend (you'll build or use sample React component) that polls `/globe-data`


## Example ingest payload
```json
{
"ts": 1694000000,
"src_ip": "203.0.113.5",
"dest": "example.com",
"bytes_in": 1200000,
"reqs": 900,
"extra": {"proto":"TCP"}
}
