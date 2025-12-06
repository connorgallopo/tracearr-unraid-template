# Tracearr Unraid Templates

Unraid Community Applications templates for [Tracearr](https://github.com/connorgallopo/tracearr).

## About Tracearr

Tracearr is a streaming access manager for Plex and Jellyfin servers that detects account sharing through:

- Impossible travel detection
- Simultaneous location monitoring
- Device velocity tracking
- Concurrent stream limits
- Geographic restrictions

## Available Templates

### Tracearr Supervised (Recommended)

**All-in-one image** with everything bundled:
- TimescaleDB (PostgreSQL 15 with time-series extensions)
- Redis (caching and real-time updates)
- GeoIP database (GeoLite2-City for geolocation)
- Auto-generated secrets (persisted across restarts)

No external database or Redis required!

| Tag | Description |
|-----|-------------|
| `supervised` | Stable all-in-one image |
| `supervised-nightly` | Latest development build (may be unstable) |

### Tracearr (Advanced)

**Lightweight image** requiring external TimescaleDB and Redis. Choose this if:
- You already run a PostgreSQL/TimescaleDB server
- You want to share a database server across containers
- You prefer separating app and data services

GeoIP database (GeoLite2-City) is bundled for geolocation.

| Tag | Description |
|-----|-------------|
| `latest` | Stable release |
| `nightly` | Latest development build (may be unstable) |

## Installation

### Community Applications (Recommended)

1. Open the **Apps** tab in Unraid
2. Search for "Tracearr"
3. Choose either **Tracearr** or **Tracearr Supervised**
4. Configure the paths and click **Apply**

### Manual Installation

1. Go to **Docker** → **Add Container**
2. Use Template Repository: `https://github.com/connorgallopo/tracearr-unraid-template`

## Configuration

### Supervised Template

| Path | Container Path | Description |
|------|----------------|-------------|
| PostgreSQL Data | `/data/postgres` | Database storage - **DO NOT change after first run** |
| Redis Data | `/data/redis` | Cache storage |
| App Data | `/data/tracearr` | Persisted secrets and app files |

Secrets (JWT, Cookie, Encryption) are **auto-generated** on first run and persisted.

### Regular Template

| Variable | Description |
|----------|-------------|
| `DATABASE_URL` | PostgreSQL connection string (e.g., `postgresql://user:pass@192.168.1.100:5432/tracearr`) |
| `REDIS_URL` | Redis connection string (e.g., `redis://192.168.1.100:6379`) |
| `JWT_SECRET` | JWT signing key (32 hex chars) |
| `COOKIE_SECRET` | Cookie signing key (32 hex chars) |
| `ENCRYPTION_KEY` | Server token encryption key (32 hex chars) |

Generate secrets with: `openssl rand -hex 32`

## Support

- [GitHub Issues](https://github.com/connorgallopo/tracearr/issues)
- [Documentation](https://github.com/connorgallopo/tracearr)

## License

This template repository is MIT licensed. Tracearr itself is AGPL-3.0 licensed.
