# 🌦️ ChatClimaBot Telegram

**Consulta de temperatura em tempo real pelo Telegram, com automação no n8n e integração com a API do OpenWeather.**

<p align="center">
  <img src="https://img.shields.io/badge/n8n-Automation-EA4B71?style=for-the-badge&logo=n8n&logoColor=white" alt="n8n">
  <img src="https://img.shields.io/badge/Telegram-Bot_API-26A5E4?style=for-the-badge&logo=telegram&logoColor=white" alt="Telegram Bot API">
  <img src="https://img.shields.io/badge/OpenWeather-Weather_API-EB6E4B?style=for-the-badge&logo=openweathermap&logoColor=white" alt="OpenWeather">
</p>

---

## 📌 Sobre o projeto

O **ChatClimaBot** é um chatbot integrado ao Telegram que permite consultar a temperatura atual de uma cidade por meio de uma mensagem.

Desenvolvido com o **n8n**, o projeto automatiza o recebimento de mensagens, a consulta de informações meteorológicas na API do OpenWeather e o envio da resposta diretamente ao usuário.

A aplicação também contempla o tratamento de cidades não encontradas, proporcionando um retorno mais claro quando a consulta não pode ser concluída.

O projeto demonstra a aplicação prática de automação de workflows, integração entre APIs REST e comunicação por meio de bots.

## ✨ Funcionalidades

- 💬 Recebimento de mensagens pelo Telegram.
- 🌡️ Consulta da temperatura atual de uma cidade.
- 🌍 Integração com a API meteorológica do OpenWeather.
- 📊 Retorno da cidade consultada e da temperatura em graus Celsius.
- ⚠️ Tratamento de consultas para cidades inexistentes.
- 🔐 Configuração de credenciais fora do código-fonte público.
- ⚙️ Automação do fluxo de comunicação utilizando o n8n.

## 🛠️ Tecnologias utilizadas

