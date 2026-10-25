# landing-template

Простой статичный одностраничный сайт (HTML + CSS, без зависимостей и JavaScript) и пример конфига nginx с HTTPS и проксированием WebSocket-запросов на локальный сервис.

- `site/` — страница-визитка вымышленной компании, `404.html`, `robots.txt`. Адаптивная вёрстка, светлая и тёмная тема.
- `nginx/example.conf` — HTTPS, раздача статики, проксирование `WebSocket` с пути `/api/v1/status` на `127.0.0.1:10000`. Остальные запросы на этот путь получают 404.

## Использование

```bash
cp -r site /var/www/site
sed 's/example\.com/ваш-домен/g' nginx/example.conf > /etc/nginx/conf.d/site.conf
certbot certonly --nginx -d ваш-домен
nginx -t && systemctl reload nginx
```

Замените название компании, тексты и контакты в `site/index.html` на свои. Путь и порт бэкенда в `nginx/example.conf` поменяйте под ваш сервис.

## Лицензия

MIT
