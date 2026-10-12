services:
  pihole:
   image: pihole/pihole:latest
   container_name: pihole
   ports:
    - "53:53/tcp"
    - "53:53/udp"
    - "<redacted>"
   environment:
     TZ: "America/NewYork"
     PIHOLE_DNS_: "1.1.1.1; 8.8.8.8"
   volumes:
    - ./etc-pihole:/etc/pihole
    - ./etc-dnsmasq.d:/etc/dnsmasq.d
   restart: unless-stopped
   dns:
    - 1.1.1.1
    - 8.8.8.8

networks:
  default:
    name: proxy
    external: true
