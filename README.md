# Tracearr Unraid Template

Unraid Community Applications template for [Tracearr](https://github.com/connorgallopo/tracearr).

## About Tracearr

Tracearr is a streaming access manager for Plex and Jellyfin servers that detects account sharing through:

- Impossible travel detection
- Simultaneous location monitoring
- Device velocity tracking
- Concurrent stream limits
- Geographic restrictions

## Installation

### Community Applications (Recommended)

1. Open the **Apps** tab in Unraid
2. Search for "Tracearr"
3. Click **Install**
4. Configure the paths and click **Apply**

### Manual Installation

1. Go to **Docker** → **Add Container**
2. Use Template Repository: `https://github.com/connorgallopo/tracearr-unraid-template`

## Image Tags

| Tag | Description |
|-----|-------------|
| `supervised` | Stable all-in-one image with built-in TimescaleDB and Redis |
| `supervised-nightly` | Latest development build (may be unstable) |

## Configuration

### Required Paths

| Path | Container Path | Description |
|------|----------------|-------------|
| PostgreSQL Data | `/data/postgres` | Database storage - **DO NOT change after first run** |
| Redis Data | `/data/redis` | Cache storage |
| App Data | `/data/tracearr` | Secrets, GeoIP database, and app files |

### Optional GeoIP Setup

For geolocation features (stream map, impossible travel detection):

1. Create a free account at [MaxMind](https://www.maxmind.com/en/geolite2/signup)
2. Download `GeoLite2-City.mmdb`
3. Place it in your App Data directory (e.g., `/mnt/user/appdata/tracearr/data/`)

### Environment Variables

All secrets are auto-generated on first run and persisted. You can optionally provide your own:

| Variable | Description |
|----------|-------------|
| `JWT_SECRET` | JWT signing key (32 hex chars) |
| `COOKIE_SECRET` | Cookie signing key (32 hex chars) |
| `ENCRYPTION_KEY` | Server token encryption key (32 hex chars) |
| `LOG_LEVEL` | Logging verbosity: `debug`, `info`, `warn`, `error` |

## Support

- [GitHub Issues](https://github.com/connorgallopo/tracearr/issues)
- [Documentation](https://github.com/connorgallopo/tracearr)

## License

This template is MIT licensed. Tracearr itself is AGPL-3.0 licensed.
