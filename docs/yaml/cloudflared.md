services:
  cloudflared:
    image: cloudflare/cloudflared:latest
    container_name: cloudflared
    user: "1000:1000"
    dns:
      - 1.1.1.1
      - 1.0.0.1
    command: tunnel --no-autoupdate --config /etc/cloudflared/config.yml run <tunnel_name>
    restart: unless-stopped
    volumes:
      - /home/<user>/.cloudflared:/etc/cloudflared:ro
    networks:
      - proxy

networks:
  proxy:
    external: true
