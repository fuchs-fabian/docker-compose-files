# `stirling-pdf`

> The German language is used by default.

## Nginx Proxy Manager

Proxy Host:

| Scheme | Forward Hostname / IP | Forward Port |
|--------|-----------------------|--------------|
| http   | stirling-pdf          | 8080         |

## Add language packs

See also: https://github.com/Stirling-Tools/Stirling-PDF/blob/main/HowToUseOCR.md

Start `stirling-pdf` once so that the volumes are created:

```bash
docker compose up -d
```

Shut it down to add the language pack:

```bash
docker compose down
```

Go to the appropriate folder:

```bash
cd ./volumes/stirling-pdf/trainingData/
```

Download the language pack, e.g.:

```bash
wget https://github.com/tesseract-ocr/tessdata/blob/main/deu.traineddata
```

Go back to the folder where the `docker-compose.yml` is and start `stirling-pdf` again.
