---
layout: page
title: "Backupy"
permalink: /backupy
---

# Backupy

## Co jest / będzie backupowane

- Konfiguracje:
  - router MikroTik (export configu),
  - konfiguracja Pi-hole,
  - konfiguracja Traefika,
  - stacki Dockera (`docker-compose.yml` itp.),
  - konfiguracja Gitea.
- Dane aplikacji:
  - volume `./gitea` (dane repo i ustawienia),
  - katalogi usług w `/srv/docker/` (np. `./data` Portainera, monitoring).
- Dane użytkowników (w przyszłości):
  - dokumenty, zdjęcia, multimedia, itp.

## Gdzie trafiają backupy

*(do uzupełnienia, gdy ustalisz docelowy schemat)*

Przykładowy plan:

- **Lokalnie:**
  - drugi dysk / NAS w sieci LAN,
  - snapshoty katalogów `/srv/docker/`.
- **Zdalnie:**
  - backup do chmury (np. rclone → B2, S3, OneDrive, itp.),
  - replikacja do innej lokalizacji / innego serwera.

## Harmonogram (propozycja)

- **Codziennie:**
  - backup konfiguracji kontenerów (pliki YAML, skrypty),
  - dump bazy Gitea (Postgres).
- **Co tydzień:**
  - pełny backup danych aplikacji (volumes) na NAS / zewnętrzny dysk.
- **Co miesiąc:**
  - „gruby” backup offsite (do chmury / innej lokalizacji).

## Testy odtwarzania

- Okresowo testować:
  - przywrócenie bazy Gitea z dumpa,
  - odtworzenie jednego kontenera (np. Gitea / Portainer) na czystej instancji,
  - przywrócenie konfiguracji MikroTika na zapasowym urządzeniu / w VM.
