# Installazione Docker con Docker Compose & WireGuard

- In base alla distro installare i due pacchetti docker con docker compose e wireguard
- Aggiornare il file `/.env` con i propri dati

## Creare un bot telegram e recuperare il tuo id
- Per creare un nuovo bot telegram cerca BotFather da telegram e lancia /newbot e segui le instruzioni.
- Salva il token che viene generato.
- Recupera il tuo id telegram cercando GetID e salvalo.
- Inserire le dati appena recuperati dentro il file `/bot/.env`

## 1. Creazione cartella Docker

- La cartella docker che stai creando deve corrispondere a quella del file `/.env` 

```bash
mkdir /home/utente/docker
cd /home/utente/docker
```

## 2. Avvio dei container

```bash
docker compose up -d
```

## 3. Configurazione WireGuard

- Crea i file di configurazione WireGuard tramite l'interfaccia web per **nginx** e il **server**.
- Sostituisci il file `/nginx_data/config/wg0.conf` con uno di quelli appena creati.
- Crea il file `/etc/wireguard/wg0.conf`
- Riavviare docker `docker compose down` e poi `docker compose up -d`

## 4. Attivazione VPN sul server

```bash
wg-quick up wg0
```

## 5. Avvio automatico della VPN all'avvio del server

```bash
systemctl enable wg-quick@wg0
systemctl start wg-quick@wg0
```
