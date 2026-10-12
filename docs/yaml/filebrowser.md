services:
  filebrowser:
    image: filebrowser/filebrowser:latest
    container_name: filebrowser
    ports:
      - "<redacted>"  # Use a different port than other services
    volumes:
      - ./data:/data
      - ./config:/config
      - ./cloud-files:/srv  # Change to a directory you want to browse
    environment:
      - FB_DATABASE=/config/filebrowser.db
      - FB_PORT=80
      - FB_ROOT=/srv
    restart: unless-stopped

networks:
  default:
    name: proxy
    external: true
