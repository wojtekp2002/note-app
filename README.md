# NoteApp - Flask + PostgreSQL + Adminer

Projekt realizuje zadanie domowe z lekcji 22. System sklada sie z API Flask, bazy PostgreSQL oraz Adminera dostepnego tylko w srodowisku developerskim.

## Struktura

```text
note-app/
├── app.py
├── requirements.txt
├── Dockerfile
├── .env
├── docker-compose.yml
├── docker-compose.override.yml
├── docker-compose.prod.yml
└── docs/
```

## Srodowisko DEV

Uruchomienie:

```bash
docker compose up -d
```

W trybie dev startuja:

- `web` - API Flask na `http://localhost:5000`,
- `db` - PostgreSQL,
- `adminer` - GUI do bazy na `http://localhost:8080`.

Dane do Adminera:

- System: `PostgreSQL`
- Server: `db`
- Username: `user`
- Password: `password`
- Database: `notes_db`

Dodanie notatki:

```bash
curl -X POST http://localhost:5000/notes \
  -H "Content-Type: application/json" \
  -d '{"content": "Moja pierwsza notatka"}'
```

Odczyt notatek:

```bash
curl http://localhost:5000/notes
```

## Srodowisko PROD

Najpierw zatrzymaj dev:

```bash
docker compose down
```

Uruchom produkcje:

```bash
docker compose -f docker-compose.yml -f docker-compose.prod.yml up -d
```

W trybie prod startuja tylko `web` i `db`. Adminer nie jest dolaczony, bo znajduje sie w `docker-compose.override.yml`, ktorego nie uzywamy przy uruchomieniu produkcyjnym.

Aplikacja jest dostepna na porcie 80:

```bash
curl http://localhost/notes
```

Port 8080 nie powinien odpowiadac:

```bash
curl --max-time 3 http://localhost:8080
```

## Sprzatanie

```bash
docker compose down
docker compose -f docker-compose.yml -f docker-compose.prod.yml down
```

Aby usunac takze wolumen bazy:

```bash
docker compose down -v
```
