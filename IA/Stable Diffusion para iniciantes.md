# 🧠 Guia Inicial de AI Art (Civitai)

## 🎨 Tipos de Geração de Imagem

### 📝 **Text2Img (Texto → Imagem)**
- Gera uma imagem **a partir de um prompt de texto**.  
- Exemplo: descrever uma cena e o modelo cria a imagem do zero.

### 🖼️ **Img2Img (Imagem → Imagem)**
- Usa uma **imagem base** como referência e aplica o prompt por cima.  
- Ideal para transformar ou refinar imagens existentes.  
- **Batch Img2Img:** processa **várias imagens de uma só vez**.  
- Frequentemente utiliza **ControlNet**.

### 🩹 **Inpainting**
- Permite **pintar uma área da imagem** para **adicionar, remover ou modificar** objetos.  
- Similar ao *Generative Fill* do Photoshop, mas local.  
- Usa um pincel + prompt.

### 🎥 **Text2Vid / Vid2Vid**
- **Text2Vid:** gera um vídeo com movimento a partir de texto.  
- **Vid2Vid:** transforma um vídeo existente segundo um prompt.

---

## 💬 Prompts

### ✅ **Prompt**
- Texto que descreve **o que você quer ver** na imagem.

### 🚫 **Negative Prompt**
- Texto que descreve **o que você NÃO quer** que apareça.  
- Exemplo: “blurry, low quality, extra fingers”.

---

## 🔍 **Upscaling**
- Aumenta a **resolução da imagem** (ex: 512×512 → 1080×1080).  
- Pode usar:
  - **Modelos internos** do Stable Diffusion.
  - **Softwares externos** como *Topaz Photo/Video AI*.  
- Etapa final antes de publicar.

---

## 🧩 **Modelos e Arquivos**

### 💾 **Model / Checkpoint**
- Arquivo principal que contém o modelo de IA treinado.  
- Define o **estilo e qualidade** das imagens.  
- Extensões:
  - `.ckpt` → formato antigo.  
  - `.safetensors` → formato atual, **mais seguro** (sem código malicioso).

### 🧠 **Training Data**
- Conjunto de imagens usado para treinar o modelo.  
- Exemplo: **LAION-5B**, dataset de **5,85 bilhões** de pares texto-imagem.

### 🔢 **SD 1.5 / SDXL 1.0**
- **SD 1.5:** modelo clássico (512×512). Muito usado pela comunidade.  
- **SDXL 1.0:** versão mais nova e detalhada da Stability AI.

### ⚙️ **LoRA (Low-Rank Adaptation)**
- “Mini-modelos” focados em **um estilo, personagem ou conceito específico**.  
- Exemplo: LoRA de um personagem de anime.

### 🧬 **Textual Inversion / Embeddings**
- Pequenos modelos focados em **corrigir detalhes** (mãos, olhos, rostos)  
  ou capturar **conceitos específicos**.

### 🎨 **VAE (Variational Autoencoder)**
- Arquivo opcional que **melhora cores e detalhes**.  
- Pode estar embutido no modelo ou separado.  
- Sem o VAE, as imagens podem parecer “lavadas” ou sem contraste.

---

## 🔌 **Extensões Importantes**

### 🕹️ **ControlNet**
- Analisa estruturas como **linhas, profundidade, poses** e permite
  reconstruir imagens mantendo a composição.  
- Essencial para **Img2Img** e **Vid2Vid**.

### 🌀 **DeForum**
- Extensão para gerar **vídeos animados suaves** dentro do Automatic1111.  
- Permite **keyframes** para zoom, pan e rotação.

### 🔍 **ESRGAN (Enhanced Super Resolution GAN)**
- Técnica de **upscaling por IA** (melhora resolução sem perda de qualidade).  
- Muito usada em interfaces de Stable Diffusion.

### 🎞️ **AnimateDiff**
- Adiciona **movimento** em *text-to-image* e *image-to-image*.  
- Base para animações curtas e vídeos generativos.

---

## 🧱 **Resumo Conceitual**

| Conceito | Função Principal | Exemplo |
|-----------|------------------|----------|
| Text2Img | Gera imagem do zero | “Faceless man in a suit” |
| Img2Img | Edita imagem existente | Refinar uma thumbnail |
| Inpainting | Adiciona/remove partes | Corrigir mãos |
| Upscaling | Aumenta resolução | 512→1080 |
| LoRA | Adiciona estilo específico | Estilo noir |
| Embedding | Corrige detalhe técnico | Corrigir olhos |
| VAE | Ajusta cor e contraste | Melhorar saturação |
| ControlNet | Mantém pose e estrutura | Recriar personagem |
| DeForum | Gera vídeo animado | Animações suaves |
| ESRGAN | Aumenta resolução via IA | Melhor nitidez |
| AnimateDiff | Adiciona movimento | Cena animada |
