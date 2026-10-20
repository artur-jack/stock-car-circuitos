# Traçados para SAS Visual Analytics

Componente de Data-Driven Content para GitHub Pages. Sem bibliotecas externas, autenticação,
credenciais ou dados de telemetria. Não publica nem transmite as linhas recebidas do SAS.
As imagens externas são carregadas diretamente no navegador quando há uma URL HTTPS.

## Conteúdo desta primeira versão

- Interlagos: desenho SVG extraído do viewer HTML fornecido no projeto, incluído no próprio index.html.
- Velocitta: referência à imagem da ficha técnica publicada por Audace Tech/Chronon, com crédito e link.
- Brasília: `brasilia.png`, recorte do diagrama renderizado da ficha PDF pública de Audace Tech/Chronon.
  Fonte: https://www.chronon.com.br/wp-content/uploads/2025/11/Brasiliapista.pdf
- Demais pistas: identificação e link à ficha técnica; mensagem explícita de imagem ainda não cadastrada.
- Não infere desenhos de circuito a partir de coordenadas do mapa do Brasil.
- Uma imagem indicada na terceira variável substitui o desenho padrão. Pode ser URL HTTPS de PNG,
  JPEG, WebP ou SVG servido como imagem. Não use a URL de uma página HTML ou PDF como imagem.
- Uso para referência: não afirma que o traçado representa a configuração de uma corrida de 2026.

## Publicação no GitHub

1. Crie um repositório público chamado `stock-car-circuitos`, com README.
2. Use Add file → Upload files e envie `index.html`, `brasilia.png` e `.nojekyll` à raiz do repositório.
   Também pode enviar este README. Não é necessário enviar dados CSV ou o relatório JSON.
3. Faça Commit changes.
4. Settings → Pages → Source: Deploy from a branch → main → /(root) → Save.
5. Aguarde a confirmação de publicação e abra a URL informada pelo GitHub, normalmente
   `https://SEU_USUARIO.github.io/stock-car-circuitos/`.
6. Fora do SAS aparece um seletor de prévia. Dentro do SAS ele fica oculto.

## Configuração no VA

No objeto Conteúdo baseado em dados, use a URL publicada e atribua as variáveis nesta ordem:

1. circuito_id (categoria)
2. Circuito (campo nome renomeado; categoria)
3. imagem_tracado_url (categoria; pode estar vazia)

A imagem enviada pelo usuário mostra `imagem_circuito_url`: ela também funcionará se estiver na
terceira posição e contiver uma URL de imagem, mas prefira `imagem_tracado_url` para o desenho.
Parâmetros não são necessários.

A fonte deve ser a mesma dos cartões, CIRCUITOS_2026_BASE. Abra a página através da ligação do mapa.
Se receber nove pistas, o componente mostra aviso em vez de escolher a primeira silenciosamente.
Confira a passagem dos filtros e a fonte de dados do objeto. Um filtro mapa → componente na mesma
página pode ser usado para teste. Requisições do VA podem falhar ou ter limites de domínio definidos
pelo administrador; GitHub Pages não contorna essas políticas.

## Segurança e implementação

Recebe somente mensagens do iframe pai, em origem HTTPS terminada em `.sas.com` (Viya for Learners).
Para outro domínio SAS institucional, adaptar explicitamente a lista no index.html.
Insere nomes com textContent; URLs de imagem devem ser HTTPS, sem usuário/senha.
Não utiliza cookies, analytics ou chamadas de API para enviar os dados recebidos.

Protocolo de mensagens conforme exemplo SAS:
https://github.com/sassoftware/sas-visualanalytics-thirdpartyvisualizations/blob/master/util/messagingUtil.js

Exemplo de imagens dinâmicas:
https://communities.sas.com/t5/SAS-Communities-Library/Embedding-Dynamic-Web-Pages-and-Images-in-SAS-Visual-Analytics/ta-p/763749

## Próxima atualização

Para adicionar imagens autorizadas, hospede-as na pasta `imagens/` e preencha a terceira variável
no cadastro com seu endereço HTTPS. Registre fonte e crédito. Esta versão não copia os arquivos
externos para o repositório nem altera automaticamente os CSVs do relatório.
