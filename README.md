## 👋 Welcome to jellyfin 🚀

Free media system with no strings attached

## 📋 Description

Free media system with no strings attached

## 🚀 Services

- **jellyfin**: jellyfin/jellyfin:latest

## 📦 Installation

### Option 1: Quick Install
```bash
curl -q -LSsf "https://raw.githubusercontent.com/composemgr/jellyfin/main/docker-compose.yaml" -o compose.yml
```

### Option 2: Git Clone
```bash
git clone "https://github.com/composemgr/jellyfin" ~/.local/srv/docker/jellyfin
cd ~/.local/srv/docker/jellyfin
docker compose up -d
```

### Option 3: Using composemgr
```bash
composemgr install jellyfin
```

## 🔧 Configuration

### Environment Variables

```shell
TZ=America/New_York
```

See `docker-compose.yaml` for complete list of configurable options.

## 🌐 Access

- **Web Interface**: http://172.17.0.1:8096

## 📂 Volumes

- `./rootfs/config/jellyfin` - Data storage
- `./rootfs/data/jellyfin` - Data storage
- `./rootfs/data/media/movies` - Data storage
- `./rootfs/data/media/tv` - Data storage
- `./rootfs/data/media/music` - Data storage

## 🔍 Logging

```shell
docker compose logs -f jellyfin
```

## 🛠️ Management

```bash
# Start services
docker compose up -d

# Stop services
docker compose down

# Update to latest images
docker compose pull && docker compose up -d

# View logs
docker compose logs -f

# Restart services
docker compose restart
```

## 📋 Requirements

- Docker Engine 20.10+
- Docker Compose V2+

## 🤝 Author

🤖 casjay: [Github](https://github.com/casjay) 🤖  
🦄 composemgr: [Github](https://github.com/composemgr) 🦄
