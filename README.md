# Emissão em Massa de Certificados

Sistema de automação para geração e envio em massa de certificados personalizados, utilizando Google Sheets, Google Slides, Google Drive e Google Apps Script.

O projeto permite processar uma lista de participantes contendo nome e e-mail, gerar um certificado individual para cada pessoa e enviar automaticamente o respectivo PDF para seu endereço de e-mail.

# Sobre o projeto

Em eventos, cursos e atividades com muitos participantes, criar e enviar certificados individualmente pode consumir muito tempo.

Este projeto foi desenvolvido para automatizar esse processo.

A partir de uma planilha contendo:

* nome do participante;
* e-mail do participante;

o sistema:

1. cria uma cópia do certificado;
2. personaliza o nome;
3. gera o PDF;
4. envia o arquivo para o participante;
5. registra o resultado do envio.

## 🔄 Fluxo da automação

```text
📊 Lista de participantes
       │
       ▼
 Google Apps Script
       │
       ├──────────────┐
       ▼              ▼
 Google Slides     E-mail
       │              │
       ▼              │
 PDF personalizado   ─┘
       │
       ▼
Google Drive
```

## Funcionalidades

* Processamento de múltiplos participantes
* Personalização automática dos certificados
* Geração individual de PDFs
* Envio para o e-mail correspondente
* Salvamento dos certificados no Google Drive
* Registro do status de cada participante
* Registro da data do envio
* Registro de erros
* Prevenção contra reenvio de certificados já processados
* Função de teste individual
* Possibilidade de reutilização para diferentes turmas e eventos

## Tecnologias utilizadas

* JavaScript
* Google Apps Script
* Google Sheets
* Google Slides
* Google Drive
* MailApp

## Estrutura da planilha

A planilha inicialmente contém:

* Nome
* E-mail

Durante a execução, o sistema adiciona colunas de controle:

* Status
* Data do envio
* Erro

## Controle de duplicidade

Uma das funcionalidades importantes do projeto é evitar o envio duplicado.

Antes de processar um participante, o sistema verifica o campo `Status`.

Se estiver:

```text
Enviado
```

o participante é ignorado.

Isso permite executar o script novamente sem reenviar certificados que já foram processados.

## Personalização do certificado

O modelo é criado no Google Slides utilizando o marcador:

```text
{{NOME}}
```

O script substitui esse marcador pelo nome correspondente da planilha.

## Modo de teste

O projeto possui uma função para testar o processo utilizando apenas o primeiro participante da lista.

Isso permite verificar:

* personalização;
* geração do PDF;
* armazenamento;
* envio do e-mail.

Somente após a validação deve ser executada a função de processamento em massa.

## Limitações

O Google Apps Script possui limites de tempo de execução e envio de e-mails.

Para listas maiores, o processamento pode precisar ser dividido em lotes ou adaptado para retomar automaticamente de onde parou.

O projeto foi estruturado para reduzir o impacto desses limites através do controle de status dos participantes.

## Possíveis melhorias

* Processamento automático em lotes;
* Retomada automática após limite de execução;
* Barra de progresso;
* Dashboard;
* Geração de número único para cada certificado;
* QR Code de validação;
* Página pública de autenticação;
* Histórico de certificados emitidos;
* Seleção de diferentes modelos;
* Personalização de múltiplos campos.

## Resultado

O sistema permite transformar uma lista de participantes em certificados personalizados sem a necessidade de editar e enviar cada documento manualmente.

Em um teste real, o sistema foi utilizado para automatizar o envio de certificados para uma lista de 80 participantes.


## Autora

Kamylla Carlos

Projeto desenvolvido como parte do portfólio de **programação, automação e tecnologia**.
