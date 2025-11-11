
# 🚀 Guia FlowZap – Instalação e Configuração (n8n + WAHA)

**Versão:** 1.0
**Plataformas:** Windows & Linux
**Projeto:** FlowZap – Automação de WhatsApp Inteligente

---

## 📘 Introdução

Este guia ensina passo a passo como instalar e configurar o ambiente **FlowZap**, que integra o **n8n** e o **WAHA (WhatsApp API Gateway)** para automatizar fluxos de mensagens inteligentes.
O conteúdo é compatível com **Windows** e **Linux**.

---

## 🧩 Etapa 1 – Instalação do Docker

### **Windows**

1. Baixe o **Docker Desktop** em:
   👉 [https://www.docker.com/products/docker-desktop](https://www.docker.com/products/docker-desktop)
2. Instale e abra o aplicativo.
3. Certifique-se de que o Docker está em execução.

### **Linux (Ubuntu/Debian)**

```bash
sudo apt update
sudo apt install docker-compose
sudo systemctl start docker
sudo systemctl enable docker
```

---

## 📁 Etapa 2 – Baixar e preparar os arquivos

1. Crie uma pasta, por exemplo:
   `C:\FlowZap`
2. Baixe o arquivo **docker-compose.yml** do repositório oficial:
   👉 [https://github.com/luizjunior-hub/docker-n8n-waha](https://github.com/luizjunior-hub/docker-n8n-waha)
3. Coloque o arquivo dentro da pasta criada.

---

## ⚙️ Etapa 3 – Subir os containers

Abra o terminal na pasta do projeto:

```bash
cd C:\FlowZap
# ou no Linux
cd ~/FlowZap

docker-compose up -d
```

Após o download das imagens, verifique se os containers estão ativos no **Docker Desktop**:
✅ n8n
✅ waha
✅ postgres
✅ redis

---

## 📱 Etapa 4 – Conectar o WhatsApp no WAHA

1. Acesse [http://localhost:3000](http://localhost:3000) no navegador.
2. No painel WAHA, vá em:
   **Dashboard → Session “default” → Login**
3. Escaneie o **QR Code** com o WhatsApp do celular.

---

## 🧠 Etapa 5 – Configurar o N8N

1. Acesse [http://localhost:5678](http://localhost:5678).
2. Crie sua conta e ative a licença gratuita.
3. Vá em:
   **Settings → Community Nodes → Install a community node**
4. Instale o pacote:

   ```
   n8n-nodes-waha
   ```

---

## 🔄 Etapa 6 – Importar o fluxo JSON

1. No painel do N8N, clique em:
   **Workflows → Import from file**
2. Cole o conteúdo do fluxo JSON do FlowZap.
3. https://github.com/luizjunior-hub/docker-n8n-waha/blob/main/flowzap.json
4. Clique em **Save** para salvar o workflow.

---

## 🚀 Etapa 7 – Testar o fluxo

1. Copie o **Webhook URL** do primeiro nó (Webhook) no N8N.
2. No WAHA, adicione a URL em:
   **Settings → Webhooks → message: received**
3. Envie uma mensagem de teste no WhatsApp, como:

   ```
   Maria, 2500, nada consta, 600
   ```
4. O FlowZap irá processar e responder automaticamente com base nas regras do fluxo.

---

## 🔍 Etapa 8 – Logs e manutenção

Para acompanhar os logs dos containers em tempo real:

```bash
docker-compose logs -f
```

Ou individualmente:

```bash
docker logs -f n8n
docker logs -f waha
```

Esses comandos permitem acompanhar as mensagens e garantir que o sistema está operando corretamente.

---

## ✅ Conclusão

Pronto! 🎉
Seu ambiente **FlowZap** está instalado, o **WhatsApp** conectado e o **fluxo de mensagens inteligente** configurado.

Agora é só começar a criar automações e aprimorar seus fluxos dentro do N8N.

