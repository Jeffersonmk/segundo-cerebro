---
title: Guia de FFmpeg para Leigos (Arch Linux)
tags: [ffmpeg, linux, vídeo, áudio, terminal, iniciante]
---

# 🧠 Guia de FFmpeg para Leigos (Arch Linux)

## ⚙️ Instalação no Arch Linux

```bash
sudo pacman -Syu
sudo pacman -S ffmpeg
```

Verifique a instalação:

```bash
ffmpeg -version
```

---

## 🧪 Ver informações de um arquivo

Mostra dados técnicos do vídeo/áudio (duração, codecs, resolução, bitrate, etc.):

```bash
ffmpeg -i video.mp4
```

Para informações mais limpas:

```bash
ffprobe -i video.mp4
```

---

## 📦 Converter formatos de vídeo/áudio

Converter um vídeo `.mp4` para `.mkv`:

```bash
ffmpeg -i entrada.mp4 saida.mkv
```

Definindo os codecs manualmente:

```bash
ffmpeg -i entrada.mp4 -vcodec libx264 -acodec aac saida.mp4
```

---

## ✂️ Cortar um trecho do vídeo

Extrair parte do vídeo, do minuto `1:00` até `2:30`:

```bash
ffmpeg -ss 00:01:00 -to 00:02:30 -i entrada.mp4 -c copy corte.mp4
```

> `-c copy` copia o conteúdo sem recodificar — é **mais rápido** e não perde qualidade.

---

## 🎵 Extrair apenas o áudio

Separar só o áudio de um vídeo:

```bash
ffmpeg -i entrada.mp4 -vn audio.mp3
```

- `-vn` desativa o vídeo e deixa apenas o áudio.

---

## 📐 Redimensionar a resolução do vídeo

Alterar a resolução para `1280×720 (HD)`:

```bash
ffmpeg -i entrada.mp4 -vf scale=1280:720 saida.mp4
```

---

## 📉 Comprimir o arquivo para reduzir o tamanho

Diminuir a taxa de bits de vídeo e áudio:

```bash
ffmpeg -i entrada.mp4 -b:v 1000k -b:a 128k saida.mp4
```

- `-b:v` controla a qualidade do vídeo (quanto menor, mais comprimido)
- `-b:a` controla a qualidade do áudio

---

## ⚡ Dicas rápidas de uso no terminal

- Use **Tab** para autocompletar nomes de arquivos/pastas
- Coloque nomes de arquivos com espaços entre **aspas** `"meu video.mp4"`
- Para sobrescrever arquivos existentes sem perguntar, adicione `-y` no final do comando
- Leia sempre as mensagens de erro do FFmpeg — geralmente explicam o problema com clareza

---

## 📚 Onde aprender mais

- [Documentação oficial](https://ffmpeg.org/documentation.html)
- [20+ comandos úteis para iniciantes (Ostechnix)](https://ostechnix.com/20-ffmpeg-commands-beginners)
