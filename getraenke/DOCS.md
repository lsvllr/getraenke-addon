# Getränke-Tracker

Strichliste für den Getränke-Kühlschrank. Erreichbar über den Cloudflare-Tunnel
(z. B. `https://getraenke.vollrath.app`), intern unter `http://<hostname>:8000`.

## Optionen

| Option | Bedeutung |
|---|---|
| `admin_password` | Passwort für den Admin-Bereich, solange dort keines gesetzt wurde. Leer = Standard `admin` (unsicher!). |
| `secret_key` | Schlüssel für Login-Cookies. Leer = wird einmal erzeugt und in `.secret_key` gespeichert. |

## Daten

Datenbank (`getraenke.db`) und `.secret_key` liegen in
`/addon_configs/<hash>_getraenke` (per Samba-Freigabe `addon_configs`
erreichbar) und sind Teil der Home-Assistant-Backups. Das Add-on wird für
Backups kurz gestoppt (`backup: cold`), damit die SQLite-Datei konsistent ist.

Kein Port wird nach außen veröffentlicht; die echte Client-IP kommt aus dem
Header `cf-connecting-ip` (Cloudflare), Login-Cookies nur über HTTPS.
