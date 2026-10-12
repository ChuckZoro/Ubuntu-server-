services:
  uptime-kuma:
    image: louislam/uptime-kuma:2
    container_name: uptime-kuma
    volumes:
      - ./uptime-kuma-data:/app/data
    ports:
      - "3001:3001"
    extra_hosts:
      - "<ip_address>"
    restart: unless-stopped

networks:
  default:
    name: proxy
    external: true
 
