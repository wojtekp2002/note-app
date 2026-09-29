# Weryfikacja

Zakres weryfikacji:

1. Budowa obrazu aplikacji z `Dockerfile`.
2. Uruchomienie trybu DEV przez `docker compose up -d`.
3. Sprawdzenie API POST/GET na porcie 5000.
4. Sprawdzenie Adminera na porcie 8080.
5. Zatrzymanie trybu DEV.
6. Uruchomienie trybu PROD przez `docker compose -f docker-compose.yml -f docker-compose.prod.yml up -d`.
7. Sprawdzenie API na porcie 80.
8. Potwierdzenie, ze Adminer nie dziala w PROD.

Pelny output z maszyny `main-learnit` znajduje sie w `docs/verification-run-output.md`.
