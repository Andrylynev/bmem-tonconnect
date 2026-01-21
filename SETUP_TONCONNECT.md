# Настройка TON Connect для BMEM Lottery Bot

TON Connect позволяет пользователям подключать кошельки одним кликом и подписывать транзакции напрямую в приложении кошелька.

## Шаг 1: Создайте GitHub репозиторий

1. Зайдите на [github.com](https://github.com)
2. Создайте новый публичный репозиторий (например `bmem-tonconnect`)
3. Скопируйте файл `tonconnect-manifest.json` из папки `docs/` в корень репозитория

## Шаг 2: Отредактируйте manifest

Откройте `tonconnect-manifest.json` и измените:

```json
{
  "url": "https://t.me/YOUR_BOT_USERNAME",
  "name": "BMEM Lottery",
  "iconUrl": "https://YOUR_USERNAME.github.io/YOUR_REPO/icon.png",
  "termsOfUseUrl": "https://t.me/YOUR_BOT_USERNAME",
  "privacyPolicyUrl": "https://t.me/YOUR_BOT_USERNAME"
}
```

**Важно:**
- `url` - ссылка на вашего Telegram бота
- `iconUrl` - HTTPS URL иконки бота (128x128 PNG)
- Все URL должны быть HTTPS

## Шаг 3: Добавьте иконку бота

1. Создайте иконку `icon.png` (128x128 пикселей)
2. Загрузите в репозиторий

## Шаг 4: Включите GitHub Pages

1. В репозитории: Settings → Pages
2. Source: Deploy from a branch
3. Branch: `main` / `(root)`
4. Save

Подождите 2-3 минуты. URL будет:
```
https://YOUR_USERNAME.github.io/YOUR_REPO/tonconnect-manifest.json
```

## Шаг 5: Проверьте manifest

Откройте URL в браузере - должен показаться JSON файл.

## Шаг 6: Добавьте URL в .env

```bash
TONCONNECT_MANIFEST_URL=https://YOUR_USERNAME.github.io/YOUR_REPO/tonconnect-manifest.json
```

## Шаг 7: Перезапустите бота

```bash
python run.py
```

---

## Как это работает

1. **Пользователь нажимает "Подключить кошелёк"**
2. **Бот показывает QR код / кнопку**
3. **Кошелёк читает manifest с GitHub Pages**
4. **Пользователь подтверждает подключение**
5. **При покупке - транзакция отправляется в кошелёк для подписи**

## Поддерживаемые кошельки

- ✅ Tonkeeper
- ✅ Telegram Wallet  
- ✅ Tonhub
- ✅ MyTonWallet
- ✅ OpenMask

## Troubleshooting

### Manifest не загружается
- Проверьте что репозиторий публичный
- Проверьте что GitHub Pages включен
- Подождите 5 минут после включения Pages

### Кошелёк не подключается
- Проверьте что все URL в manifest используют HTTPS
- Убедитесь что иконка доступна по указанному URL

### Ошибка "Invalid manifest"
- Проверьте JSON синтаксис на [jsonlint.com](https://jsonlint.com)
- Все обязательные поля должны присутствовать

---

## Альтернатива: Ручной ввод адреса

Если TON Connect не настроен, пользователи могут ввести адрес кошелька вручную. Бот покажет кнопки с deep links для оплаты.
