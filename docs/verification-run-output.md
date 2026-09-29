# Wynik weryfikacji NoteApp

Data: 2026-09-29T15:03:18+02:00

## Docker
Docker version 29.5.1, build 2518b52
Docker Compose version v5.1.3

## DEV
#1 [internal] load local bake definitions
#1 reading from stdin 488B done
#1 DONE 0.0s

#2 [internal] load build definition from Dockerfile
#2 transferring dockerfile: 204B done
#2 DONE 0.0s

#3 [internal] load metadata for docker.io/library/python:3.9-slim
#3 DONE 0.5s

#4 [internal] load .dockerignore
#4 transferring context: 89B 0.0s done
#4 DONE 0.0s

#5 [internal] load build context
#5 transferring context: 63B done
#5 DONE 0.0s

#6 [1/5] FROM docker.io/library/python:3.9-slim@sha256:2d97f6910b16bd338d3060f261f53f144965f755599aab1acda1e13cf1731b1b
#6 resolve docker.io/library/python:3.9-slim@sha256:2d97f6910b16bd338d3060f261f53f144965f755599aab1acda1e13cf1731b1b
#6 resolve docker.io/library/python:3.9-slim@sha256:2d97f6910b16bd338d3060f261f53f144965f755599aab1acda1e13cf1731b1b 0.1s done
#6 DONE 0.1s

#7 [2/5] WORKDIR /app
#7 CACHED

#8 [3/5] COPY requirements.txt .
#8 CACHED

#9 [4/5] RUN pip install --no-cache-dir -r requirements.txt
#9 CACHED

#10 [5/5] COPY app.py .
#10 CACHED

#11 exporting to image
#11 exporting layers done
#11 exporting manifest sha256:a269b87059f9b85e2fdbc9a3b07a013fe40778ff45eb83a253ec24ea244a7f41 done
#11 exporting config sha256:18ebfe7f384833765aa57169a54a97ad01981472b234efdd21e22a8986102485 done
#11 exporting attestation manifest sha256:6b695ce83eeb17949688eddb1a17f7f03c5a77a94309d4eccfad900fb67ebaf4
#11 exporting attestation manifest sha256:6b695ce83eeb17949688eddb1a17f7f03c5a77a94309d4eccfad900fb67ebaf4 0.1s done
#11 exporting manifest list sha256:3d8b377901de83e65c10e062b3f4a308a7f08a520296b90e60cbe73648a5c465 0.0s done
#11 naming to docker.io/library/note-app-web:latest done
#11 unpacking to docker.io/library/note-app-web:latest 0.0s done
#11 DONE 0.2s

#12 resolving provenance for metadata file
#12 DONE 0.0s
### Kontenery DEV
NAME               IMAGE                COMMAND                  SERVICE   CREATED          STATUS                   PORTS
note-app-adminer   adminer:latest       "entrypoint.sh docke…"   adminer   9 seconds ago    Up 8 seconds             0.0.0.0:8080->8080/tcp, [::]:8080->8080/tcp
note-app-db        postgres:15-alpine   "docker-entrypoint.s…"   db        10 seconds ago   Up 8 seconds (healthy)   5432/tcp
note-app-web       note-app-web         "flask --app app run…"   web       10 seconds ago   Up 2 seconds             0.0.0.0:5000->5000/tcp, [::]:5000->5000/tcp

### Adminer DEV
<title>Login - Adminer</title>

### POST /notes
{
  "note": "Moja pierwsza notatka",
  "status": "success"
}


### GET /notes
[
  [
    1,
    "Moja pierwsza notatka"
  ]
]


## PROD
#1 [internal] load local bake definitions
#1 reading from stdin 488B done
#1 DONE 0.0s

#2 [internal] load build definition from Dockerfile
#2 transferring dockerfile: 204B done
#2 DONE 0.0s

#3 [internal] load metadata for docker.io/library/python:3.9-slim
#3 DONE 0.2s

#4 [internal] load .dockerignore
#4 transferring context: 89B done
#4 DONE 0.0s

#5 [internal] load build context
#5 transferring context: 63B done
#5 DONE 0.0s

#6 [1/5] FROM docker.io/library/python:3.9-slim@sha256:2d97f6910b16bd338d3060f261f53f144965f755599aab1acda1e13cf1731b1b
#6 resolve docker.io/library/python:3.9-slim@sha256:2d97f6910b16bd338d3060f261f53f144965f755599aab1acda1e13cf1731b1b 0.1s done
#6 DONE 0.1s

#7 [2/5] WORKDIR /app
#7 CACHED

#8 [3/5] COPY requirements.txt .
#8 CACHED

#9 [4/5] RUN pip install --no-cache-dir -r requirements.txt
#9 CACHED

#10 [5/5] COPY app.py .
#10 CACHED

#11 exporting to image
#11 exporting layers done
#11 exporting manifest sha256:a269b87059f9b85e2fdbc9a3b07a013fe40778ff45eb83a253ec24ea244a7f41 done
#11 exporting config sha256:18ebfe7f384833765aa57169a54a97ad01981472b234efdd21e22a8986102485 done
#11 exporting attestation manifest sha256:30c984bbcfc92ad04688435b522b19d970cfb16a748b597dd48fa39db2e72219 0.1s done
#11 exporting manifest list sha256:4b7e8b8253b70892678657f8190f68a0d573b4240488c5316534b62699127e54
#11 exporting manifest list sha256:4b7e8b8253b70892678657f8190f68a0d573b4240488c5316534b62699127e54 0.0s done
#11 naming to docker.io/library/note-app-web:latest done
#11 unpacking to docker.io/library/note-app-web:latest 0.0s done
#11 DONE 0.2s

#12 resolving provenance for metadata file
#12 DONE 0.0s
### Kontenery PROD
NAME           IMAGE                COMMAND                  SERVICE   CREATED         STATUS                   PORTS
note-app-db    postgres:15-alpine   "docker-entrypoint.s…"   db        8 seconds ago   Up 8 seconds (healthy)   5432/tcp
note-app-web   note-app-web         "python app.py"          web       8 seconds ago   Up 2 seconds             0.0.0.0:80->5000/tcp, [::]:80->5000/tcp

### GET /notes na porcie 80
[[1,"Moja pierwsza notatka"]]

### Adminer powinien byc niedostepny
OK: port 8080/Adminer is not reachable in prod
