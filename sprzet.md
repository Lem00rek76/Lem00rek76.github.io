---
layout: page
title: "Sprzęt"
permalink: /sprzet
---

# Sprzęt

## Główny serwer

- **Model:** Raspberry Pi 5 (rpi5)  
- **Rola:** główny serwer homelabu  
- **System operacyjny:** Ubuntu 25.10 „Questing Quokka”  

## Oprogramowanie bazowe

- **Docker** – zainstalowany ręcznie z oficjalnego repozytorium Dockera (nie z repo starej wersji Ubuntu)
- **Docker Compose** – do zarządzania stackami usług

## Struktura katalogów dla usług Docker

Wszystkie usługi Dockera trzymane są w katalogu `/srv/docker/`:

- `/srv/docker/traefik/` – reverse proxy Traefik
- `/srv/docker/portainer/` – Portainer (GUI do zarządzania Dockerem)
- `/srv/docker/gitea/` – serwer Gitea + Postgres
- `/srv/docker/monitoring/` – narzędzia monitoringu (Grafana, Prometheus, Loki, Uptime Kuma, itp.)
- `/srv/docker/pihole/` – Pi-hole (DNS + blokowanie reklam)
- (w przyszłości kolejne serwisy)

Dzięki temu wszystkie usługi Dockera są w jednym, logicznym miejscu (`/srv/docker/`), łatwym do backupu i przeglądu.
