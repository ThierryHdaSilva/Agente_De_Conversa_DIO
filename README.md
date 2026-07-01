# 🎙️ Assistente de Voz com Whisper + Gemini

Agente conversacional por voz que grava áudio do microfone, transcreve com o
[Whisper](https://github.com/openai/whisper) (OpenAI), envia o texto para a
API do **Google Gemini** e converte a resposta de volta em voz (TTS).

> **Nota sobre a escolha do modelo de linguagem:** o material de referência
> deste projeto (curso da [DIO](https://www.dio.me/)) sugere o uso da API
> da OpenAI (ChatGPT). Como a API da OpenAI não oferece mais um plano
> gratuito (é necessário cadastrar cartão e comprar créditos), optei por
> usar a **API do Google Gemini** como alternativa gratuita. A lógica do
> projeto (transcrição → pergunta → resposta) permanece a mesma descrita
> no curso — apenas o provedor do modelo de linguagem (LLM) foi trocado.

## ▶️ Como usar

O projeto foi desenvolvido e é executado inteiramente no **Google Colab**
(por causa do acesso ao microfone via navegador). Basta abrir o notebook
pelo link abaixo e rodar as células em ordem:

🔗 **[Abrir no Google Colab](COLOQUE_AQUI_O_LINK_DO_SEU_COLAB)**

## ⚙️ Configuração necessária

Antes de rodar, você precisa de uma API key **gratuita** do Google Gemini:

1. Gere sua chave em [aistudio.google.com/app/apikey](https://aistudio.google.com/app/apikey)
   (login com conta Google, sem necessidade de cartão de crédito)
2. No Colab, abra o painel lateral esquerdo → ícone de chave (🔑) → **Add new secret**
3. Nome: `GEMINI_API_KEY` — Valor: sua chave
4. Ative o toggle **"Notebook access"**

> A chave nunca fica salva no notebook — ela é lida em tempo de execução via
> `google.colab.userdata`, então é seguro compartilhar este projeto publicamente.

## 🧩 Como funciona

1. **Gravação** — captura áudio do microfone via JavaScript (`MediaRecorder`)
   dentro do navegador, já que o Colab roda num servidor remoto sem acesso
   direto ao hardware.
2. **Transcrição** — o áudio é processado pelo modelo Whisper (`small`),
   convertendo fala em texto (português).
3. **Resposta** — o texto transcrito é enviado à API do Gemini
   (`gemini-2.5-flash`), que retorna uma resposta em linguagem natural.
4. **Fala** — a resposta em texto é convertida de volta em áudio com
   `gTTS` (Google Text-to-Speech) e reproduzida automaticamente.

## 🛠️ Tecnologias

- [OpenAI Whisper](https://github.com/openai/whisper) — transcrição de fala
- [Google Gemini API](https://ai.google.dev/gemini-api/docs) — geração de resposta (LLM)
- [gTTS](https://github.com/pndurette/gTTS) — conversão de texto em voz
- [pydub](https://github.com/jiaaro/pydub) — manipulação e ajuste de áudio
- Google Colab — ambiente de execução

## 📌 Status

Projeto em desenvolvimento, com fins de estudo (agentes de IA, processamento
de áudio e integração com LLMs), realizado como atividade da [DIO](https://www.dio.me/).
