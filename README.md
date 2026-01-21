# Jellyfin

Jellyfin is a free and open-source media server platform that allows you to manage and stream your media library across devices. It's a complete alternative to proprietary media servers with no premium features, paywalls, or tracking.

## Features

- **Media Streaming**: Stream movies, TV shows, music, photos, and live TV
- **Multi-Platform**: Available on web, mobile (iOS/Android), desktop, and smart TVs
- **Hardware Acceleration**: Support for GPU transcoding (Intel QuickSync, NVIDIA NVENC, AMD AMF, VA-API)
- **Live TV & DVR**: Watch and record live TV with EPG support
- **User Management**: Multiple user profiles with parental controls
- **Metadata Management**: Automatic metadata fetching from TheMovieDB, TVmaze, and more
- **Plugin System**: Extensible with plugins for additional functionality
- **No Tracking**: Completely open source with no telemetry or data collection

## Installation

### Option 1: Quick Install
```bash
curl -q -LSsf "https://raw.githubusercontent.com/composemgr/jellyfin/main/docker-compose.yaml" | docker compose -f - up -d
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

## Configuration

### Environment Variables

- `TZ`: Timezone (default: America/New_York)
- `JELLYFIN_PublishedServerUrl`: Public URL for the server

### Media Directories

Place your media in the following directories:
- `./rootfs/data/media/movies`: Movie files
- `./rootfs/data/media/tv`: TV show files
- `./rootfs/data/media/music`: Music files

### Hardware Acceleration

To enable GPU transcoding, add device mappings:

**Intel QuickSync:**
```yaml
devices:
  - /dev/dri:/dev/dri
```

**NVIDIA:**
```yaml
runtime: nvidia
environment:
  - NVIDIA_VISIBLE_DEVICES=all
```

### Ports

- `8096`: Web interface and HTTP streaming
- `8920`: HTTPS (optional)
- `1900`: Service discovery (optional)
- `7359`: Local network discovery (optional)

## Initial Setup

1. Access Jellyfin at `http://localhost:8096`
2. Complete the setup wizard:
   - Create administrator account
   - Add media libraries (paths: /media/movies, /media/tv, /media/music)
   - Configure metadata providers
   - Set up user profiles
3. Configure transcoding settings in Dashboard > Playback
4. Install plugins from Dashboard > Plugins > Catalog

## Security Recommendations

- **Change Default Credentials**: Set strong admin password during setup
- **Enable HTTPS**: Use reverse proxy for SSL/TLS encryption
- **Network Access**: Use firewall rules to restrict access
- **User Permissions**: Create separate users with appropriate access levels
- **API Keys**: Protect API keys if using third-party apps
- **Updates**: Keep Jellyfin updated for security patches

## Backup

Important directories to backup:
- `./rootfs/config/jellyfin`: Configuration and database
- `./rootfs/data/jellyfin`: Metadata cache (optional, can be regenerated)

## Troubleshooting

### Transcoding Issues
- Verify hardware acceleration is properly configured
- Check codec support in Dashboard > Playback
- Review transcode logs in Dashboard > Logs

### Media Not Scanning
- Ensure media files have correct permissions
- Check file naming follows Jellyfin conventions
- Trigger manual library scan in Dashboard

### Performance Issues
- Enable hardware acceleration
- Increase cache size
- Use SSD for metadata storage
- Limit concurrent streams

## Documentation

- Official Documentation: https://jellyfin.org/docs/
- GitHub: https://github.com/jellyfin/jellyfin
- Community Forum: https://forum.jellyfin.org/
- Naming Conventions: https://jellyfin.org/docs/general/server/media/movies

## License

Jellyfin is licensed under the GNU GPL v2.
