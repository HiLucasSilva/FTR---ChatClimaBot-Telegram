
FTR---ChatClimaBot-Telegram
Repository navigation
Code
Issues
Pull requests
Agents
Actions
Projects
Wiki
Security and quality
Insights
Settings
FTR---ChatClimaBot-Telegram
/
README.md
in
main

Edit

Preview
ChatClimaBot — Chatbot de clima no Telegram

O ChatClimaBot é um chatbot desenvolvido no n8n que recebe o nome de uma cidade pelo Telegram, consulta a API do OpenWeather e responde com a temperatura atual. Quando a cidade não é encontrada ou a API retorna uma resposta inválida, o bot envia uma mensagem de erro amigável. Funcionalidades

Recebe mensagens enviadas ao bot pelo Telegram.
Consulta a temperatura atual usando a API do OpenWeather.
Retorna a cidade e a temperatura em graus Celsius.
Trata cidades inexistentes com uma mensagem de erro.
Mantém tokens e chaves de API nas credenciais do n8n, fora do repositório. Tecnologias utilizadas
n8n — automação do workflow.
Telegram Bot API — comunicação com o usuário.
OpenWeather Current Weather API — consulta meteorológica. Pré-requisitos
Uma instância do n8n Cloud ou n8n instalado localmente.
Um bot criado pelo @BotFather no Telegram.
Uma chave de API do OpenWeather.
O arquivo workflow-chatbot-telegram.json, exportado do workflow funcional no n8n. Arquivos da entrega
workflow-chatbot-telegram.json — workflow exportado do n8n.
README.md — documentação do projeto. Não publique tokens, chaves de API, credenciais exportadas ou outros segredos. O JSON exportado deve ser revisado antes de ser enviado ao repositório.
Como importar o workflow no n8n

Entre na sua instância do n8n.

Abra a área Workflows.

Use o menu de opções e escolha Import from File (o nome pode variar conforme a versão).

Selecione workflow-chatbot-telegram.json.

Abra os nós que utilizam credenciais e associe as credenciais criadas na sua própria instância.

Confira as configurações dos nós e salve o workflow.

Ative ou publique o workflow conforme a versão e o tipo de instância do n8n. Configuração das credenciais As credenciais devem ser configuradas diretamente no n8n. Não coloque os valores reais das chaves no arquivo JSON, no README ou no código do workflow.

Telegram

No Telegram, converse com o @BotFather e crie um bot, se ainda não tiver um.

Copie o token fornecido pelo BotFather.

No n8n, abra Credentials e crie uma credencial do tipo Telegram API (o nome pode variar conforme a versão).

Insira o token no campo correspondente e salve a credencial.

No workflow importado, selecione essa credencial nos nós do Telegram Trigger e do envio de mensagens. Variável documentada para o ambiente: TELEGRAM_BOT_TOKEN. A variável acima documenta o nome esperado para a configuração. O workflow pode usar o sistema de credenciais gerenciadas do n8n em vez de ler diretamente uma variável de ambiente.

OpenWeather

Crie ou acesse sua conta no OpenWeather.

Gere uma chave de API.

No n8n, abra Credentials e crie ou edite a credencial de autenticação usada pelo nó HTTP Request.

Configure a chave como parâmetro de consulta appid, de acordo com a configuração do workflow.

Salve a credencial e selecione-a no nó HTTP Request. Variável documentada para o ambiente: OPENWEATHER_API_KEY. Se o workflow utilizar uma credencial Query Auth, mantenha a chave dentro dessa credencial. Não adicione a chave real diretamente aos parâmetros do nó nem ao JSON exportado. Se a sua versão do workflow estiver configurada para ler variáveis de ambiente, defina OPENWEATHER_API_KEY no ambiente do n8n e ajuste a expressão do nó para usar essa variável. O método escolhido deve ser consistente com a configuração exportada.

Como executar o chatbot

Importe o workflow e configure as credenciais do Telegram e OpenWeather.
Salve e ative/publique o workflow.
Abra o bot no Telegram e envie uma cidade no formato aceito pelo workflow. Exemplos:
São Paulo,SP,BR
Rio de Janeiro,RJ,BR
Belo Horizonte,MG,BR
Para uma cidade válida, o bot deve responder com a cidade e a temperatura atual em °C, por exemplo: 🌤️ A temperatura em São Paulo é de 23°C. A temperatura é ilustrativa e varia conforme a consulta.
Para testar o tratamento de erro, envie um nome de cidade inexistente, por exemplo CidadeQueNaoExiste999,XX,BR. O bot deve responder com uma mensagem amigável, como: ❌ Cidade não encontrada! Confira o nome e tente novamente. Checklist de validação
 Importar o workflow em uma instância limpa do n8n e configurar as credenciais.
 Testar pelo menos três cidades válidas, por exemplo São Paulo, Rio de Janeiro e Belo Horizonte.
 Testar uma cidade inexistente e confirmar a mensagem de erro.
 Conferir se as mensagens enviadas pelo bot estão formatadas corretamente.
 Revisar o JSON exportado e garantir que não contém tokens, chaves de API ou outros segredos.
 Confirmar que o repositório público contém workflow-chatbot-telegram.json e README.md, sem arquivos de credenciais ou segredos. Segurança
Nunca envie TELEGRAM_BOT_TOKEN ou OPENWEATHER_API_KEY para o GitHub.
Use credenciais protegidas pelo n8n ou variáveis de ambiente configuradas no servidor.
Se um token ou uma chave for exposto acidentalmente, revogue-o e gere outro antes de continuar.
