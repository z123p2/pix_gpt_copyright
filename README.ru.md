[English](README.md) | Русский

# Робот GPT-копирайтер (PIX Studio)

![Platform](https://img.shields.io/badge/RPA-PIX_Studio-blue)
![ChatGPT](https://img.shields.io/badge/LLM-ChatGPT-green)
![Stability](https://img.shields.io/badge/API-Stability.ai-orange)

RPA-робот, который готовит статью к публикации автоматически: парсит
зарубежный новостной портал, переводит статью на русский язык через ChatGPT,
генерирует обложку через Stability.ai API, сохраняет результат в Word и
отправляет в Telegram-чат.

## Пайплайн

```
Новостной портал (rpatoday.net) -> парсинг статей -> перевод ChatGPT
      -> выжимка ChatGPT -> имя файла ChatGPT -> генерация картинки
      (Stability.ai / luan.tools) -> сохранение в Word -> отправка в Telegram-бот
```

## Модули

| Модуль | Назначение |
|---|---|
| main.pix | Управляет всем пайплайном |
| InitAllSettings.pix | Читает конфигурацию из config.xlsx (токены, пути, промпты) |
| GetNews_rpatoday.net.pix | Парсит статьи с новостного портала |
| Chat_GPT_Custom.pix | Обращается к ChatGPT: перевод, выжимка, заголовок, имя файла |
| GenerateImage_stability.ai.pix | Генерирует обложку через Stability.ai |
| GenerateImage_api.luan.tools.pix | Альтернативная генерация изображения через luan.tools |
| SaveToWord.pix | Сохраняет статью и картинку в Word |
| SendToTGBot.pix | Отправляет результат в Telegram-чат |

## Конфигурация

Все настройки хранятся в config.xlsx (Имя / Значение / Описание):

- Настройки IMAP для исходного почтового ящика
- Токен Telegram-бота и chat id
- URL GigaChat
- Инструкции для ChatGPT: перевод, выжимка, заголовок, имя файла
- Рабочие директории: task, completed, img, template

Секреты никогда не коммитятся: config.xlsx в этом репозитории содержит только
имена параметров и тексты промптов. Свои токены вносите в локальную копию
config.xlsx.

## Запуск

1. Установите PIX Studio
2. Откройте Task_9_GPT_copyright.pixproj
3. Заполните токены и chat id в config.xlsx
4. Запустите main.pix

## Примечания

- Разработан на RPA-платформе PIX
- У того же автора есть PIX-роботы для управления лидами Битрикс24 и для
  обработки банковских гарантий - см. закреплённые репозитории
