# 🎤 Analisador de Voz - Sistema de Análise Vocal com IA

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/piruvari/Analisador_de_voz/blob/main/Analizador_de_voz_v5.ipynb)
[![Python 3.8+](https://img.shields.io/badge/python-3.8+-blue.svg)](https://www.python.org/downloads/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

Sistema de análise vocal baseado em inteligência artificial que extrai 11 características técnicas de performances vocais e gera relatórios práticos para replicação de técnicas de canto.

> **💡 100% baseado em Google Colab - Não precisa instalar nada no seu computador!**

---

## 📋 Índice

- [Sobre o Projeto](#sobre-o-projeto)
- [Características Analisadas](#características-analisadas)
- [Como Usar no Google Colab](#como-usar-no-google-colab)
- [Exemplo de Resultado](#exemplo-de-resultado)
- [Configurações](#configurações)
- [Documentação Completa](#documentação-completa)
- [Limitações](#limitações)
- [FAQ](#faq)
- [Contribuindo](#contribuindo)
- [Licença](#licença)

---

## 🎯 Sobre o Projeto

Este sistema permite analisar gravações vocais e extrair dados técnicos precisos sobre como um cantor está produzindo sua voz.

### Para Quem é Este Sistema?

- 🎓 **Cantores** que querem estudar técnicas de artistas específicos
- 👨‍🏫 **Professores de canto** que precisam de análise objetiva de alunos
- 🎧 **Produtores musicais** que desejam direcionar sessões de gravação
- 🔬 **Pesquisadores** de música e acústica vocal

### O Que o Sistema Faz

```
INPUT: arquivo.wav → PROCESSAMENTO (IA) → OUTPUT: relatório.txt
```

1. **Separa vocais** de instrumentos (Demucs)
2. **Transcreve** letra com timestamps (Whisper)
3. **Analisa 11 características vocais** (Librosa, Praat)
4. **Gera relatório duplo**:
   - 📝 Guia prático (linguagem natural)
   - 📊 Dados técnicos (segmento por segmento)

---

## 🎵 Características Analisadas

| # | Feature | O Que Mede | Para Que Serve |
|---|---------|------------|----------------|
| 1 | **Pitch (F0)** | Altura da voz (Hz) | Saber qual nota cantar |
| 2 | **Vibrato** | Oscilação controlada | Medir a "tremidinha" |
| 3 | **Formantes** | Ressonâncias do trato vocal | Posição língua/mandíbula |
| 4 | **Breathiness** | Quantidade de ar | Voz sussurrada vs. limpa |
| 5 | **Brilho Espectral** | Claridade tonal | Som claro vs. escuro |
| 6 | **Tensão Vocal** | Compressão | Garganta aberta vs. fechada |
| 7 | **Ataque (ADSR)** | Como começa nota | Ataque duro vs. suave |
| 8 | **Dinâmica** | Variação volume | Forte/fraco |
| 9 | **Portamentos** | Deslizes entre notas | Legato vs. staccato |
| 10 | **HNR** | Pureza tonal | Voz limpa vs. rouca |
| 11 | **Ressonância** | Registro vocal | Peito/misto/cabeça |

---

## 🚀 Como Usar no Google Colab

### ⚡ Início Rápido (5 minutos)

#### **Passo 1: Abra o Notebook**

Clique no botão abaixo para abrir no Google Colab:

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/piruvari/Analisador_de_voz/blob/main/Analizador_de_voz_v5.ipynb)

#### **Passo 2: Prepare Seu Áudio**

**Requisitos do arquivo:**
- ✅ Formato: **WAV** (obrigatório)
- ✅ Conteúdo: Música cantada (com ou sem instrumentos)
- ✅ Duração: Qualquer (testado até 40 minutos)
- ✅ Qualidade recomendada: 44.1 kHz, 16-bit

**Onde colocar o arquivo:**
1. Faça upload para seu **Google Drive**
2. Crie uma pasta (ex: `AudioAnalysis/`)
3. Coloque o arquivo WAV lá

**Não tem WAV?** Converta seu MP3/FLAC:
- Online: [CloudConvert](https://cloudconvert.com/mp3-to-wav)
- Desktop: [Audacity](https://www.audacityteam.org/) (gratuito)

#### **Passo 3: Configure o Notebook**

Na **Célula 1**, ajuste apenas 3 variáveis:

```python
# Célula 1: Configurações básicas
TRACK = "Sia_Chandelier"  # ← Altere para nome da sua música

# Célula 2: Caminhos dos arquivos
AUDIO_PATH = '/content/drive/MyDrive/AudioAnalysis/voz/Sia_Chandelier_vocals.wav'  # ← Seu caminho
DRIVE_OUTPUT_PATH = '/content/drive/MyDrive/AudioAnalysis/voz/'  # ← Pasta de saída
```

**Como encontrar o caminho correto:**
1. No Colab, clique no ícone 📁 (barra lateral esquerda)
2. Monte o Drive (clique em "Mount Drive")
3. Navegue até seu arquivo
4. Clique com botão direito → "Copy path"
5. Cole no código

#### **Passo 4: Execute**

**Opção A - Executar Tudo (Recomendado):**
```
Menu: Runtime → Run all
Ou: Ctrl+F9 (Windows) / Cmd+F9 (Mac)
```

**Opção B - Célula por Célula:**
```
Clique em cada célula e pressione: Shift+Enter
```

#### **Passo 5: Aguarde**

⏱️ **Tempo de Processamento:**
- Música 3-4 min: 10-30 minutos
- Música 10 min: 30-60 minutos
- Música 40 min: 1-2 horas

*Tempo varia conforme disponibilidade de GPU no Colab*

**O que você verá:**
```
[1/5] Carregando modelo Whisper (medium)...
[2/5] Detectando idioma... ✓ Idioma: EN
[3/5] Transcrevendo áudio... ✓ 25 segmentos detectados
[4/5] Aplicando segmentação... ✓ 71 segmentos refinados
[5/5] Analisando características vocais...
  Analisando segmento 5/71...
  Analisando segmento 10/71...
  ...
✓ Análise completa!
```

#### **Passo 6: Acesse o Resultado**

O arquivo será salvo automaticamente no seu Google Drive:
```
📁 Google Drive
  └─ AudioAnalysis/voz/
      └─ Sia_Chandelier_vocals_analise_pratica.txt  ← Aqui!
```

Abra o arquivo `.txt` para ver o relatório completo!

---

## 📊 Exemplo de Resultado

### Parte 1: Guia Prático

```
====================================================================================================
GUIA PRÁTICO DE REPLICAÇÃO VOCAL
====================================================================================================

1. ALTURA DA VOZ (PITCH/TOM)
────────────────────────────────────────

📊 DADOS TÉCNICOS:
   • F0 Médio: 464.3 Hz
   • Range: 350.0 Hz a 580.0 Hz

🎯 O QUE FAZER:
   ✓ Esta é uma VOZ MUITO AGUDA
   ✓ Cante acima de F4 (Fá4)
   ✓ Use FALSETE ou voz de cabeça

💡 COMO PRATICAR:
   1. Use afinador de celular (Tuner, Pano Tuner)
   2. Cante sustentado tentando manter 464 Hz
   3. Ajuste até acertar a frequência
```

### Parte 2: Análise Técnica por Segmento

```
[0.50s - 3.50s] "I'm gonna swing from the chandelier"
─────────────────────────────────────────────────────────────────
1️⃣ PITCH: 464.3 Hz (MUITO AGUDO) | Range: 350-580 Hz
2️⃣ VIBRATO: 3.7 Hz (LENTO), 817.8 cents (intenso)
3️⃣ FORMANTES: F1=850Hz (boca ABERTA) | F2=1800Hz (língua CENTRO)
4️⃣ BREATHINESS: ALTO → cante sussurrado, muito ar
5️⃣ BRILHO: BRILHANTE (2800 Hz) → som para FRENTE
6️⃣ TENSÃO: MÉDIA → tensão equilibrada
7️⃣ ATAQUE: 0.089s (MODERADO) → comece firme
8️⃣ DINÂMICA: -15.2 dB (FORTE) | Range: 35.8 dB
9️⃣ PORTAMENTOS: 12 detectados → deslize ocasionalmente
🔟 QUALIDADE: HNR 16.3 dB (voz LIMPA)
➕ RESSONÂNCIA: MISTA (580 Hz)
```

---

## ⚙️ Configurações

### Parâmetros Ajustáveis

#### 1. Modelo Whisper (Precisão da Transcrição)

```python
MODEL_SIZE = 'medium'  # Altere na Célula de Configurações
```

| Modelo | Tempo | Precisão | Memória | Quando Usar |
|--------|-------|----------|---------|-------------|
| `tiny` | 1-2 min | ~70% | 1 GB | Teste rápido |
| `base` | 2-3 min | ~80% | 1.5 GB | Preview |
| `small` | 3-5 min | ~85% | 2 GB | Boa opção |
| **`medium`** | 5-10 min | **~95%** | 5 GB | **✅ RECOMENDADO** |
| `large` | 15-25 min | ~98% | 10 GB | Máxima precisão |

#### 2. Segmentação Temporal

```python
SEGMENTACAO_TEMPO = 3.0  # segundos por segmento
```

| Valor | Granularidade | Segmentos (3 min) | Quando Usar |
|-------|---------------|-------------------|-------------|
| 1.0 | Palavra por palavra | ~180 | Análise ultra-detalhada |
| **3.0** | Frase curta | **~60** | **✅ RECOMENDADO** |
| 5.0 | Frase longa | ~36 | Visão geral |
| 10.0 | Seção musical | ~18 | Verso/refrão/ponte |

**Dica:** Valores menores = mais detalhado, mas arquivo maior

---

## 📚 Documentação Completa

### Manual Técnico em PDF

📖 [Download do Manual Técnico Completo](docs/Manual_Tecnico.pdf)

**O manual inclui:**
- ✅ Explicação científica de cada feature
- ✅ Algoritmos e fórmulas matemáticas
- ✅ Como interpretar cada número
- ✅ Exemplos práticos de uso
- ✅ Referências bibliográficas

### Vídeo Tutorial (Em breve)
🎬 Tutorial em vídeo mostrando passo a passo

---

## ⚠️ Limitações

### O Que Funciona Bem

✅ Vocais isolados (a cappella, separated tracks)  
✅ Pop, Rock, Soul, R&B, Gospel, Jazz  
✅ Arquivos WAV de boa qualidade  
✅ Músicas cantadas (não rap falado)  

### Limitações Conhecidas

❌ **Formato de áudio:** Apenas WAV (converta antes)  
❌ **Técnicas extremas:** Growl, scream, death metal  
❌ **Harmonias:** Múltiplas vozes simultâneas confundem  
❌ **Separação imperfeita:** Demucs pode deixar "vazamento" de instrumentos  

### ⚠️ Aviso de Saúde Vocal

Este sistema é uma **ferramenta de análise**, não substitui:
- Aulas de canto profissionais
- Avaliação médica (otorrinolaringologista)
- Tratamento fonoaudiológico

**Procure médico se:**
- HNR < 8 dB por mais de 2 semanas
- Dor ao cantar
- Rouquidão persistente
- Perda de alcance vocal

---

## ❓ FAQ (Perguntas Frequentes)

<details>
<summary><b>Preciso instalar algo no meu computador?</b></summary>

**NÃO!** Tudo roda no Google Colab (navegador). Só precisa:
- Conta Google (gratuita)
- Google Drive com espaço livre (~500 MB)
- Navegador web
</details>

<details>
<summary><b>O Google Colab é grátis?</b></summary>

**SIM!** A versão gratuita é suficiente para este projeto. 

Limitações da versão gratuita:
- Sessão máxima: 12 horas
- Pode não ter GPU disponível sempre
- Recursos compartilhados

Se processar músicas longas frequentemente, considere **Colab Pro** ($10/mês).
</details>

<details>
<summary><b>Posso usar MP3 ou só WAV?</b></summary>

**Apenas WAV.** Mas é fácil converter:

**Online (grátis):**
- [CloudConvert](https://cloudconvert.com/mp3-to-wav)
- [Online-Convert](https://audio.online-convert.com/convert-to-wav)

**Desktop (grátis):**
- [Audacity](https://www.audacityteam.org/)
- [FFmpeg](https://ffmpeg.org/)
</details>

<details>
<summary><b>Quanto tempo demora?</b></summary>

Depende dos recursos disponíveis no Colab:

| Duração da Música | Com GPU | Sem GPU |
|-------------------|---------|---------|
| 3-4 minutos | 5-10 min | 15-30 min |
| 10 minutos | 15-20 min | 40-60 min |
| 40 minutos | 40-60 min | 2-3 horas |
</details>

<details>
<summary><b>Funciona com música que tem instrumentos?</b></summary>

**SIM!** O sistema usa Demucs para separar vocais automaticamente.

**Melhor resultado:** Vocais já isolados profissionalmente  
**Bom resultado:** Música completa (pop, rock, etc)  
**Resultado parcial:** Músicas com vocais muito baixos no mix
</details>

<details>
<summary><b>Funciona em qualquer idioma?</b></summary>

**SIM!** Whisper detecta automaticamente 90+ idiomas:
- Português ✅
- Inglês ✅
- Espanhol ✅
- Francês ✅
- Italiano ✅
- Alemão ✅
- E muitos mais...
</details>

<details>
<summary><b>Posso analisar minha própria voz?</b></summary>

**SIM!** É uma ótima aplicação:

1. Grave sua voz (WAV, 44.1 kHz)
2. Analise com o sistema
3. Compare com seu artista favorito
4. Veja exatamente o que precisa ajustar
5. Pratique e analise novamente

Perfeito para acompanhar progresso!
</details>

<details>
<summary><b>O sistema dá erro. O que fazer?</b></summary>

**Checklist de troubleshooting:**

1. ✅ Arquivo é WAV? (não MP3, FLAC, etc)
2. ✅ Caminho está correto? (copie do Drive)
3. ✅ Drive está montado? (Execute célula de mount)
4. ✅ Tem espaço no Drive? (mínimo 500 MB)
5. ✅ Executou células na ordem? (ou usou Run All)

Se ainda não funcionar: [Abra um Issue](https://github.com/piruvari/Analisador_de_voz/issues)
</details>

<details>
<summary><b>Posso usar para trabalhos comerciais?</b></summary>

**SIM!** Licença MIT permite uso comercial.

**Você pode:**
- ✅ Usar em estúdio de gravação
- ✅ Ensinar técnica vocal
- ✅ Pesquisa acadêmica
- ✅ Produção musical

**Apenas mantenha:** Créditos no código-fonte
</details>

---

## 🤝 Contribuindo

Contribuições são muito bem-vindas! 

### Como Contribuir

1. **Fork** o repositório
2. **Clone** seu fork
3. **Crie** uma branch (`git checkout -b feature/MinhaFeature`)
4. **Commit** mudanças (`git commit -m 'Adiciona MinhaFeature'`)
5. **Push** para branch (`git push origin feature/MinhaFeature`)
6. **Abra** um Pull Request

### Áreas Que Precisam de Ajuda

- [ ] Suporte para MP3, FLAC, M4A
- [ ] Interface web (sem Colab)
- [ ] Análise em tempo real
- [ ] Comparação antes/depois automática
- [ ] Tradução docs (EN, ES, FR, DE)
- [ ] Mais exemplos de análises
- [ ] Testes automatizados

### Reportar Bugs

Encontrou um bug? [Abra um Issue](https://github.com/piruvari/Analisador_de_voz/issues)

**Inclua:**
- Descrição do problema
- Passos para reproduzir
- Mensagem de erro (se houver)
- Sistema operacional
- Modelo Whisper usado

---

---

## 🔬 Referências Técnicas

### Algoritmos Utilizados

| Feature | Algoritmo | Referência |
|---------|-----------|------------|
| Pitch (F0) | YIN | De Cheveigné & Kawahara (2002) |
| Formantes | Burg's LPC | Burg (1975) |
| HNR | Autocorrelação | Boersma (1993) |
| Separação | Demucs | Défossez et al. (2019) |
| Transcrição | Whisper | Radford et al. (2022) |

### Bibliotecas

- **[Librosa](https://librosa.org/)** - Análise de áudio e música
- **[Praat/Parselmouth](https://parselmouth.readthedocs.io/)** - Análise fonética
- **[Demucs](https://github.com/facebookresearch/demucs)** - Separação de fonte
- **[Whisper](https://github.com/openai/whisper)** - Reconhecimento de fala

---

## 📞 Contato e Suporte

### Issues e Discussões

- 🐛 **Bug Reports:** [GitHub Issues](https://github.com/piruvari/Analisador_de_voz/issues)
- 💡 **Feature Requests:** [GitHub Issues](https://github.com/piruvari/Analisador_de_voz/issues)
- 💬 **Discussões:** [GitHub Discussions](https://github.com/piruvari/Analisador_de_voz/discussions)

### Desenvolvedor

- **GitHub:** [@piruvari](https://github.com/piruvari)
- **Repositório:** [Analisador_de_voz](https://github.com/piruvari/Analisador_de_voz)

---



## 📊 Status e Roadmap

### Versões

- ✅ **v5.0** (Atual): Sistema completo com 11 features
- 🔄 **v5.1** (Em progresso): Suporte MP3/FLAC
- 📋 **v6.0** (Planejado Q2/2025): Interface web
- 💭 **v7.0** (Futuro): Análise em tempo real

### Estatísticas

- **Estrelas:** ![GitHub stars](https://img.shields.io/github/stars/piruvari/Analisador_de_voz?style=social)
- **Forks:** ![GitHub forks](https://img.shields.io/github/forks/piruvari/Analisador_de_voz?style=social)
- **Issues:** ![GitHub issues](https://img.shields.io/github/issues/piruvari/Analisador_de_voz)

---

<div align="center">

## 🚀 Comece Agora!

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/piruvari/Analisador_de_voz/blob/main/Analizador_de_voz_v5.ipynb)

**Se este projeto foi útil, considere dar uma ⭐!**

---

<sub>Desenvolvido com ❤️ para pesquisa e educação em técnica vocal</sub>

<sub>Este sistema não substitui orientação profissional médica ou pedagógica</sub>

</div>
