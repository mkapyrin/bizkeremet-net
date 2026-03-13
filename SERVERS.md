# Серверы проекта bizkeremet.net

**Дата обновления:** 13 марта 2026

---

## Production

| Параметр | Значение |
|----------|----------|
| **URL** | https://bizkeremet.net |
| **IP** | 195.54.174.150 |
| **Hostname** | nl.uulu.ru (mail.uulu.ru) |
| **SSH** | `ssh root@195.54.174.150` |
| **Путь на сервере** | `/var/www/bizkeremet-net/` |
| **Docker Compose** | `docker-compose.yml` |
| **Контейнер** | `bizkeremet-net` |
| **Порт** | 8086 → 80 (nginx внутри контейнера) |
| **Nginx** | `/etc/nginx/sites-available/bizkeremet.net` → `proxy_pass 127.0.0.1:8086` |
| **SSL** | Let's Encrypt (pending DNS change) |
| **Repo** | `mkapyrin/bizkeremet-net` (branch: main) |

---

## Деплой

```bash
ssh root@195.54.174.150 "cd /var/www/bizkeremet-net && git pull origin main && docker compose up --build -d"
```

---

## Почта

| Параметр | Значение |
|----------|----------|
| **MX** | mail.uulu.ru |
| **Почтовый сервер** | chasquid v1.8 |
| **Домен** | bizkeremet.net |
| **Aliases** | `info` → np@prodmag.ru, `*` → np@prodmag.ru |
| **Contact form** | FormSubmit.co → info@bizkeremet.net |

---

## Инвентаризация сервера

Полная инвентаризация сервера nl.uulu.ru: `/root/INV.md` на сервере.

---

**Последнее обновление:** 13 марта 2026
