[Personal IA.json](https://github.com/user-attachments/files/24084634/Personal.IA.json)# N8N-template
Agente de Atendimento Automático com n8n 🤖

Agente de IA para Personal Trainer 🏋🥬

Funcionalidades:

* Responde mesagens automaticamente.
* Respostas inteligentes geradas pelo GPT 4 MINI.
* IA reconhece audios , imagens , documentos e textos.
* Possue uma agenda do Google Calendar de testes já pronta (Você deve pegar de base a que já existe e criar em seu email uma agenda).
* Anota dados dos clientes e informações sobre treinos , mensalidades , etc.
* Entre Demais Coisas


  Ferramentas Usadas:

  * OpenAI
  * Google Sheets
  * Google Calendar
  * N8N


    Preview
    
  <img width="1741" height="381" alt="Captura de tela 2025-12-10 141214" src="https://github.com/user-attachments/assets/f9d3255d-590e-4fb6-a942-cf066fa8670a" />



Como Usar: 

1) Importe o Fluxo
2) Configure suas credenciais
3) Rode o Fluxo!


[Personal IA.json](https://github.com/user-attachments/files/24084693/Personal.IA.json)
{
  "name": "Personal IA",
  "nodes": [
    {
      "parameters": {
        "promptType": "define",
        "text": "={{ $json.messages }}",
        "options": {
          "systemMessage": "=<orientação geral>\n\n\nVocê é o Assistente Virtual do Personal Gabriel , sua função é ser receptível e cordial com os clientes , gerenciar agendamentos de treinos , acolher/buscar novos clientes , responder duvidas recorrentes , realizar reagendamentos e cancelamento.\n\nInformações fixas:\n\nNome do Profissional: [Gabriel]\n\nLocal de Trabalho: Onyx Academia - Avenida Miguel Paes, 808, centro de Igarapé, CEP 32.900-000   e  PowerFitness - Rua Miguel Henriques da Silva, 283\n\nFuncionamento: [Segunda a Sábado de 7h as 13h]\n\nDias fechados: [Domingo]\n\nFormas de pagamento: [FORMAS: Pix]\n\nTelefone do cliente: {{ $('Normaliza').item.json.message.chat_id.toString() }}\n\nHoje: {{ $now.toString() }} — {{ new Date().toLocaleDateString('pt-BR', { weekday: 'long' }) }}\n\nTempo de sessão : 70 minutos\n\nTempo de experiência : 3 anos\n\nFormações: Formado em Educação Física na Universidade PUC \n\n\n</orientação geral>\n\n\n<passo_a_passo>\n\nPasso a passo para criar um agendamento de aula experimental:\n\n1) Quando o Cliente estiver interessado e confirmar que deseja realizar uma aula experimental envie o link desta agenda pra ele :\n\nhttps://calendar.google.com/calendar/u/0/appointments/schedules/AcZssZ3hoV_00Oh4-tZP-fNZU3ryVpfTvkea_to8SZbMJiS0H_FuKUti-Yv_ludVqzY9AKKRDpQ7y287\n\n\nRegra Geral para criar uma agendamento: envie SEMPRE esse link para o cliente se ele tiver o desejo de realizar uma Aula experimental\n\nhttps://calendar.google.com/calendar/u/0/appointments/schedules/AcZssZ3hoV_00Oh4-tZP-fNZU3ryVpfTvkea_to8SZbMJiS0H_FuKUti-Yv_ludVqzY9AKKRDpQ7y287\n\n\nQuando enviar o link da agenda finalize com isso:\n\n\"Basta escolher a data e horário que melhor se adequa para você. Se precisar de ajuda com algo mais, é só me avisar! 😊\"\n\n\nCaso o cliente queira desmarcar ou reagendar , fale com ele que ele pode realizar isso na próprio link da agenda : \n\nhttps://calendar.google.com/calendar/u/0/appointments/schedules/AcZssZ3hoV_00Oh4-tZP-fNZU3ryVpfTvkea_to8SZbMJiS0H_FuKUti-Yv_ludVqzY9AKKRDpQ7y287\n\n</passo_a_passo>\n\n\n\n\nPasso a passo para fechar pacotes : \n\n\nCaso o cliente queira fechar um pacote , acione a ferramenta \"Tabela de Valores\" e mostre a ele o menu. \n\nAssim que ele confirmar o serviço que ele deseja , peça as informações abaixo:\n\nNome: (nome do cliente)\n\nServiço: (Plano mensal, plano semestral , plano anual, Avaliação física)\n\nTelefone: o telefone do cliente é o \n{{ $('Normaliza').item.json.message.chat_id.toString() }}\n\n\nAssim que o cliente confirmar que vai fechar um pacote envie a chave pix : 150.417.086-57 (Cpf).\n\n\nAssim que isso for enviado , peça para o cliente avisar que o pagamento foi realizado!\n\nLogo em seguida que o cliente disser que o pagamento foi realizado, acione a ferramenta \"Anotar1\" e registre o {nome} , {Telefone} e {Servico}\n\n\n\nPasso a passo para buscar informações do  plano/serviço do cliente (se ele pediu/deseja saber):\n\n\nAcione a ferramenta \"Buscar1\" e informe o Status do Servico/Plano dele e o informe:\n\n\"O {Servico} no nome:{Nome} do {Telefone} esta em {Status}\"\n\n\n\n\n<ferramentas>\n\n\"Tabela de Valores\"\n\n\"Calculator\"\n\n\"Anotar1\" : Registar informações de um novo assinante\n\n\"Buscar1\" : É obrigatório consultar para verificar as informações sobre o pacote que o cliente tem no banco de dados. Não confie na memória.\n\n\n</ferramentas>\n\n<regras_de_decisao>\n\nIdentificar intenção: orçamento / agendar \n\nSempre ser preciso e cordial em suas falas/afirmações.\n\nNão realizar nada fora do padrão , ou seja não fugir da sua função e nem do que está no prompt.\n\n</regras_de_decisao>\n\n<restricoes>\n\nHorários sempre em 24h.\n\nTools com ISO 8601.\n\nSempre consultar a ferramenta \"Tabela de Valores\" para preços.\n\n</restricoes>\n\n<serviços adicionais>\n\nAvaliação física\n \nFixa de treino personalizado\n"
        }
      },
      "id": "13610c88-3d91-4314-82b7-b7ba9585ddf5",
      "name": "AI Agent1",
      "type": "@n8n/n8n-nodes-langchain.agent",
      "typeVersion": 1.6,
      "position": [
        6220,
        -660
      ]
    },
    {
      "parameters": {
        "method": "POST",
        "url": "={{ $('Normaliza').item.json.instance.Server_url }}/message/sendText/{{ $('Normaliza').item.json.instance.Name }} ",
        "sendHeaders": true,
        "headerParameters": {
          "parameters": [
            {
              "name": "apikey",
              "value": "={{ $('Normaliza').item.json.instance.Apikey }}"
            }
          ]
        },
        "sendBody": true,
        "specifyBody": "json",
        "jsonBody": "={\n  \"number\": \"{{ $('Normaliza').item.json.message.chat_id || $('Normaliza').item.json.message.lid }}\",\n  \"text\": \"{{ $json.output.replace(/\\n/g, '\\\\n').replace(/\\\"/g, '\\\\\"').trim() }}\"\n}",
        "options": {}
      },
      "type": "n8n-nodes-base.httpRequest",
      "typeVersion": 4.2,
      "position": [
        7480,
        260
      ],
      "id": "0fa5b3ea-9527-4d35-920b-a9673c236ecf",
      "name": "Enviar Mensagem Whatsaap"
    },
    {
      "parameters": {
        "assignments": {
          "assignments": [
            {
              "id": "8f16b1bf-1a3e-4029-8d7a-1bccb919ee43",
              "name": "message.message_id",
              "value": "={{ $json.body.data.key.id || '' }}",
              "type": "string"
            },
            {
              "id": "11800d83-ecca-4f9c-a878-a2419db0c8e9",
              "name": "message.chat_id",
              "value": "={{ $json.body.data.key.remoteJid.split('@')[0] || '' }}",
              "type": "string"
            },
            {
              "id": "c33f9527-e661-49e5-8e5e-64f3b430928a",
              "name": "message.content_type",
              "value": "={{ $('Webhook1').item.json.body.data.message.extendedTextMessage ? 'text' : '' }}{{ $('Webhook1').item.json.body.data.message.conversation ? 'text' : '' }}{{ $('Webhook1').item.json.body.data.message.audioMessage ? 'audio' : '' }}{{ $('Webhook1').item.json.body.data.message.imageMessage ? 'image' : '' }}",
              "type": "string"
            },
            {
              "id": "06eba1c9-cff0-4f68-b6da-6bb0092466b7",
              "name": "message.content",
              "value": "={{ $('Webhook1').item.json.body.data.message.extendedTextMessage?.text || '' }}{{ $('Webhook1').item.json.body.data.message.imageMessage?.caption || '' }}{{ $('Webhook1').item.json.body.data.message.conversation || '' }}",
              "type": "string"
            },
            {
              "id": "b97f1af3-5361-46fc-9303-d644921231d8",
              "name": "message.Timestamp",
              "value": "={{ $('Webhook1').item.json.body.data.messageTimestamp.toDateTime('s').toISO() }}",
              "type": "string"
            },
            {
              "id": "dc3dc59c-90a3-4a45-bea2-de092c91083b",
              "name": "message.Content_URL",
              "value": "={{ $('Webhook1').item.json.body.data.message.audioMessage?.url || '' }}{{ $('Webhook1').item.json.body.data.message.imageMessage?.url || '' }}",
              "type": "string"
            },
            {
              "id": "8b01a818-a456-476e-bace-adefe2f04eb4",
              "name": "message.event",
              "value": "={{ $('Webhook1').item.json.body.data.key.fromMe ? 'outcoming' : 'incoming' }}",
              "type": "string"
            },
            {
              "id": "b2f1f6b5-292f-4695-9e41-be200c6d7053",
              "name": "instance.Name",
              "value": "={{ $json.body.instance }}",
              "type": "string"
            },
            {
              "id": "572fcce5-8a26-4e8f-a48a-ef0bee569dcd",
              "name": "instance.Apikey",
              "value": "={{ $json.body.apikey }}",
              "type": "string"
            },
            {
              "id": "e90043db-657b-461c-b040-2d6089abfbdb",
              "name": "instance.Server_url",
              "value": "={{ $json.body.server_url }}",
              "type": "string"
            },
            {
              "id": "348264f9-ed02-4936-ae78-bb963ccbee29",
              "name": "apiKey_eleven",
              "value": "sk_0060ad",
              "type": "string"
            }
          ]
        },
        "options": {}
      },
      "id": "d61b152f-a2c5-4266-a467-0e70e59f8b6e",
      "name": "Normaliza",
      "type": "n8n-nodes-base.set",
      "typeVersion": 3.4,
      "position": [
        -320,
        280
      ]
    },
    {
      "parameters": {
        "httpMethod": "POST",
        "path": "4477b68b-4ae1-4ee0-850e-c029c35f5bda",
        "options": {}
      },
      "type": "n8n-nodes-base.webhook",
      "typeVersion": 2,
      "position": [
        -600,
        -120
      ],
      "id": "808592ce-7a12-4f73-9863-a2e0a830c3b5",
      "name": "Webhook1",
      "webhookId": "4477b68b-4ae1-4ee0-850e-c029c35f5bda"
    },
    {
      "parameters": {
        "rules": {
          "values": [
            {
              "conditions": {
                "options": {
                  "caseSensitive": true,
                  "leftValue": "",
                  "typeValidation": "strict",
                  "version": 2
                },
                "conditions": [
                  {
                    "leftValue": "={{ $json.message.event }}",
                    "rightValue": "outcoming",
                    "operator": {
                      "type": "string",
                      "operation": "equals"
                    },
                    "id": "da030431-061c-401a-811f-0a8f1c8b7206"
                  }
                ],
                "combinator": "and"
              },
              "renameOutput": true,
              "outputKey": "outcoming"
            },
            {
              "conditions": {
                "options": {
                  "caseSensitive": true,
                  "leftValue": "",
                  "typeValidation": "strict",
                  "version": 2
                },
                "conditions": [
                  {
                    "id": "5aa84cbc-b918-4ac7-9539-24645e09d6bb",
                    "leftValue": "={{ $json.message.event }}",
                    "rightValue": "incoming",
                    "operator": {
                      "type": "string",
                      "operation": "equals",
                      "name": "filter.operator.equals"
                    }
                  }
                ],
                "combinator": "and"
              },
              "renameOutput": true,
              "outputKey": "incoming"
            }
          ]
        },
        "options": {}
      },
      "type": "n8n-nodes-base.switch",
      "typeVersion": 3.2,
      "position": [
        40,
        140
      ],
      "id": "5c3214fa-0dff-415a-a961-fafe45ea2744",
      "name": "Switch"
    },
    {
      "parameters": {
        "operation": "set",
        "key": "={{ $json.message.chat_id }}_timeout",
        "value": "true",
        "keyType": "string",
        "expire": true,
        "ttl": 900
      },
      "type": "n8n-nodes-base.redis",
      "typeVersion": 1,
      "position": [
        380,
        -220
      ],
      "id": "aea3fff0-3ebf-4b63-9102-d47a921f3547",
      "name": "Gera Timeout",
      "credentials": {
        "redis": {
          "id": "LJnIUUJF6ZcmT5jv",
          "name": "Redis teste1"
        }
      }
    },
    {
      "parameters": {
        "operation": "get",
        "propertyName": "block",
        "key": "={{ $json.message.chat_id }}_timeout",
        "options": {}
      },
      "type": "n8n-nodes-base.redis",
      "typeVersion": 1,
      "position": [
        420,
        400
      ],
      "id": "6420b97d-0038-4e99-9193-ef7c4306d865",
      "name": "Get block",
      "credentials": {
        "redis": {
          "id": "LJnIUUJF6ZcmT5jv",
          "name": "Redis teste1"
        }
      }
    },
    {
      "parameters": {
        "rules": {
          "values": [
            {
              "conditions": {
                "options": {
                  "caseSensitive": true,
                  "leftValue": "",
                  "typeValidation": "strict",
                  "version": 2
                },
                "conditions": [
                  {
                    "leftValue": "={{ $json.block }}",
                    "rightValue": "",
                    "operator": {
                      "type": "string",
                      "operation": "empty",
                      "singleValue": true
                    },
                    "id": "93d75160-e708-48fa-a01d-cd696b570f15"
                  }
                ],
                "combinator": "and"
              },
              "renameOutput": true,
              "outputKey": "IA PODE RESPONDER"
            },
            {
              "conditions": {
                "options": {
                  "caseSensitive": true,
                  "leftValue": "",
                  "typeValidation": "strict",
                  "version": 2
                },
                "conditions": [
                  {
                    "id": "aa823b00-22db-438e-a821-d988ff7dd684",
                    "leftValue": "={{ $json.block }}",
                    "rightValue": "true",
                    "operator": {
                      "type": "string",
                      "operation": "equals",
                      "name": "filter.operator.equals"
                    }
                  }
                ],
                "combinator": "and"
              },
              "renameOutput": true,
              "outputKey": "IA NÃO PODE RESPONDER"
            }
          ]
        },
        "options": {}
      },
      "type": "n8n-nodes-base.switch",
      "typeVersion": 3.2,
      "position": [
        780,
        120
      ],
      "id": "efca0e11-251d-47bd-a3ce-0347fac5355e",
      "name": "Switch1"
    },
    {
      "parameters": {},
      "type": "n8n-nodes-base.noOp",
      "typeVersion": 1,
      "position": [
        1120,
        440
      ],
      "id": "5fe4ba4b-dd04-45b6-a666-42c3567952db",
      "name": "No Operation, do nothing"
    },
    {
      "parameters": {
        "content": "## Intervenção Humana - Timeout",
        "height": 1076,
        "width": 2099,
        "color": 6
      },
      "id": "9c4f3262-41d8-4bd9-a13d-bed441678ab5",
      "name": "Sticky Note2",
      "type": "n8n-nodes-base.stickyNote",
      "typeVersion": 1,
      "position": [
        -640,
        -340
      ]
    },
    {
      "parameters": {
        "content": "",
        "height": 856,
        "width": 2019,
        "color": 2
      },
      "id": "6e21fc72-c4fe-4e26-ab31-0a0f2d1a195d",
      "name": "Sticky Note",
      "type": "n8n-nodes-base.stickyNote",
      "typeVersion": 1,
      "position": [
        -620,
        -220
      ]
    },
    {
      "parameters": {
        "content": "",
        "height": 1476,
        "width": 2139,
        "color": 7
      },
      "id": "8ff306d8-25e1-41f8-a25f-942148f9a5d3",
      "name": "Sticky Note3",
      "type": "n8n-nodes-base.stickyNote",
      "typeVersion": 1,
      "position": [
        1480,
        -740
      ]
    },
    {
      "parameters": {
        "content": "",
        "height": 1296,
        "width": 1979,
        "color": 6
      },
      "id": "95e3aad2-168a-44a1-8c49-4702b21490de",
      "name": "Sticky Note4",
      "type": "n8n-nodes-base.stickyNote",
      "typeVersion": 1,
      "position": [
        1580,
        -600
      ]
    },
    {
      "parameters": {
        "rules": {
          "values": [
            {
              "conditions": {
                "options": {
                  "caseSensitive": true,
                  "leftValue": "",
                  "typeValidation": "strict",
                  "version": 1
                },
                "conditions": [
                  {
                    "id": "101c3ff7-e997-43bb-8e99-fe82746c5993",
                    "leftValue": "={{ $('Webhook1').item.json.body.data.message.audioMessage }}",
                    "rightValue": "",
                    "operator": {
                      "type": "object",
                      "operation": "notEmpty",
                      "singleValue": true
                    }
                  }
                ],
                "combinator": "and"
              },
              "renameOutput": true,
              "outputKey": "audioMessage"
            },
            {
              "conditions": {
                "options": {
                  "caseSensitive": true,
                  "leftValue": "",
                  "typeValidation": "strict",
                  "version": 1
                },
                "conditions": [
                  {
                    "id": "38226af4-80fe-4155-9ceb-2379f44e29ed",
                    "leftValue": "={{ $('Webhook1').item.json.body.data.message.imageMessage }}",
                    "rightValue": "",
                    "operator": {
                      "type": "object",
                      "operation": "notEmpty",
                      "singleValue": true
                    }
                  }
                ],
                "combinator": "and"
              },
              "renameOutput": true,
              "outputKey": "imageMessage"
            },
            {
              "conditions": {
                "options": {
                  "caseSensitive": true,
                  "leftValue": "",
                  "typeValidation": "strict",
                  "version": 1
                },
                "conditions": [
                  {
                    "id": "300366d9-2416-4cf4-93c3-e48c8761c60f",
                    "leftValue": "={{ $('Normaliza').item.json.message.content }}",
                    "rightValue": "",
                    "operator": {
                      "type": "string",
                      "operation": "notEmpty",
                      "singleValue": true
                    }
                  }
                ],
                "combinator": "and"
              },
              "renameOutput": true,
              "outputKey": "conversation "
            },
            {
              "conditions": {
                "options": {
                  "caseSensitive": true,
                  "leftValue": "",
                  "typeValidation": "strict",
                  "version": 1
                },
                "conditions": [
                  {
                    "id": "f33566fd-3eb9-45f4-934a-3a39e2adca6c",
                    "leftValue": "={{ $('Webhook1').item.json.body.data.messageType === 'documentMessage' }}",
                    "rightValue": true,
                    "operator": {
                      "type": "boolean",
                      "operation": "equals"
                    }
                  }
                ],
                "combinator": "and"
              },
              "renameOutput": true,
              "outputKey": "documentMessage"
            }
          ]
        },
        "options": {
          "fallbackOutput": "none"
        }
      },
      "id": "6bc0bfe8-60e7-419f-a538-aeade97f8345",
      "name": "Switch2",
      "type": "n8n-nodes-base.switch",
      "typeVersion": 3,
      "position": [
        1620,
        -80
      ]
    },
    {
      "parameters": {
        "method": "POST",
        "url": "={{ $('Normaliza').item.json.instance.Server_url }}/chat/getBase64FromMediaMessage/{{ $('Normaliza').item.json.instance.Name }}",
        "sendHeaders": true,
        "headerParameters": {
          "parameters": [
            {
              "name": "apikey",
              "value": "={{ $('Normaliza').item.json.instance.Apikey }}"
            }
          ]
        },
        "sendBody": true,
        "specifyBody": "json",
        "jsonBody": "={\n    \"message\": {\n        \"key\": {\n            \"id\":  \"{{ $('Normaliza').item.json.message.message_id }}\"\n        }\n    },\n    \"convertToMp4\": true\n} ",
        "options": {}
      },
      "id": "b5bf6064-ae12-4737-adc2-c6004ca821a9",
      "name": "Mensagem de Audio1",
      "type": "n8n-nodes-base.httpRequest",
      "typeVersion": 4.1,
      "position": [
        2180,
        -560
      ],
      "retryOnFail": true,
      "maxTries": 2
    },
    {
      "parameters": {
        "operation": "toBinary",
        "sourceProperty": "base64",
        "options": {
          "fileName": "audio",
          "mimeType": "={{ $json.mimetype }}"
        }
      },
      "id": "4be0afff-dfba-40b2-8802-33bbaeb045d3",
      "name": "Converter Áudio1",
      "type": "n8n-nodes-base.convertToFile",
      "typeVersion": 1.1,
      "position": [
        2420,
        -560
      ]
    },
    {
      "parameters": {
        "assignments": {
          "assignments": [
            {
              "id": "2f8e1fbf-9134-4b48-be29-066509e021f5",
              "name": "telefone",
              "value": "={{ $('Webhook1').item.json.body.data.key.remoteJid }}",
              "type": "string"
            },
            {
              "id": "a6004904-d9e1-4627-be79-d2a5b073d44f",
              "name": "mensagem",
              "value": "={{ $('Webhook1').item.json.body.data.message.conversation }}",
              "type": "string"
            }
          ]
        },
        "options": {}
      },
      "id": "939a0a1b-1263-457e-93c9-5da520eceb56",
      "name": "Filta Msg App1",
      "type": "n8n-nodes-base.set",
      "typeVersion": 3.4,
      "position": [
        2320,
        60
      ]
    },
    {
      "parameters": {
        "method": "POST",
        "url": "={{ $('Normaliza').item.json.instance.Server_url }}/chat/getBase64FromMediaMessage/{{ $('Normaliza').item.json.instance.Name }}",
        "sendHeaders": true,
        "headerParameters": {
          "parameters": [
            {
              "name": "apikey",
              "value": "={{ $('Normaliza').item.json.instance.Apikey }}"
            }
          ]
        },
        "sendBody": true,
        "specifyBody": "json",
        "jsonBody": "={\n    \"message\": {\n        \"key\": {\n            \"id\":  \"{{ $('Normaliza').item.json.message.message_id }}\"\n        }\n    },\n    \"convertToMp4\": true\n} ",
        "options": {}
      },
      "id": "4612e8e1-6ec9-40fc-bcb7-bfb68435b3ab",
      "name": "Envio de Imagens1",
      "type": "n8n-nodes-base.httpRequest",
      "typeVersion": 4.1,
      "position": [
        1960,
        -160
      ],
      "retryOnFail": true,
      "maxTries": 2
    },
    {
      "parameters": {
        "operation": "toBinary",
        "sourceProperty": "base64",
        "options": {
          "fileName": "image",
          "mimeType": ""
        }
      },
      "id": "6a4f251a-5629-4063-b013-2ed66ca5b9f4",
      "name": "Converter Imagem1",
      "type": "n8n-nodes-base.convertToFile",
      "typeVersion": 1.1,
      "position": [
        2200,
        -160
      ]
    },
    {
      "parameters": {
        "operation": "pdf",
        "options": {}
      },
      "id": "1293a327-a3a2-4f86-8b0b-0ed17403e4d3",
      "name": "Extrair Dados1",
      "type": "n8n-nodes-base.extractFromFile",
      "typeVersion": 1,
      "position": [
        2640,
        480
      ]
    },
    {
      "parameters": {
        "method": "POST",
        "url": "={{ $('Normaliza').item.json.instance.Server_url }}/chat/getBase64FromMediaMessage/{{ $('Normaliza').item.json.instance.Name }}",
        "sendHeaders": true,
        "headerParameters": {
          "parameters": [
            {
              "name": "apikey",
              "value": "={{ $('Normaliza').item.json.instance.Apikey }}"
            }
          ]
        },
        "sendBody": true,
        "specifyBody": "json",
        "jsonBody": "={\n    \"message\": {\n        \"key\": {\n            \"id\":  \"{{ $('Normaliza').item.json.message.message_id }}\"\n        }\n    },\n    \"convertToMp4\": true\n} ",
        "options": {}
      },
      "id": "be52bb38-22e9-4863-96fc-08d29cd93a0c",
      "name": "Envio de Documentos",
      "type": "n8n-nodes-base.httpRequest",
      "typeVersion": 4.1,
      "position": [
        2020,
        360
      ],
      "retryOnFail": true,
      "maxTries": 2
    },
    {
      "parameters": {
        "operation": "toBinary",
        "sourceProperty": "base64",
        "options": {
          "fileName": "={{ $json.fileName }}",
          "mimeType": "application/pdf"
        }
      },
      "id": "5a5c6c5c-baaf-4276-a0ef-216bacf8fd52",
      "name": "Converter Arquivo",
      "type": "n8n-nodes-base.convertToFile",
      "typeVersion": 1.1,
      "position": [
        2360,
        440
      ]
    },
    {
      "parameters": {
        "resource": "audio",
        "operation": "transcribe",
        "options": {}
      },
      "id": "b5def5e9-2b54-423e-9982-d6a4594e9228",
      "name": "OpenAI3",
      "type": "@n8n/n8n-nodes-langchain.openAi",
      "typeVersion": 1.6,
      "position": [
        2740,
        -560
      ],
      "credentials": {
        "openAiApi": {
          "id": "v5zkgrZhL2qlKUbX",
          "name": "Openai teste1"
        }
      }
    },
    {
      "parameters": {
        "resource": "image",
        "operation": "analyze",
        "modelId": {
          "__rl": true,
          "value": "gpt-4o-mini",
          "mode": "list",
          "cachedResultName": "GPT-4O-MINI"
        },
        "text": "Descreva essa imagem, oque tem nela?",
        "inputType": "base64",
        "options": {}
      },
      "id": "eb0ce9e1-e5d2-4c88-8483-e6473667d5ba",
      "name": "OpenAI1",
      "type": "@n8n/n8n-nodes-langchain.openAi",
      "typeVersion": 1.6,
      "position": [
        2380,
        -160
      ],
      "credentials": {
        "openAiApi": {
          "id": "v5zkgrZhL2qlKUbX",
          "name": "Openai teste1"
        }
      }
    },
    {
      "parameters": {
        "content": "## Extração de Texto\n**Não lê imagem mas torna mais barato o uso de tokens**\n\n",
        "height": 280,
        "width": 300,
        "color": 7
      },
      "type": "n8n-nodes-base.stickyNote",
      "typeVersion": 1,
      "position": [
        2540,
        380
      ],
      "id": "1e59f600-c817-4d97-aa6d-c6113d73c4c0",
      "name": "Sticky Note31"
    },
    {
      "parameters": {
        "assignments": {
          "assignments": [
            {
              "id": "2f2922a9-48b3-4c89-b64b-c38bb8b6d6c0",
              "name": "Mídia_Tratada",
              "value": "={{ $json.mensagem }}{{ $json.text }}{{ $json.content }}",
              "type": "string"
            },
            {
              "id": "f63d6095-aa42-4c65-96e7-8a2b4fd21d4b",
              "name": "message_Id",
              "value": "={{ $('Normaliza').item.json.message.message_id }}",
              "type": "string"
            },
            {
              "id": "1772262e-3e2d-4f1c-8a49-eb7e9a3240e6",
              "name": "Timetamp",
              "value": "={{ $('Normaliza').item.json.message.Timestamp }}",
              "type": "string"
            }
          ]
        },
        "options": {}
      },
      "type": "n8n-nodes-base.set",
      "typeVersion": 3.4,
      "position": [
        3360,
        480
      ],
      "id": "bc5b382e-fc3d-47c8-be8b-09f3a15aebcb",
      "name": "Organiza Texto1"
    },
    {
      "parameters": {
        "assignments": {
          "assignments": [
            {
              "id": "81d92796-c567-4c0b-bd7a-727fd911f9e8",
              "name": "content",
              "value": "=A imagem enviada tem o seguinte conteúdo:\n{{ $json.content }}\nA imagem contém a seguinte legenda:\n{{ $('Normaliza1').item.json.message.content }}",
              "type": "string"
            }
          ]
        },
        "options": {}
      },
      "type": "n8n-nodes-base.set",
      "typeVersion": 3.4,
      "position": [
        2720,
        -320
      ],
      "id": "c1939765-106b-4a78-b083-c2ca8965296d",
      "name": "Edit Fields1"
    },
    {
      "parameters": {
        "conditions": {
          "options": {
            "caseSensitive": true,
            "leftValue": "",
            "typeValidation": "strict",
            "version": 2
          },
          "conditions": [
            {
              "id": "54d3dfaa-2a45-4aa7-bbb5-1c3030db3ea1",
              "leftValue": "={{ $('Normaliza').item.json.message.content }}",
              "rightValue": "[empty]",
              "operator": {
                "type": "string",
                "operation": "notEmpty",
                "singleValue": true
              }
            }
          ],
          "combinator": "and"
        },
        "options": {}
      },
      "type": "n8n-nodes-base.if",
      "typeVersion": 2.2,
      "position": [
        2560,
        -160
      ],
      "id": "ec61000a-65c0-47bd-aab5-634a1d50eb6a",
      "name": "If3"
    },
    {
      "parameters": {
        "content": "",
        "height": 1476,
        "width": 2139,
        "color": 4
      },
      "id": "2ef03671-b594-46ae-9408-a09f70a33f91",
      "name": "Sticky Note5",
      "type": "n8n-nodes-base.stickyNote",
      "typeVersion": 1,
      "position": [
        3640,
        -740
      ]
    },
    {
      "parameters": {
        "content": "Buffer",
        "height": 1296,
        "width": 1979,
        "color": 3
      },
      "id": "0d13482b-f4a0-46a9-976b-c2d529108130",
      "name": "Sticky Note6",
      "type": "n8n-nodes-base.stickyNote",
      "typeVersion": 1,
      "position": [
        3720,
        -600
      ]
    },
    {
      "parameters": {
        "operation": "push",
        "list": "={{ $('Normaliza').item.json.message.chat_id }}_buf",
        "messageData": "={{ JSON.stringify({ \n    \"messageContent\": $('Organiza Texto1').item.json['Mídia_Tratada'],\n    \"messageTime\": $('Organiza Texto1').item.json.Timetamp,\n    \"messageID\": $('Organiza Texto1').item.json.message_Id,\n    \n}) }}"
      },
      "type": "n8n-nodes-base.redis",
      "typeVersion": 1,
      "position": [
        3800,
        -360
      ],
      "id": "d274b20a-d0b4-4e43-829b-670d13560a95",
      "name": "Push Buffer",
      "credentials": {
        "redis": {
          "id": "LJnIUUJF6ZcmT5jv",
          "name": "Redis teste1"
        }
      }
    },
    {
      "parameters": {
        "operation": "get",
        "propertyName": "messages",
        "key": "={{ $('Normaliza').item.json.message.chat_id }}_buf",
        "options": {}
      },
      "type": "n8n-nodes-base.redis",
      "typeVersion": 1,
      "position": [
        4000,
        -40
      ],
      "id": "86dd6525-b0c1-4512-999d-4e77160cee68",
      "name": "Redis",
      "credentials": {
        "redis": {
          "id": "LJnIUUJF6ZcmT5jv",
          "name": "Redis teste1"
        }
      }
    },
    {
      "parameters": {
        "rules": {
          "values": [
            {
              "conditions": {
                "options": {
                  "caseSensitive": true,
                  "leftValue": "",
                  "typeValidation": "strict",
                  "version": 2
                },
                "conditions": [
                  {
                    "leftValue": "={{ \n  $json.messages.length > 8 \n    ? $('Normaliza').item.json.message.messageID\n    : JSON.parse($json.messages.first()).messageID\n}}",
                    "rightValue": "={{ $('Organiza Texto1').item.json.message_Id }}",
                    "operator": {
                      "type": "string",
                      "operation": "notEquals"
                    },
                    "id": "5a97bee9-c263-49c5-8430-83a7c3c585fe"
                  }
                ],
                "combinator": "and"
              },
              "renameOutput": true,
              "outputKey": "={{true}}"
            },
            {
              "conditions": {
                "options": {
                  "caseSensitive": true,
                  "leftValue": "",
                  "typeValidation": "strict",
                  "version": 2
                },
                "conditions": [
                  {
                    "id": "fd2636bb-0129-4575-bfca-e75e013d8f99",
                    "leftValue": "={{ JSON.parse($json.messages.last()).messageTime }}",
                    "rightValue": "={{ $now.minus(3.'seconds') }}",
                    "operator": {
                      "type": "dateTime",
                      "operation": "before"
                    }
                  }
                ],
                "combinator": "and"
              },
              "renameOutput": true,
              "outputKey": "={{ true }}"
            }
          ]
        },
        "options": {
          "fallbackOutput": "extra",
          "renameFallbackOutput": "esperar"
        }
      },
      "type": "n8n-nodes-base.switch",
      "typeVersion": 3.2,
      "position": [
        4360,
        -40
      ],
      "id": "eba212e1-1925-4886-80ca-9b6e3b374077",
      "name": "Switch3"
    },
    {
      "parameters": {},
      "type": "n8n-nodes-base.noOp",
      "typeVersion": 1,
      "position": [
        5100,
        -500
      ],
      "id": "af8d2a6f-583a-4a09-a16d-d281d1feac25",
      "name": "No Operation, do nothing1"
    },
    {
      "parameters": {},
      "type": "n8n-nodes-base.wait",
      "typeVersion": 1.1,
      "position": [
        4640,
        280
      ],
      "id": "84ccb3e5-3449-42b5-9e85-22d79647ace4",
      "name": "Wait",
      "webhookId": "05ea8059-bcce-4cd7-9d0e-faa8e9f9fe09"
    },
    {
      "parameters": {
        "operation": "delete",
        "key": "={{ $('Normaliza').item.json.message.chat_id.toString() }}_buf"
      },
      "type": "n8n-nodes-base.redis",
      "typeVersion": 1,
      "position": [
        5120,
        -40
      ],
      "id": "a0263242-c310-4692-9566-35a2e80d1474",
      "name": "Redis1",
      "credentials": {
        "redis": {
          "id": "LJnIUUJF6ZcmT5jv",
          "name": "Redis teste1"
        }
      }
    },
    {
      "parameters": {
        "assignments": {
          "assignments": [
            {
              "id": "db5cfe0a-7f43-4a61-8b27-bfd3a95deb8d",
              "name": "messages",
              "value": "={{ $json.messages.map(msg => JSON.parse(msg)).sort((a, b) => new Date(a.messageTime) - new Date(b.messageTime)).map(msg => msg.messageContent).join(' ') }}\n",
              "type": "string"
            }
          ]
        },
        "options": {}
      },
      "id": "189f876a-07cf-4d9e-a9ab-baf76316a3bf",
      "name": "Remonta Input",
      "type": "n8n-nodes-base.set",
      "typeVersion": 3.4,
      "position": [
        5440,
        -40
      ]
    },
    {
      "parameters": {
        "jsCode": "function limparMensagem(texto) {\n  if (typeof texto !== 'string') {\n    return '';\n  }\n\n  // Função para remover metadados e dados técnicos\n  function removerMetadataTecnico(str) {\n    return str\n      // Remove objetos e chaves de metadados específicos\n      .replace(/\"response_metadata\"\\s*:\\s*{[^}]*}/g, '')  // Remove \"response_metadata\"\n      .replace(/\"additional_kwargs\"\\s*:\\s*{[^}]*}/g, '')  // Remove \"additional_kwargs\"\n      .replace(/\"tool_calls\"\\s*:\\s*\\[\\s*\\]/g, '')  // Remove \"tool_calls\" vazio\n      .replace(/\"invalid_tool_calls\"\\s*:\\s*\\[\\s*\\]/g, '')  // Remove \"invalid_tool_calls\" vazio\n      .replace(/\"type\"\\s*:\\s*\"(ai|human)\"/g, '')  // Remove os tipos \"ai\" e \"human\"\n      .replace(/\"data\"\\s*:\\s*{[^}]*}/g, '')  // Remove a chave \"data\"\n      // Remove objetos JSON em excesso ou vazios\n      .replace(/,\\s*{[^}]*}/g, '') // Remove objetos soltos\n      .replace(/,\\s*\\[\\s*\\]/g, '') // Remove arrays vazios\n      .replace(/\\s*:\\s*null/g, '') // Remove valores null\n      .replace(/\\s*:\\s*\\[\\]/g, '') // Remove arrays vazios\n      .replace(/\\s*:\\s*{}/g, '') // Remove objetos vazios\n      // Ajusta espaços desnecessários\n      .replace(/\\s+/g, ' ')\n      .replace(/^\\s+|\\s+$/g, '');  // Remove espaços no início e fim\n  }\n\n  // Função para limpar caracteres especiais\n  function limparCaracteresEspeciais(str) {\n    return str\n      .replace(/\\\\\\\\[rnt]/g, ' ')  // Limpa sequências de escape\n      .replace(/\\\\\\\\\\\"/g, '')  // Remove as aspas escapadas\n      .replace(/\\\\\\\\\\\\\\\\/g, '')  // Remove barras invertidas\n      .replace(/[\\x00-\\x1F\\x7F-\\x9F]/g, '')  // Remove caracteres de controle\n      .replace(/\\\"+/g, '')  // Remove aspas extras\n      .replace(/[{}[\\]]/g, '')  // Remove chaves e colchetes extras\n      .trim();\n  }\n\n  // Função para extrair e limpar a mensagem principal\n  function extrairMensagemPrincipal(str) {\n    // Divide em frases, removendo pontuação extra\n    const frases = str.split(/(?<=[.!?])\\s+/);\n\n    return frases\n      .map(frase => frase.trim())\n      .filter(frase => {\n        // Remove frases que ainda têm metadados ou são irrelevantes\n        return frase.length > 0 &&\n          !frase.includes('tool_calls') &&\n          !frase.includes('invalid_tool_calls') &&\n          !frase.match(/^[:\\s\\[\\]{}]+$/);\n      })\n      .join(' ');\n  }\n\n  // Processo de limpeza e extração\n  let resultado = texto;\n\n  // Passo 1: Remove metadados e chaves indesejadas\n  resultado = removerMetadataTecnico(resultado);\n\n  // Passo 2: Extrai a mensagem relevante, ignorando o que não é necessário\n  resultado = extrairMensagemPrincipal(resultado);\n\n  // Passo 3: Remove caracteres especiais e formatação indesejada\n  resultado = limparCaracteresEspeciais(resultado);\n\n  // Limpeza final para remover espaços extras\n  resultado = resultado\n    .replace(/\\s+/g, ' ')\n    .replace(/^[\\\",\\s]+|[\\\",\\s]+$/g, '')\n    .trim();\n\n  return resultado;\n}\n\nfunction processarMensagens(items) {\n  return items.map(item => {\n    try {\n      if (!item?.json?.mensagem) {\n        return item;\n      }\n\n      let mensagem = item.json.mensagem;\n\n      // Se for objeto, converte para string\n      if (typeof mensagem === 'object') {\n        try {\n          mensagem = JSON.stringify(mensagem);\n        } catch (e) {\n          console.error('Erro ao converter objeto para string:', e);\n          return item;\n        }\n      }\n\n      // Aplica a limpeza\n      const mensagemLimpa = limparMensagem(mensagem);\n\n      // Atualiza apenas se houver conteúdo significativo\n      if (mensagemLimpa && mensagemLimpa.length > 0) {\n        item.json.mensagem = mensagemLimpa;\n      }\n\n      return { json: item.json };\n    } catch (error) {\n      console.error('Erro ao processar item:', error);\n      return item;\n    }\n  });\n}\n\n// Execução principal\ntry {\n  const items = $input.all();\n  return processarMensagens(items);\n} catch (error) {\n  console.error('Erro na execução:', error);\n  throw error;\n}\n"
      },
      "id": "18edd61b-ca33-4734-a6b1-683bf576e3d1",
      "name": "Code",
      "type": "n8n-nodes-base.code",
      "typeVersion": 2,
      "position": [
        5880,
        -660
      ]
    },
    {
      "parameters": {
        "content": "",
        "height": 256,
        "width": 2159,
        "color": 3
      },
      "id": "ac9669c0-ea90-415b-8e4c-0978dc070b5a",
      "name": "Sticky Note7",
      "type": "n8n-nodes-base.stickyNote",
      "typeVersion": 1,
      "position": [
        5800,
        -740
      ]
    },
    {
      "parameters": {
        "assignments": {
          "assignments": [
            {
              "id": "efde61c9-1d5d-416a-8fc3-ae28d21fa94e",
              "name": "=output",
              "value": "={{ $json.output.split('\\n\\n') }}",
              "type": "array"
            }
          ]
        },
        "options": {}
      },
      "type": "n8n-nodes-base.set",
      "typeVersion": 3.4,
      "position": [
        6880,
        -660
      ],
      "id": "30860a24-624e-4dad-bcf1-90b848816766",
      "name": "Edit Fields5"
    },
    {
      "parameters": {
        "fieldToSplitOut": "output",
        "options": {}
      },
      "type": "n8n-nodes-base.splitOut",
      "typeVersion": 1,
      "position": [
        7680,
        -660
      ],
      "id": "d2dc81a5-3c2e-488d-946b-2952ffc3aa7a",
      "name": "Split Out"
    },
    {
      "parameters": {
        "options": {}
      },
      "type": "n8n-nodes-base.splitInBatches",
      "typeVersion": 3,
      "position": [
        7100,
        100
      ],
      "id": "5ab52976-a722-4add-afdc-d61d186c9471",
      "name": "Loop Over Items"
    },
    {
      "parameters": {},
      "type": "n8n-nodes-base.noOp",
      "name": "Replace Me",
      "typeVersion": 1,
      "position": [
        7640,
        -380
      ],
      "id": "9de67ba9-cd4c-456f-8ea2-e70af6c232fb"
    },
    {
      "parameters": {
        "content": "",
        "height": 1196,
        "width": 1199
      },
      "id": "6bcc5d6e-f7a0-4965-bac8-7736baede4a5",
      "name": "Sticky Note8",
      "type": "n8n-nodes-base.stickyNote",
      "typeVersion": 1,
      "position": [
        5800,
        -460
      ]
    },
    {
      "parameters": {
        "content": "",
        "height": 1196,
        "width": 959,
        "color": 5
      },
      "id": "0351b5c3-d6c5-422e-ac05-5a05ef48736e",
      "name": "Sticky Note9",
      "type": "n8n-nodes-base.stickyNote",
      "typeVersion": 1,
      "position": [
        7020,
        -460
      ]
    },
    {
      "parameters": {
        "amount": 4
      },
      "type": "n8n-nodes-base.wait",
      "typeVersion": 1.1,
      "position": [
        7780,
        360
      ],
      "id": "ec3c5424-4f59-4fca-93b5-f6d5ac312d77",
      "name": "Digitando",
      "webhookId": "449d8ae9-3347-4689-8dfb-66e98a8ad8ad"
    },
    {
      "parameters": {
        "model": {
          "__rl": true,
          "mode": "list",
          "value": "gpt-4.1-mini"
        },
        "options": {}
      },
      "type": "@n8n/n8n-nodes-langchain.lmChatOpenAi",
      "typeVersion": 1.2,
      "position": [
        5840,
        -340
      ],
      "id": "49e3c66d-49ae-4193-b552-f86862a4ced4",
      "name": "OpenAI Chat Model1",
      "credentials": {
        "openAiApi": {
          "id": "v5zkgrZhL2qlKUbX",
          "name": "Openai teste1"
        }
      }
    },
    {
      "parameters": {
        "sessionIdType": "customKey",
        "sessionKey": "={{ $('Normaliza').item.json.message.chat_id }}_mem",
        "sessionTTL": 10000
      },
      "type": "@n8n/n8n-nodes-langchain.memoryRedisChat",
      "typeVersion": 1.5,
      "position": [
        6060,
        -340
      ],
      "id": "8f1ac0bf-7aa7-43b0-8031-f22ee4e6d3b7",
      "name": "Redis Chat Memory1",
      "credentials": {
        "redis": {
          "id": "LJnIUUJF6ZcmT5jv",
          "name": "Redis teste1"
        }
      }
    },
    {
      "parameters": {},
      "type": "@n8n/n8n-nodes-langchain.toolCalculator",
      "typeVersion": 1,
      "position": [
        6340,
        -400
      ],
      "id": "96035162-0764-4018-98f7-763eac7d193f",
      "name": "Calculator"
    },
    {
      "parameters": {
        "content": "",
        "height": 1116,
        "width": 659,
        "color": 6
      },
      "id": "5696a200-95d2-4b4b-b742-8488fcf9af01",
      "name": "Sticky Note10",
      "type": "n8n-nodes-base.stickyNote",
      "typeVersion": 1,
      "position": [
        6320,
        -440
      ]
    },
    {
      "parameters": {
        "options": {}
      },
      "type": "n8n-nodes-base.dateTimeTool",
      "typeVersion": 2,
      "position": [
        6460,
        -400
      ],
      "id": "75a9626a-7c73-40a4-9959-d6b3c339aa3f",
      "name": "Date & Time"
    },
    {
      "parameters": {},
      "type": "n8n-nodes-base.manualTrigger",
      "typeVersion": 1,
      "position": [
        5480,
        5400
      ],
      "id": "5ce4e4d8-370f-4c33-9466-cf30311ff36e",
      "name": "When clicking ‘Execute workflow’",
      "disabled": true
    },
    {
      "parameters": {
        "options": {}
      },
      "id": "416ea766-c81f-474f-af2c-66e2802a2313",
      "name": "Chat Memory Delete",
      "type": "@n8n/n8n-nodes-langchain.memoryManager",
      "typeVersion": 1.1,
      "position": [
        5960,
        5400
      ],
      "disabled": true
    },
    {
      "parameters": {
        "mode": "delete"
      },
      "id": "b0127e9c-05da-4930-80d7-9afaf56a4bac",
      "name": "Chat Memory Delete1",
      "type": "@n8n/n8n-nodes-langchain.memoryManager",
      "typeVersion": 1.1,
      "position": [
        6180,
        5660
      ],
      "disabled": true
    },
    {
      "parameters": {
        "sessionIdType": "customKey",
        "sessionKey": "=553198472741_mem",
        "sessionTTL": 10000
      },
      "type": "@n8n/n8n-nodes-langchain.memoryRedisChat",
      "typeVersion": 1.5,
      "position": [
        5800,
        5660
      ],
      "id": "f95f1854-41f1-4c4e-97d8-9bd4a2e88a24",
      "name": "Redis Chat Memory",
      "credentials": {
        "redis": {
          "id": "LJnIUUJF6ZcmT5jv",
          "name": "Redis teste1"
        }
      }
    },
    {
      "parameters": {
        "descriptionType": "manual",
        "toolDescription": "Acione essa ferramenta quando essas cinco condições estiverem alcançadas: \n\n1) foi verificada que existe disponibilidade para a data que o cliente pediu.\n2) o cliente confirmou que quer marcar uma aula experimental ou fechar um pacote com o personal.\n\n3) O cliente informou o EMAIL da agenda dele",
        "calendar": {
          "__rl": true,
          "value": "rodrigueseduardo6192@gmail.com",
          "mode": "list",
          "cachedResultName": "rodrigueseduardo6192@gmail.com"
        },
        "start": "={{ $fromAI(\"Start_Time\", \"horário que vai iniciar a consulta ou procedimento ex.:2024-10-08 00:00:00\", \"string\" ) }}",
        "end": "={{ $fromAI(\"Final_Time\", \"horário que vai iniciar a consulta ou procedimento ex.:2024-10-08 01:00:00\", \"string\" ) }}",
        "additionalFields": {
          "summary": "={{ $json.aula_experimental === \"sim\" ? \"[Aula Experimental]\" : \"[Aula]\" }}\n \n Cliente #{{ $('Normaliza').item.json.message.chat_id }}"
        }
      },
      "type": "n8n-nodes-base.googleCalendarTool",
      "typeVersion": 1.3,
      "position": [
        6340,
        -240
      ],
      "id": "423ba4ec-1495-4eb9-9261-1e2302e97d54",
      "name": "CriarConsulta1",
      "credentials": {
        "googleCalendarOAuth2Api": {
          "id": "zqxw8NlhWkHviDP1",
          "name": "Google Calendar teste1"
        }
      },
      "disabled": true
    },
    {
      "parameters": {
        "descriptionType": "manual",
        "toolDescription": "Essa ferramenta deverá ser acionada quando não houver disponibilidade no dia que o cliente pediu. Retorne 3 horários livres no mesmo dia que o cliente pediu o agendamento.",
        "operation": "getAll",
        "calendar": {
          "__rl": true,
          "value": "rodrigueseduardo6192@gmail.com",
          "mode": "list",
          "cachedResultName": "rodrigueseduardo6192@gmail.com"
        },
        "limit": 12,
        "timeMin": "={{ $fromAI(\"Initital_DateTime\", \"Data e hora inicial da consulta Ex.: 2024-10-17 -04:00:00\") }}",
        "timeMax": "={{ $fromAI(\"Final_DateTime\", \"Data e hora final da consulta Ex.: 2024-10-17 04:00:00\") }}",
        "options": {}
      },
      "type": "n8n-nodes-base.googleCalendarTool",
      "typeVersion": 1.3,
      "position": [
        6480,
        -240
      ],
      "id": "b203d085-d817-42f8-ae78-beb1eda3c2d3",
      "name": "Vagas",
      "credentials": {
        "googleCalendarOAuth2Api": {
          "id": "zqxw8NlhWkHviDP1",
          "name": "Google Calendar teste1"
        }
      },
      "disabled": true
    },
    {
      "parameters": {
        "descriptionType": "manual",
        "toolDescription": "Antes de marcar uma aula experimental ou fechar um pacote acione essa ferramenta primeiro para ter certeza que existe disponibilidade.",
        "resource": "calendar",
        "calendar": {
          "__rl": true,
          "value": "rodrigueseduardo6192@gmail.com",
          "mode": "list",
          "cachedResultName": "rodrigueseduardo6192@gmail.com"
        },
        "timeMin": "={{ $fromAI(\"Initital_DateTime\", \"Data e hora inicial da consulta Ex.: 2024-10-17 00:00:00\") }}",
        "timeMax": "={{ $fromAI(\"Final_DateTime\", \"Data e hora final da consulta Ex.: 2024-10-17 01:00:00\") }}",
        "options": {}
      },
      "type": "n8n-nodes-base.googleCalendarTool",
      "typeVersion": 1.3,
      "position": [
        6340,
        -60
      ],
      "id": "7087f1b0-7f02-4f04-abff-c2fa7d614455",
      "name": "Disponibilidade",
      "credentials": {
        "googleCalendarOAuth2Api": {
          "id": "zqxw8NlhWkHviDP1",
          "name": "Google Calendar teste1"
        }
      },
      "disabled": true
    },
    {
      "parameters": {
        "operation": "delete",
        "calendar": {
          "__rl": true,
          "value": "rodrigueseduardo6192@gmail.com",
          "mode": "list",
          "cachedResultName": "rodrigueseduardo6192@gmail.com"
        },
        "eventId": "={{ $fromAI(\"protocolo\", \"O protocolo é o {Event_ID} aula experimental ou pacote a ser deletado ou cancelado\", \"string\") }}",
        "options": {}
      },
      "type": "n8n-nodes-base.googleCalendarTool",
      "typeVersion": 1.3,
      "position": [
        6480,
        -60
      ],
      "id": "2da8cff7-a1a3-4ba9-b1dc-c88117d63c99",
      "name": "DeletarConsulta",
      "credentials": {
        "googleCalendarOAuth2Api": {
          "id": "zqxw8NlhWkHviDP1",
          "name": "Google Calendar teste1"
        }
      },
      "disabled": true
    },
    {
      "parameters": {
        "descriptionType": "manual",
        "toolDescription": "Acione essa ferramenta quando criar uma consulta e informe: \"Seu {nome_do_intuito}, {dia_mês_ano}, {horário_marcado} e o {Event_ID}”",
        "tableId": "Consulta",
        "fieldsUi": {
          "fieldValues": [
            {
              "fieldId": "userID",
              "fieldValue": "={{ $('Normaliza').item.json.message.chat_id }}"
            },
            {
              "fieldId": "Protocolo",
              "fieldValue": "={{ $fromAI(\"protocolo\", \"é o Event_ID\", \"string\") }}"
            },
            {
              "fieldId": "Horário",
              "fieldValue": "={{ $fromAI(\"Start\", \"data e horário do intuito no formato ex.:2024-10-08 01:0:00\") }}"
            },
            {
              "fieldId": "Intuito",
              "fieldValue": "={{ $fromAI(\"nome_do_intuito\", \"é o nome do intuito que o cliente vai realizar\") }}"
            }
          ]
        }
      },
      "type": "n8n-nodes-base.supabaseTool",
      "typeVersion": 1,
      "position": [
        6620,
        -400
      ],
      "id": "0f506067-337d-4aa6-83c2-e22480dd0f24",
      "name": "Anotar",
      "credentials": {
        "supabaseApi": {
          "id": "6Xrjq6SUm4AsPrEM",
          "name": "Supabase MM"
        }
      },
      "disabled": true
    },
    {
      "parameters": {
        "descriptionType": "manual",
        "toolDescription": "Quando o cliente não lembrar do protocolo da consulta acione essa ferramenta e busque todos eventos agendados.",
        "operation": "getAll",
        "tableId": "Consulta",
        "limit": 10,
        "filters": {
          "conditions": [
            {
              "keyName": "userID",
              "condition": "eq",
              "keyValue": "={{ $('Normaliza').item.json.message.chat_id }}"
            }
          ]
        }
      },
      "type": "n8n-nodes-base.supabaseTool",
      "typeVersion": 1,
      "position": [
        6760,
        -400
      ],
      "id": "843dcc83-a5b7-4788-95c0-e9902d5ce9a7",
      "name": "Buscar",
      "credentials": {
        "supabaseApi": {
          "id": "6Xrjq6SUm4AsPrEM",
          "name": "Supabase MM"
        }
      },
      "disabled": true
    },
    {
      "parameters": {
        "descriptionType": "manual",
        "toolDescription": " Quando qualquer evento for cancelado ou deletado acione essa ferramenta informando o protocolo do evento.",
        "operation": "delete",
        "tableId": "Consulta",
        "matchType": "allFilters",
        "filters": {
          "conditions": [
            {
              "keyName": "userID",
              "condition": "eq",
              "keyValue": "={{ $('Normaliza').item.json.message.chat_id }}"
            },
            {
              "keyName": "Protocolo",
              "condition": "eq",
              "keyValue": "={{ $fromAI(\"Event_ID\", \"O protocolo único da visita a escola  ou matricula a ser deletado ou cancelado\", \"string\") }}"
            }
          ]
        }
      },
      "type": "n8n-nodes-base.supabaseTool",
      "typeVersion": 1,
      "position": [
        6620,
        -240
      ],
      "id": "704f0d89-7dd4-43f3-8075-84de5b85ef7a",
      "name": "Deletar",
      "credentials": {
        "supabaseApi": {
          "id": "6Xrjq6SUm4AsPrEM",
          "name": "Supabase MM"
        }
      },
      "disabled": true
    },
    {
      "parameters": {
        "descriptionType": "manual",
        "toolDescription": "Acione está ferramenta quando o cliente estiver interessado nos valores dos procedimentos.\n",
        "documentId": {
          "__rl": true,
          "value": "1FWJv3JenMKpHTOE5Pq687qsw3--iYFhcQIAGKY6DmBI",
          "mode": "list",
          "cachedResultName": "Planilha sem título",
          "cachedResultUrl": "https://docs.google.com/spreadsheets/d/1FWJv3JenMKpHTOE5Pq687qsw3--iYFhcQIAGKY6DmBI/edit?usp=drivesdk"
        },
        "sheetName": {
          "__rl": true,
          "value": "gid=0",
          "mode": "list",
          "cachedResultName": "Página1",
          "cachedResultUrl": "https://docs.google.com/spreadsheets/d/1FWJv3JenMKpHTOE5Pq687qsw3--iYFhcQIAGKY6DmBI/edit#gid=0"
        },
        "options": {}
      },
      "type": "n8n-nodes-base.googleSheetsTool",
      "typeVersion": 4.6,
      "position": [
        6760,
        -240
      ],
      "id": "4bb8d46d-ee67-4e98-bb3e-0641e03591fd",
      "name": "Tabela de Valores",
      "credentials": {
        "googleSheetsOAuth2Api": {
          "id": "jjsvZX9LvUIcsvFq",
          "name": "Google Sheets Teste MM"
        }
      }
    },
    {
      "parameters": {
        "descriptionType": "manual",
        "toolDescription": "Quando tiver a confirmação da confirmação e do pagamento do cliente acione essa ferramenta para criar um banco de informação.",
        "operation": "append",
        "documentId": {
          "__rl": true,
          "value": "14qJLF-iQCnVMgLnyRnFja84JBTnviMc9GX_cq5QWutA",
          "mode": "list",
          "cachedResultName": "Status dos Alunos",
          "cachedResultUrl": "https://docs.google.com/spreadsheets/d/14qJLF-iQCnVMgLnyRnFja84JBTnviMc9GX_cq5QWutA/edit?usp=drivesdk"
        },
        "sheetName": {
          "__rl": true,
          "value": "gid=0",
          "mode": "list",
          "cachedResultName": "Página1",
          "cachedResultUrl": "https://docs.google.com/spreadsheets/d/14qJLF-iQCnVMgLnyRnFja84JBTnviMc9GX_cq5QWutA/edit#gid=0"
        },
        "columns": {
          "mappingMode": "defineBelow",
          "value": {
            "Nome": "={{ $fromAI(\"nome_cliente\", \"nome do cliente\", \"string\") }}",
            "Telefone": "={{ $('Normaliza').item.json.message.chat_id }}",
            "Status": "={{ $fromAI(\n    \"status\",\n    \"Retorne o status do pacote. Se o pacote ainda estiver dentro do prazo, responda exatamente 'em dia'. Se o pacote estiver vencido, responda exatamente 'atrasado'.\",\n    \"string\",\n    \"em dia\"\n) }}\n\n",
            "Servico": "={{ $fromAI(\n  \"Servico\",\n  \"Identifique o tipo de serviço do cliente e retorne exatamente 'mensal', 'semestral' ou 'anual'.\",\n  \"string\"\n) }}\n"
          },
          "matchingColumns": [],
          "schema": [
            {
              "id": "Nome",
              "displayName": "Nome",
              "required": false,
              "defaultMatch": false,
              "display": true,
              "type": "string",
              "canBeUsedToMatch": true
            },
            {
              "id": "Telefone",
              "displayName": "Telefone",
              "required": false,
              "defaultMatch": false,
              "display": true,
              "type": "string",
              "canBeUsedToMatch": true
            },
            {
              "id": "Servico",
              "displayName": "Servico",
              "required": false,
              "defaultMatch": false,
              "display": true,
              "type": "string",
              "canBeUsedToMatch": true,
              "removed": false
            },
            {
              "id": "Status",
              "displayName": "Status",
              "required": false,
              "defaultMatch": false,
              "display": true,
              "type": "string",
              "canBeUsedToMatch": true
            }
          ],
          "attemptToConvertTypes": false,
          "convertFieldsToString": false
        },
        "options": {}
      },
      "type": "n8n-nodes-base.googleSheetsTool",
      "typeVersion": 4.6,
      "position": [
        6880,
        -400
      ],
      "id": "4183b571-61e1-46e5-bc28-f288e369f7c0",
      "name": "Anotar1",
      "credentials": {
        "googleSheetsOAuth2Api": {
          "id": "jjsvZX9LvUIcsvFq",
          "name": "Google Sheets Teste MM"
        }
      }
    },
    {
      "parameters": {
        "descriptionType": "manual",
        "toolDescription": "O número do telefone do cliente é {{ $('Normaliza').item.json.message.chat_id }} , Quando um cliente quiser consultar sobre as informações do seu pacote acione essa ferramenta.",
        "documentId": {
          "__rl": true,
          "value": "14qJLF-iQCnVMgLnyRnFja84JBTnviMc9GX_cq5QWutA",
          "mode": "list",
          "cachedResultName": "Status dos Alunos",
          "cachedResultUrl": "https://docs.google.com/spreadsheets/d/14qJLF-iQCnVMgLnyRnFja84JBTnviMc9GX_cq5QWutA/edit?usp=drivesdk"
        },
        "sheetName": {
          "__rl": true,
          "value": "gid=0",
          "mode": "list",
          "cachedResultName": "Página1",
          "cachedResultUrl": "https://docs.google.com/spreadsheets/d/14qJLF-iQCnVMgLnyRnFja84JBTnviMc9GX_cq5QWutA/edit#gid=0"
        },
        "filtersUI": {
          "values": [
            {
              "lookupColumn": "Telefone",
              "lookupValue": "={{ $('Normaliza').item.json.message.chat_id }}"
            },
            {
              "lookupColumn": "Status",
              "lookupValue": "em dia ou atrasado"
            }
          ]
        },
        "options": {}
      },
      "type": "n8n-nodes-base.googleSheetsTool",
      "typeVersion": 4.6,
      "position": [
        6880,
        -240
      ],
      "id": "81535ba5-3013-4818-acf4-d390f2065565",
      "name": "Buscar1",
      "credentials": {
        "googleSheetsOAuth2Api": {
          "id": "jjsvZX9LvUIcsvFq",
          "name": "Google Sheets Teste MM"
        }
      }
    }
  ],
  "pinData": {},
  "connections": {
    "AI Agent1": {
      "main": [
        [
          {
            "node": "Edit Fields5",
            "type": "main",
            "index": 0
          }
        ]
      ]
    },
    "Normaliza": {
      "main": [
        [
          {
            "node": "Switch",
            "type": "main",
            "index": 0
          }
        ]
      ]
    },
    "Webhook1": {
      "main": [
        [
          {
            "node": "Normaliza",
            "type": "main",
            "index": 0
          }
        ]
      ]
    },
    "Switch": {
      "main": [
        [
          {
            "node": "Gera Timeout",
            "type": "main",
            "index": 0
          }
        ],
        [
          {
            "node": "Get block",
            "type": "main",
            "index": 0
          }
        ]
      ]
    },
    "Get block": {
      "main": [
        [
          {
            "node": "Switch1",
            "type": "main",
            "index": 0
          }
        ]
      ]
    },
    "Switch1": {
      "main": [
        [
          {
            "node": "Switch2",
            "type": "main",
            "index": 0
          }
        ],
        [
          {
            "node": "No Operation, do nothing",
            "type": "main",
            "index": 0
          }
        ]
      ]
    },
    "Mensagem de Audio1": {
      "main": [
        [
          {
            "node": "Converter Áudio1",
            "type": "main",
            "index": 0
          }
        ]
      ]
    },
    "Converter Áudio1": {
      "main": [
        [
          {
            "node": "OpenAI3",
            "type": "main",
            "index": 0
          }
        ]
      ]
    },
    "Filta Msg App1": {
      "main": [
        [
          {
            "node": "Organiza Texto1",
            "type": "main",
            "index": 0
          }
        ]
      ]
    },
    "Envio de Imagens1": {
      "main": [
        [
          {
            "node": "Converter Imagem1",
            "type": "main",
            "index": 0
          }
        ]
      ]
    },
    "Converter Imagem1": {
      "main": [
        [
          {
            "node": "OpenAI1",
            "type": "main",
            "index": 0
          }
        ]
      ]
    },
    "Extrair Dados1": {
      "main": [
        [
          {
            "node": "Organiza Texto1",
            "type": "main",
            "index": 0
          }
        ]
      ]
    },
    "Envio de Documentos": {
      "main": [
        [
          {
            "node": "Converter Arquivo",
            "type": "main",
            "index": 0
          }
        ]
      ]
    },
    "Converter Arquivo": {
      "main": [
        [
          {
            "node": "Extrair Dados1",
            "type": "main",
            "index": 0
          }
        ]
      ]
    },
    "OpenAI3": {
      "main": [
        [
          {
            "node": "Organiza Texto1",
            "type": "main",
            "index": 0
          }
        ]
      ]
    },
    "OpenAI1": {
      "main": [
        [
          {
            "node": "If3",
            "type": "main",
            "index": 0
          }
        ]
      ]
    },
    "Edit Fields1": {
      "main": [
        [
          {
            "node": "Organiza Texto1",
            "type": "main",
            "index": 0
          }
        ]
      ]
    },
    "If3": {
      "main": [
        [
          {
            "node": "Edit Fields1",
            "type": "main",
            "index": 0
          }
        ],
        [
          {
            "node": "Organiza Texto1",
            "type": "main",
            "index": 0
          }
        ]
      ]
    },
    "Switch2": {
      "main": [
        [
          {
            "node": "Mensagem de Audio1",
            "type": "main",
            "index": 0
          }
        ],
        [
          {
            "node": "Envio de Imagens1",
            "type": "main",
            "index": 0
          }
        ],
        [
          {
            "node": "Filta Msg App1",
            "type": "main",
            "index": 0
          }
        ],
        [
          {
            "node": "Envio de Documentos",
            "type": "main",
            "index": 0
          }
        ]
      ]
    },
    "Organiza Texto1": {
      "main": [
        [
          {
            "node": "Push Buffer",
            "type": "main",
            "index": 0
          }
        ]
      ]
    },
    "Push Buffer": {
      "main": [
        [
          {
            "node": "Redis",
            "type": "main",
            "index": 0
          }
        ]
      ]
    },
    "Redis": {
      "main": [
        [
          {
            "node": "Switch3",
            "type": "main",
            "index": 0
          }
        ]
      ]
    },
    "Switch3": {
      "main": [
        [
          {
            "node": "No Operation, do nothing1",
            "type": "main",
            "index": 0
          }
        ],
        [
          {
            "node": "Redis1",
            "type": "main",
            "index": 0
          }
        ],
        [
          {
            "node": "Wait",
            "type": "main",
            "index": 0
          }
        ]
      ]
    },
    "Wait": {
      "main": [
        [
          {
            "node": "Redis",
            "type": "main",
            "index": 0
          }
        ]
      ]
    },
    "Redis1": {
      "main": [
        [
          {
            "node": "Remonta Input",
            "type": "main",
            "index": 0
          }
        ]
      ]
    },
    "Remonta Input": {
      "main": [
        [
          {
            "node": "Code",
            "type": "main",
            "index": 0
          }
        ]
      ]
    },
    "Code": {
      "main": [
        [
          {
            "node": "AI Agent1",
            "type": "main",
            "index": 0
          }
        ]
      ]
    },
    "Edit Fields5": {
      "main": [
        [
          {
            "node": "Split Out",
            "type": "main",
            "index": 0
          }
        ]
      ]
    },
    "Split Out": {
      "main": [
        [
          {
            "node": "Loop Over Items",
            "type": "main",
            "index": 0
          }
        ]
      ]
    },
    "Loop Over Items": {
      "main": [
        [
          {
            "node": "Replace Me",
            "type": "main",
            "index": 0
          }
        ],
        [
          {
            "node": "Enviar Mensagem Whatsaap",
            "type": "main",
            "index": 0
          }
        ]
      ]
    },
    "Replace Me": {
      "main": [
        []
      ]
    },
    "Enviar Mensagem Whatsaap": {
      "main": [
        [
          {
            "node": "Digitando",
            "type": "main",
            "index": 0
          }
        ]
      ]
    },
    "Digitando": {
      "main": [
        [
          {
            "node": "Loop Over Items",
            "type": "main",
            "index": 0
          }
        ]
      ]
    },
    "OpenAI Chat Model1": {
      "ai_languageModel": [
        [
          {
            "node": "AI Agent1",
            "type": "ai_languageModel",
            "index": 0
          }
        ]
      ]
    },
    "Redis Chat Memory1": {
      "ai_memory": [
        [
          {
            "node": "AI Agent1",
            "type": "ai_memory",
            "index": 0
          }
        ]
      ]
    },
    "Calculator": {
      "ai_tool": [
        [
          {
            "node": "AI Agent1",
            "type": "ai_tool",
            "index": 0
          }
        ]
      ]
    },
    "Date & Time": {
      "ai_tool": [
        [
          {
            "node": "AI Agent1",
            "type": "ai_tool",
            "index": 0
          }
        ]
      ]
    },
    "When clicking ‘Execute workflow’": {
      "main": [
        [
          {
            "node": "Chat Memory Delete1",
            "type": "main",
            "index": 0
          }
        ]
      ]
    },
    "Redis Chat Memory": {
      "ai_memory": [
        [
          {
            "node": "Chat Memory Delete1",
            "type": "ai_memory",
            "index": 0
          }
        ]
      ]
    },
    "Chat Memory Delete": {
      "main": [
        []
      ]
    },
    "CriarConsulta1": {
      "ai_tool": [
        [
          {
            "node": "AI Agent1",
            "type": "ai_tool",
            "index": 0
          }
        ]
      ]
    },
    "Vagas": {
      "ai_tool": [
        [
          {
            "node": "AI Agent1",
            "type": "ai_tool",
            "index": 0
          }
        ]
      ]
    },
    "Disponibilidade": {
      "ai_tool": [
        [
          {
            "node": "AI Agent1",
            "type": "ai_tool",
            "index": 0
          }
        ]
      ]
    },
    "DeletarConsulta": {
      "ai_tool": [
        [
          {
            "node": "AI Agent1",
            "type": "ai_tool",
            "index": 0
          }
        ]
      ]
    },
    "Anotar": {
      "ai_tool": [
        [
          {
            "node": "AI Agent1",
            "type": "ai_tool",
            "index": 0
          }
        ]
      ]
    },
    "Buscar": {
      "ai_tool": [
        [
          {
            "node": "AI Agent1",
            "type": "ai_tool",
            "index": 0
          }
        ]
      ]
    },
    "Deletar": {
      "ai_tool": [
        [
          {
            "node": "AI Agent1",
            "type": "ai_tool",
            "index": 0
          }
        ]
      ]
    },
    "Tabela de Valores": {
      "ai_tool": [
        [
          {
            "node": "AI Agent1",
            "type": "ai_tool",
            "index": 0
          }
        ]
      ]
    },
    "Anotar1": {
      "ai_tool": [
        [
          {
            "node": "AI Agent1",
            "type": "ai_tool",
            "index": 0
          }
        ]
      ]
    },
    "Buscar1": {
      "ai_tool": [
        [
          {
            "node": "AI Agent1",
            "type": "ai_tool",
            "index": 0
          }
        ]
      ]
    }
  },
  "active": false,
  "settings": {
    "executionOrder": "v1"
  },
  "versionId": "19ef8d6d-bd67-4d27-88fa-b4b17ff4eb87",
  "meta": {
    "templateCredsSetupCompleted": true,
    "instanceId": "71462a5924886888de022a8b5698639599a969bc07f1d65f5d067c0ea19b766d"
  },
  "id": "YBSnShM7IuYsNMzD",
  "tags": []
}


   Sobre Feedbacks:

   * Por favor dê seu feedback sobre o Agente de IA !
   * Diga os pontos negativos e positivos em sua visão .
   * E principalmente em que posso melhorar.


Desde já Agradeço!!