| Tecnologia | Finalidade |
| --- | --- |
| [n8n](https://n8n.io/) | Criação e execução do workflow de automação |
| [Telegram Bot API](https://core.telegram.org/bots/api) | Comunicação entre o usuário e o chatbot |
| [OpenWeather API](https://openweathermap.org/api) | Consulta de informações meteorológicas |
| JSON | Exportação e compartilhamento do workflow |

## 🔄 Como funciona

### Exemplo de interação

**Mensagem enviada pelo usuário:**

```text
São Paulo,SP,BR
```

**Exemplo de resposta esperada:**

```text
🌤️ A temperatura em São Paulo é de 23°C.
```

*O valor acima é ilustrativo. A temperatura real depende dos dados retornados pela API no momento da consulta.*

Quando a cidade não é encontrada, o bot pode retornar uma mensagem amigável orientando o usuário a verificar o nome informado.

## 📋 Pré-requisitos

Antes de executar o projeto, você precisará de:

- Uma instância do [n8n](https://n8n.io/), local ou na nuvem.
- Uma conta no Telegram.
- Um bot criado por meio do [@BotFather](https://t.me/BotFather).
- Uma chave de API do [OpenWeather](https://openweathermap.org/api).
- O arquivo `workflow-chatbot-telegram.json` disponível neste repositório.

## 🚀 Instalação e configuração

### 1. Clone o repositório

```bash
git clone https://github.com/HiLucasSilva/FTR---ChatClimaBot-Telegram.git
```

Entre na pasta do projeto:

```bash
cd FTR---ChatClimaBot-Telegram
```

### 2. Crie um bot no Telegram

1. Abra o [@BotFather](https://t.me/BotFather).
2. Envie o comando `/newbot`.
3. Defina o nome e o nome de usuário do bot.
4. Copie o token gerado e guarde-o em local seguro.

**Importante:** nunca publique o token do bot em arquivos públicos ou no GitHub.

### 3. Obtenha uma chave do OpenWeather

1. Acesse [OpenWeather](https://openweathermap.org/api).
2. Crie sua conta e gere uma chave de API.
3. Verifique os limites e as condições de utilização do serviço.

### 4. Importe o workflow no n8n

1. Acesse sua instância do n8n.
2. Abra a área de workflows.
3. Selecione a opção de importar um workflow a partir de arquivo.
4. Escolha `workflow-chatbot-telegram.json`.
5. Abra os nós que dependem de credenciais e configure suas próprias credenciais.

Os nomes dos menus podem variar conforme a versão do n8n.

### 5. Configure as credenciais

**Telegram**

Crie uma credencial compatível com a API do Telegram no n8n e associe-a aos nós responsáveis por receber e enviar mensagens.

**OpenWeather**

Configure a credencial utilizada pelo nó de requisição HTTP, de acordo com o método de autenticação definido no workflow.

A chave deve ser fornecida por meio das credenciais gerenciadas pelo n8n ou da configuração de ambiente prevista pelo fluxo.

> Os nomes `TELEGRAM_BOT_TOKEN` e `OPENWEATHER_API_KEY` podem ser utilizados como referências de configuração, mas o workflow precisa estar preparado para ler essas variáveis caso você escolha esse método.

### 6. Execute o chatbot

1. Confira se todas as credenciais foram associadas corretamente.
2. Salve o workflow.
3. Ative ou publique o fluxo, conforme a configuração da sua instância.
4. Abra o bot no Telegram.
5. Envie o nome de uma cidade no formato aceito pelo workflow.

Exemplos de entrada:

```text
São Paulo,SP,BR
Rio de Janeiro,RJ,BR
Belo Horizonte,MG,BR
```

## 🧪 Testes e validação

Após a configuração, recomenda-se executar os seguintes testes:

- [ ] Importar o workflow em uma instância do n8n.
- [ ] Configurar as credenciais do Telegram e do OpenWeather.
- [ ] Consultar pelo menos três cidades válidas.
- [ ] Verificar se a temperatura é retornada em graus Celsius.
- [ ] Testar uma cidade inexistente.
- [ ] Validar o recebimento e o envio das mensagens.
- [ ] Revisar o arquivo JSON para garantir que não contenha credenciais ou segredos.

## 📁 Estrutura do projeto

```text
FTR---ChatClimaBot-Telegram/
│
├── workflow-chatbot-telegram.json
└── README.md
```

- `workflow-chatbot-telegram.json`: workflow exportado para importação no n8n.
- `README.md`: documentação do projeto, instalação e configuração.

## 🔒 Segurança

A segurança das credenciais é essencial para manter a integração protegida.

- Nunca compartilhe tokens do Telegram ou chaves privadas do OpenWeather.
- Não inclua credenciais reais no README ou em arquivos versionados.
- Revise os arquivos JSON antes de enviá-los ao repositório.
- Prefira as credenciais gerenciadas pelo n8n.
- Caso uma chave seja exposta, revogue-a e gere uma nova.

## 🎯 Objetivos de aprendizado

Este projeto foi desenvolvido para explorar conceitos importantes do desenvolvimento de soluções integradas:

- Automação de processos com n8n.
- Integração entre serviços externos por meio de APIs.
- Comunicação automatizada com bots do Telegram.
- Processamento de requisições HTTP e respostas JSON.
- Tratamento de erros e validação de resultados.
- Boas práticas de documentação e segurança.

## 🔮 Melhorias futuras

Algumas possibilidades para evoluir o projeto:

- 🌧️ Consultar a previsão do tempo para os próximos dias.
- 💧 Exibir umidade, sensação térmica e velocidade do vento.
- 📍 Melhorar a identificação de cidades e a validação das entradas.
- 🧾 Padronizar mensagens de erro e respostas.
- 🖼️ Adicionar capturas de tela do chatbot em funcionamento à documentação.

Essas melhorias são sugestões para versões futuras, não funcionalidades já implementadas.

## 👨‍💻 Autor

**Lucas Mendonça Silva**

Desenvolvedor em formação, interessado em desenvolvimento de software, automação e integração de sistemas.

- GitHub: [@HiLucasSilva](https://github.com/HiLucasSilva)

---

<p align="center">
  Desenvolvido com dedicação para explorar o potencial da automação e das APIs.
</p>

<p align="center">
  ⭐ Se este projeto foi útil para você, considere deixar uma estrela no repositório!
</p>
