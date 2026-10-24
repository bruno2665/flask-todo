# Flask Todo-Liste

Kleine Todo-App mit Flask und SQLite.

## Start

```bash
python -m venv .venv
source .venv/bin/activate      # Windows: .venv\Scripts\activate
pip install -r requirements.txt
python app.py
```

Dann im Browser http://127.0.0.1:5000 öffnen.

## Funktionen

- Aufgaben hinzufügen
- Als erledigt markieren / wieder öffnen
- Aufgaben löschen

Die Daten liegen in `todos.db` (wird automatisch angelegt). Mit der
Umgebungsvariable `TODO_DB` lässt sich ein anderer Pfad setzen.

## Deployment (Docker, z. B. Hetzner VPS)

```bash
git clone https://github.com/bruno2665/flask-todo
cd flask-todo
docker compose up -d --build
```

Die App lauscht nur auf `127.0.0.1:8000`. Für den öffentlichen Zugriff einen
Reverse Proxy davorschalten, z. B. Caddy:

```
todo.example.com {
    reverse_proxy 127.0.0.1:8000
}
```

Die Datenbank liegt im Docker-Volume `todo-data` und überlebt Updates
(`git pull && docker compose up -d --build`).
