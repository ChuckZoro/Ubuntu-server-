services:
  vaultwarden:
    image: vaultwarden/server:latest
    container_name: vaultwarden
    restart: unless-stopped
    env_file:
    - vaultwarden.env
    volumes:
    - ./vw-data:/data

networks:
  default:
    name: proxy
    external: true
