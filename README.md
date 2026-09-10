English | [Русский](README.ru.md)

# GPT Copywriter Robot (PIX Studio)

![Platform](https://img.shields.io/badge/RPA-PIX_Studio-blue)
![ChatGPT](https://img.shields.io/badge/LLM-ChatGPT-green)
![Stability](https://img.shields.io/badge/API-Stability.ai-orange)

RPA robot that produces a ready-to-publish article automatically: it parses a
foreign news portal, translates the article into Russian with ChatGPT,
generates a cover image via the Stability.ai API, saves the result to Word and
sends it to a Telegram chat.

## Pipeline

```
News portal (rpatoday.net) -> parse articles -> ChatGPT translation
      -> ChatGPT summary -> ChatGPT file name -> image generation
      (Stability.ai / luan.tools) -> save to Word -> send to Telegram bot
```

## Modules

| Module | Purpose |
|---|---|
| main.pix | Orchestrates the whole pipeline |
| InitAllSettings.pix | Reads configuration from config.xlsx (tokens, paths, prompts) |
| GetNews_rpatoday.net.pix | Parses articles from the news portal |
| Chat_GPT_Custom.pix | Calls ChatGPT: translation, summary, title, file name |
| GenerateImage_stability.ai.pix | Generates the cover image via Stability.ai |
| GenerateImage_api.luan.tools.pix | Alternative image generation via luan.tools |
| SaveToWord.pix | Saves the article and image into a Word file |
| SendToTGBot.pix | Sends the result to a Telegram chat |

## Configuration

All settings are stored in config.xlsx (Name / Value / Description):

- IMAP settings for the source mailbox
- Telegram bot token and chat id
- GigaChat URL
- ChatGPT instructions: translation, summary, title, file name
- Working directories: task, completed, img, template

Secrets are never committed: config.xlsx in this repository contains
parameter names and prompt texts only. Put your real tokens into your local
copy of config.xlsx.

## How to run

1. Install PIX Studio
2. Open Task_9_GPT_copyright.pixproj
3. Fill in your tokens and chat id in config.xlsx
4. Run main.pix

## Notes

- Built on the PIX RPA platform
- The same author also has PIX robots for Bitrix24 lead management and for
  bank guarantee processing - see the pinned repositories
