{
  "updatedAt": "2025-12-17T08:16:12.352Z",
  "createdAt": "2025-12-03T10:58:40.842Z",
  "id": "NyC6Z3by7wRaLBYM",
  "name": "chatbot-winkle-main-WEB",
  "description": null,
  "active": true,
  "isArchived": false,
  "nodes": [
    {
      "parameters": {
        "assignments": {
          "assignments": [
            {
              "id": "716793bd-8b85-449e-b4a5-31051cfd5ee1",
              "name": "chatInput",
              "value": "={{ $('chat').item.json.body.chatInput }}",
              "type": "string"
            },
            {
              "id": "37455e13-ce96-470a-952f-43cab4686f66",
              "name": "sessionId",
              "value": "={{ $('chat').item.json.body.sessionId }}",
              "type": "string"
            }
          ]
        },
        "options": {}
      },
      "type": "n8n-nodes-base.set",
      "typeVersion": 3.4,
      "position": [
        1200,
        528
      ],
      "id": "82a7cca5-bd32-4348-b014-8f628cd6c586",
      "name": "Mapeo Chat1"
    },
    {
      "parameters": {
        "content": "",
        "height": 272,
        "width": 272,
        "color": 3
      },
      "type": "n8n-nodes-base.stickyNote",
      "typeVersion": 1,
      "position": [
        -848,
        448
      ],
      "id": "e2d541d8-0be5-4a07-b0b5-a169b9826f8b",
      "name": "Sticky Note5"
    },
    {
      "parameters": {
        "content": "## Si es texto",
        "height": 272,
        "width": 992,
        "color": 2
      },
      "type": "n8n-nodes-base.stickyNote",
      "typeVersion": 1,
      "position": [
        1136,
        464
      ],
      "id": "83e517ea-33f9-4fbe-9376-2ac6f6b36a43",
      "name": "Sticky Note6"
    },
    {
      "parameters": {
        "content": "## Sentimiento y Clasificador",
        "height": 624,
        "width": 1312,
        "color": 4
      },
      "type": "n8n-nodes-base.stickyNote",
      "typeVersion": 1,
      "position": [
        2288,
        272
      ],
      "id": "2c974488-5ace-409c-bf74-84c80a931a50",
      "name": "Sticky Note8"
    },
    {
      "parameters": {
        "content": "",
        "height": 272,
        "width": 256,
        "color": 5
      },
      "type": "n8n-nodes-base.stickyNote",
      "typeVersion": 1,
      "position": [
        240,
        448
      ],
      "id": "86f063fb-0b58-4293-8b48-1340e9349caa",
      "name": "Sticky Note17"
    },
    {
      "parameters": {
        "resource": "audio",
        "operation": "transcribe",
        "binaryPropertyName": "data0",
        "options": {
          "language": "es"
        }
      },
      "type": "@n8n/n8n-nodes-langchain.openAi",
      "typeVersion": 2,
      "position": [
        784,
        736
      ],
      "id": "75583097-9c8c-402d-af4e-88aa490fcf5d",
      "name": "Transcribe a recording1",
      "credentials": {
        "openAiApi": {
          "id": "EPBmvTYfgROzhEq9",
          "name": "OpenAi account"
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
                    "leftValue": "={{ $json.files[0].fileType }}",
                    "rightValue": "image",
                    "operator": {
                      "type": "string",
                      "operation": "equals"
                    },
                    "id": "c6b41916-bb63-40cc-8e80-8ea3a5994c31"
                  }
                ],
                "combinator": "and"
              },
              "renameOutput": true,
              "outputKey": "image"
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
                    "id": "e20f52a4-3c80-43ef-ade4-7d827e2d647b",
                    "leftValue": "={{ $json.files[0].fileType }}",
                    "rightValue": "audio",
                    "operator": {
                      "type": "string",
                      "operation": "notExists",
                      "singleValue": true
                    }
                  }
                ],
                "combinator": "and"
              },
              "renameOutput": true,
              "outputKey": "Text"
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
                    "id": "1e7c7612-1edc-4fe2-b0b8-7005758c3ce6",
                    "leftValue": "={{ $json.files[0].fileType }}",
                    "rightValue": "audio",
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
              "outputKey": "audio"
            }
          ]
        },
        "options": {}
      },
      "type": "n8n-nodes-base.switch",
      "typeVersion": 3.3,
      "position": [
        320,
        512
      ],
      "id": "b7945e81-4851-4278-8c45-ea2fbff5c01c",
      "name": "Switch1"
    },
    {
      "parameters": {
        "content": "## Si es Imagen",
        "height": 272,
        "width": 992,
        "color": 2
      },
      "type": "n8n-nodes-base.stickyNote",
      "typeVersion": 1,
      "position": [
        1136,
        160
      ],
      "id": "52fe3b81-8a11-4e51-babc-a82b738e8cd3",
      "name": "Sticky Note18"
    },
    {
      "parameters": {
        "assignments": {
          "assignments": [
            {
              "id": "716793bd-8b85-449e-b4a5-31051cfd5ee1",
              "name": "chatInput",
              "value": "={{ $('chat').item.json.chatInput }}",
              "type": "string"
            },
            {
              "id": "37455e13-ce96-470a-952f-43cab4686f66",
              "name": "sessionId",
              "value": "={{ $('chat').item.json.sessionId }}",
              "type": "string"
            },
            {
              "id": "69e4bd03-4f03-43f4-8dea-004ef4c2c0e5",
              "name": "explicacionImagen",
              "value": "={{ $json.text }}",
              "type": "string"
            }
          ]
        },
        "options": {}
      },
      "type": "n8n-nodes-base.set",
      "typeVersion": 3.4,
      "position": [
        1200,
        224
      ],
      "id": "e3c0fa32-99c8-439f-b73a-a6638afc7aa0",
      "name": "Mapeo Chat Imagen1"
    },
    {
      "parameters": {
        "content": "## Si es audio",
        "height": 272,
        "width": 992,
        "color": 2
      },
      "type": "n8n-nodes-base.stickyNote",
      "typeVersion": 1,
      "position": [
        1136,
        768
      ],
      "id": "50d9d284-5ed3-4dc9-be48-93a010369253",
      "name": "Sticky Note19"
    },
    {
      "parameters": {
        "assignments": {
          "assignments": [
            {
              "id": "716793bd-8b85-449e-b4a5-31051cfd5ee1",
              "name": "chatInput",
              "value": "={{ $json.text }}",
              "type": "string"
            },
            {
              "id": "37455e13-ce96-470a-952f-43cab4686f66",
              "name": "sessionId",
              "value": "={{ $('chat').item.json.sessionId }}",
              "type": "string"
            }
          ]
        },
        "includeOtherFields": true,
        "options": {}
      },
      "type": "n8n-nodes-base.set",
      "typeVersion": 3.4,
      "position": [
        1216,
        864
      ],
      "id": "972ee5b6-bdd8-479c-b00b-d7bef0b9492f",
      "name": "Mapeo Chat Audio1"
    },
    {
      "parameters": {
        "jsCode": "// Accedemos al JSON del nodo anterior\nconst chatInput = $input.first().json.chatInput;\nconst sessionId = $input.first().json.sessionId;\n\n// Concatenamos ambos valores con un separador (puedes cambiarlo por lo que prefieras)\nconst link = `${sessionId} - ${chatInput}`;\n\n// Devolvemos un nuevo objeto con la propiedad 'link'\nreturn [\n  {\n    json: {\n      link: link\n    }\n  }\n];\n"
      },
      "type": "n8n-nodes-base.code",
      "typeVersion": 2,
      "position": [
        1552,
        224
      ],
      "id": "691a07b9-9dc4-4151-8311-75e071552c3b",
      "name": "Generate Link Imagen1"
    },
    {
      "parameters": {
        "jsCode": "// Accedemos al JSON del nodo anterior\nconst chatInput = $input.first().json.chatInput;\nconst sessionId = $input.first().json.sessionId;\n\n// Concatenamos ambos valores con un separador (puedes cambiarlo por lo que prefieras)\nconst link = `${sessionId} - ${chatInput}`;\n\n// Devolvemos un nuevo objeto con la propiedad 'link'\nreturn [\n  {\n    json: {\n      link: link\n    }\n  }\n];\n"
      },
      "type": "n8n-nodes-base.code",
      "typeVersion": 2,
      "position": [
        1552,
        528
      ],
      "id": "9f51ad32-a92b-42a4-9e13-de64258343cc",
      "name": "Generate Link Texto1"
    },
    {
      "parameters": {
        "jsCode": "// Accedemos al JSON del nodo anterior\nconst chatInput = $input.first().json.chatInput;\nconst sessionId = $input.first().json.sessionId;\n\n// Concatenamos ambos valores con un separador (puedes cambiarlo por lo que prefieras)\nconst link = `${sessionId} - ${chatInput}`;\n\n// Devolvemos un nuevo objeto con la propiedad 'link'\nreturn [\n  {\n    json: {\n      link: link\n    }\n  }\n];\n"
      },
      "type": "n8n-nodes-base.code",
      "typeVersion": 2,
      "position": [
        1568,
        864
      ],
      "id": "9d547e90-7940-4588-a53e-98c37a1d75df",
      "name": "Generate Link Audio1"
    },
    {
      "parameters": {
        "promptType": "define",
        "text": "🧠 Contexto del Agente\n\nEres un agente intermediario encargado de analizar y describir contenido visual y textual para el chatbot de Winkle, una empresa especializada en la fabricación de filamentos y resinas 3D.\n\n🎯 Objetivo\n\nTu tarea es interpretar la imagen y el mensaje del cliente, extrayendo información técnica y relevante que pueda ayudar al chatbot de Winkle a ofrecer una respuesta precisa y profesional.\n\n🧩 Instrucciones\n\nAnaliza la imagen recibida y describe lo que ves de forma concisa, objetiva y técnica.\n\nIdentifica posibles problemas de impresión (por ejemplo: subextrusión, warping, capas mal adheridas, stringing, etc.).\n\nMenciona detalles técnicos relevantes (tipo de material, color, boquilla, impresora, defectos visibles, etc.).\n\nResume el mensaje del cliente destacando solo la intención principal o el problema reportado.\n\nEl resultado final debe ser una explicación breve y clara, dirigida al chatbot de Winkle, que le ayude a entender la situación sin tener que ver la imagen.\n\n✍️ Ejemplo de salida\n\nLa imagen muestra una pieza impresa con filamento PLA color blanco, con signos de mala adhesión entre capas y warping en la base.\nEl cliente menciona que el problema ocurre en las primeras capas.",
        "messages": {
          "messageValues": [
            {
              "type": "HumanMessagePromptTemplate",
              "messageType": "imageBinary",
              "binaryImageDataKey": "data0"
            },
            {
              "type": "HumanMessagePromptTemplate",
              "message": "={{ $json.chatInput }}"
            }
          ]
        },
        "batching": {}
      },
      "type": "@n8n/n8n-nodes-langchain.chainLlm",
      "typeVersion": 1.7,
      "position": [
        720,
        320
      ],
      "id": "2cb4cef5-677f-43c3-afd2-2530e84737e5",
      "name": "Reconocimiento de Imagen1"
    },
    {
      "parameters": {
        "model": {
          "__rl": true,
          "value": "gpt-4.1-mini",
          "mode": "list",
          "cachedResultName": "gpt-4.1-mini"
        },
        "options": {
          "temperature": 0.2
        }
      },
      "type": "@n8n/n8n-nodes-langchain.lmChatOpenAi",
      "typeVersion": 1.2,
      "position": [
        2560,
        752
      ],
      "id": "995735b8-d9bd-4dec-8d00-40916f0358a2",
      "name": "GPT 4.1 Mini1",
      "credentials": {
        "openAiApi": {
          "id": "EPBmvTYfgROzhEq9",
          "name": "OpenAi account"
        }
      }
    },
    {
      "parameters": {
        "content": "",
        "height": 240,
        "width": 496,
        "color": 2
      },
      "type": "n8n-nodes-base.stickyNote",
      "typeVersion": 1,
      "position": [
        3824,
        464
      ],
      "id": "6a97b17f-084d-4140-bf14-7d1408eb1a08",
      "name": "Sticky Note20"
    },
    {
      "parameters": {
        "operation": "update",
        "documentId": {
          "__rl": true,
          "value": "1AoaykyVTjFzRmPiJh3CbO3nTUyyuGq6WtLOvRGg2CwM",
          "mode": "list",
          "cachedResultName": "Prompts",
          "cachedResultUrl": "https://docs.google.com/spreadsheets/d/1AoaykyVTjFzRmPiJh3CbO3nTUyyuGq6WtLOvRGg2CwM/edit?usp=drivesdk"
        },
        "sheetName": {
          "__rl": true,
          "value": 1579569901,
          "mode": "list",
          "cachedResultName": "Test Clientes",
          "cachedResultUrl": "https://docs.google.com/spreadsheets/d/1AoaykyVTjFzRmPiJh3CbO3nTUyyuGq6WtLOvRGg2CwM/edit#gid=1579569901"
        },
        "columns": {
          "mappingMode": "defineBelow",
          "value": {
            "output": "={{ $json.output}}",
            "link": "={{ $json.link}}"
          },
          "matchingColumns": [
            "link"
          ],
          "schema": [
            {
              "id": "id",
              "displayName": "id",
              "required": false,
              "defaultMatch": true,
              "display": true,
              "type": "string",
              "canBeUsedToMatch": true,
              "removed": true
            },
            {
              "id": "email",
              "displayName": "email",
              "required": false,
              "defaultMatch": false,
              "display": true,
              "type": "string",
              "canBeUsedToMatch": true,
              "removed": true
            },
            {
              "id": "link",
              "displayName": "link",
              "required": false,
              "defaultMatch": false,
              "display": true,
              "type": "string",
              "canBeUsedToMatch": true,
              "removed": false
            },
            {
              "id": "comentarios",
              "displayName": "comentarios",
              "required": false,
              "defaultMatch": false,
              "display": true,
              "type": "string",
              "canBeUsedToMatch": true,
              "removed": true
            },
            {
              "id": "input",
              "displayName": "input",
              "required": false,
              "defaultMatch": false,
              "display": true,
              "type": "string",
              "canBeUsedToMatch": true,
              "removed": true
            },
            {
              "id": "Explicación Imagen",
              "displayName": "Explicación Imagen",
              "required": false,
              "defaultMatch": false,
              "display": true,
              "type": "string",
              "canBeUsedToMatch": true,
              "removed": true
            },
            {
              "id": "output",
              "displayName": "output",
              "required": false,
              "defaultMatch": false,
              "display": true,
              "type": "string",
              "canBeUsedToMatch": true,
              "removed": false
            },
            {
              "id": "row_number",
              "displayName": "row_number",
              "required": false,
              "defaultMatch": false,
              "display": true,
              "type": "number",
              "canBeUsedToMatch": true,
              "readOnly": true,
              "removed": true
            }
          ],
          "attemptToConvertTypes": false,
          "convertFieldsToString": false
        },
        "options": {}
      },
      "type": "n8n-nodes-base.googleSheets",
      "typeVersion": 4.7,
      "position": [
        4176,
        528
      ],
      "id": "b23f2e97-09e7-4622-b68f-c62b61620618",
      "name": "Update row in sheet",
      "retryOnFail": true,
      "alwaysOutputData": true,
      "credentials": {
        "googleSheetsOAuth2Api": {
          "id": "5AL0KPkfdvFFUXdP",
          "name": "Google Sheets account"
        }
      }
    },
    {
      "parameters": {
        "content": "## Gestión Multimedia",
        "height": 688,
        "width": 384,
        "color": 4
      },
      "type": "n8n-nodes-base.stickyNote",
      "typeVersion": 1,
      "position": [
        624,
        256
      ],
      "id": "87efd4ee-d384-4afd-ac71-800b589cc7e3",
      "name": "Sticky Note21"
    },
    {
      "parameters": {
        "operation": "append",
        "documentId": {
          "__rl": true,
          "value": "1AoaykyVTjFzRmPiJh3CbO3nTUyyuGq6WtLOvRGg2CwM",
          "mode": "list",
          "cachedResultName": "Prompts",
          "cachedResultUrl": "https://docs.google.com/spreadsheets/d/1AoaykyVTjFzRmPiJh3CbO3nTUyyuGq6WtLOvRGg2CwM/edit?usp=drivesdk"
        },
        "sheetName": {
          "__rl": true,
          "value": 1720095373,
          "mode": "list",
          "cachedResultName": "creacion ticket",
          "cachedResultUrl": "https://docs.google.com/spreadsheets/d/1AoaykyVTjFzRmPiJh3CbO3nTUyyuGq6WtLOvRGg2CwM/edit#gid=1720095373"
        },
        "columns": {
          "mappingMode": "defineBelow",
          "value": {
            "input": "={{ $('Mapeo Chat Imagen1').item.json.chatInput }}",
            "id": "={{ $('Mapeo Chat Imagen1').item.json.sessionId }}",
            "link": "={{ $json.link }}",
            "Explicación Imagen": "={{ $('Mapeo Chat Imagen1').item.json.explicacionImagen }}"
          },
          "matchingColumns": [
            "input"
          ],
          "schema": [
            {
              "id": "id",
              "displayName": "id",
              "required": false,
              "defaultMatch": true,
              "display": true,
              "type": "string",
              "canBeUsedToMatch": true,
              "removed": false
            },
            {
              "id": "link",
              "displayName": "link",
              "required": false,
              "defaultMatch": false,
              "display": true,
              "type": "string",
              "canBeUsedToMatch": true,
              "removed": false
            },
            {
              "id": "comentarios",
              "displayName": "comentarios",
              "required": false,
              "defaultMatch": false,
              "display": true,
              "type": "string",
              "canBeUsedToMatch": true,
              "removed": true
            },
            {
              "id": "input",
              "displayName": "input",
              "required": false,
              "defaultMatch": false,
              "display": true,
              "type": "string",
              "canBeUsedToMatch": true,
              "removed": false
            },
            {
              "id": "Explicación Imagen",
              "displayName": "Explicación Imagen",
              "required": false,
              "defaultMatch": false,
              "display": true,
              "type": "string",
              "canBeUsedToMatch": true,
              "removed": false
            },
            {
              "id": "output",
              "displayName": "output",
              "required": false,
              "defaultMatch": false,
              "display": true,
              "type": "string",
              "canBeUsedToMatch": true,
              "removed": true
            }
          ],
          "attemptToConvertTypes": false,
          "convertFieldsToString": false
        },
        "options": {}
      },
      "type": "n8n-nodes-base.googleSheets",
      "typeVersion": 4.7,
      "position": [
        1936,
        224
      ],
      "id": "e1ee2ade-1f09-4277-8360-41e6b070897a",
      "name": "Update Input Imagen1",
      "retryOnFail": true,
      "credentials": {
        "googleSheetsOAuth2Api": {
          "id": "5AL0KPkfdvFFUXdP",
          "name": "Google Sheets account"
        }
      }
    },
    {
      "parameters": {
        "operation": "append",
        "documentId": {
          "__rl": true,
          "value": "1AoaykyVTjFzRmPiJh3CbO3nTUyyuGq6WtLOvRGg2CwM",
          "mode": "list",
          "cachedResultName": "Prompts",
          "cachedResultUrl": "https://docs.google.com/spreadsheets/d/1AoaykyVTjFzRmPiJh3CbO3nTUyyuGq6WtLOvRGg2CwM/edit?usp=drivesdk"
        },
        "sheetName": {
          "__rl": true,
          "value": 1579569901,
          "mode": "list",
          "cachedResultName": "Test Clientes",
          "cachedResultUrl": "https://docs.google.com/spreadsheets/d/1AoaykyVTjFzRmPiJh3CbO3nTUyyuGq6WtLOvRGg2CwM/edit#gid=1579569901"
        },
        "columns": {
          "mappingMode": "defineBelow",
          "value": {
            "input": "={{ $('chat').item.json.body.chatInput }}",
            "id": "={{ $('chat').item.json.body.sessionId }}",
            "link": "={{ $json.link }}",
            "email": "={{ $('chat').item.json.body.email }}"
          },
          "matchingColumns": [
            "input"
          ],
          "schema": [
            {
              "id": "id",
              "displayName": "id",
              "required": false,
              "defaultMatch": true,
              "display": true,
              "type": "string",
              "canBeUsedToMatch": true,
              "removed": false
            },
            {
              "id": "email",
              "displayName": "email",
              "required": false,
              "defaultMatch": false,
              "display": true,
              "type": "string",
              "canBeUsedToMatch": true,
              "removed": false
            },
            {
              "id": "link",
              "displayName": "link",
              "required": false,
              "defaultMatch": false,
              "display": true,
              "type": "string",
              "canBeUsedToMatch": true,
              "removed": false
            },
            {
              "id": "comentarios",
              "displayName": "comentarios",
              "required": false,
              "defaultMatch": false,
              "display": true,
              "type": "string",
              "canBeUsedToMatch": true,
              "removed": true
            },
            {
              "id": "input",
              "displayName": "input",
              "required": false,
              "defaultMatch": false,
              "display": true,
              "type": "string",
              "canBeUsedToMatch": true,
              "removed": false
            },
            {
              "id": "Explicación Imagen",
              "displayName": "Explicación Imagen",
              "required": false,
              "defaultMatch": false,
              "display": true,
              "type": "string",
              "canBeUsedToMatch": true,
              "removed": true
            },
            {
              "id": "output",
              "displayName": "output",
              "required": false,
              "defaultMatch": false,
              "display": true,
              "type": "string",
              "canBeUsedToMatch": true,
              "removed": true
            }
          ],
          "attemptToConvertTypes": false,
          "convertFieldsToString": false
        },
        "options": {}
      },
      "type": "n8n-nodes-base.googleSheets",
      "typeVersion": 4.7,
      "position": [
        1936,
        528
      ],
      "id": "e143758d-c55d-4722-80a5-5e010324b8d0",
      "name": "Update Input Texto1",
      "retryOnFail": true,
      "credentials": {
        "googleSheetsOAuth2Api": {
          "id": "5AL0KPkfdvFFUXdP",
          "name": "Google Sheets account"
        }
      }
    },
    {
      "parameters": {
        "operation": "append",
        "documentId": {
          "__rl": true,
          "value": "1AoaykyVTjFzRmPiJh3CbO3nTUyyuGq6WtLOvRGg2CwM",
          "mode": "list",
          "cachedResultName": "Prompts",
          "cachedResultUrl": "https://docs.google.com/spreadsheets/d/1AoaykyVTjFzRmPiJh3CbO3nTUyyuGq6WtLOvRGg2CwM/edit?usp=drivesdk"
        },
        "sheetName": {
          "__rl": true,
          "value": 1720095373,
          "mode": "list",
          "cachedResultName": "creacion ticket",
          "cachedResultUrl": "https://docs.google.com/spreadsheets/d/1AoaykyVTjFzRmPiJh3CbO3nTUyyuGq6WtLOvRGg2CwM/edit#gid=1720095373"
        },
        "columns": {
          "mappingMode": "defineBelow",
          "value": {
            "id": "={{ $('Mapeo Chat Audio1').item.json.sessionId }}",
            "link": "={{ $json.link }}",
            "input": "={{ $('Mapeo Chat Audio1').item.json.chatInput }}"
          },
          "matchingColumns": [
            "input"
          ],
          "schema": [
            {
              "id": "id",
              "displayName": "id",
              "required": false,
              "defaultMatch": true,
              "display": true,
              "type": "string",
              "canBeUsedToMatch": true,
              "removed": false
            },
            {
              "id": "link",
              "displayName": "link",
              "required": false,
              "defaultMatch": false,
              "display": true,
              "type": "string",
              "canBeUsedToMatch": true,
              "removed": false
            },
            {
              "id": "comentarios",
              "displayName": "comentarios",
              "required": false,
              "defaultMatch": false,
              "display": true,
              "type": "string",
              "canBeUsedToMatch": true,
              "removed": true
            },
            {
              "id": "input",
              "displayName": "input",
              "required": false,
              "defaultMatch": false,
              "display": true,
              "type": "string",
              "canBeUsedToMatch": true,
              "removed": false
            },
            {
              "id": "Explicación Imagen",
              "displayName": "Explicación Imagen",
              "required": false,
              "defaultMatch": false,
              "display": true,
              "type": "string",
              "canBeUsedToMatch": true,
              "removed": true
            },
            {
              "id": "output",
              "displayName": "output",
              "required": false,
              "defaultMatch": false,
              "display": true,
              "type": "string",
              "canBeUsedToMatch": true,
              "removed": true
            }
          ],
          "attemptToConvertTypes": false,
          "convertFieldsToString": false
        },
        "options": {}
      },
      "type": "n8n-nodes-base.googleSheets",
      "typeVersion": 4.7,
      "position": [
        1936,
        864
      ],
      "id": "21f3b1e8-f8fb-45c3-b5e0-0b0f5572c18e",
      "name": "Update Input Audio1",
      "retryOnFail": true,
      "credentials": {
        "googleSheetsOAuth2Api": {
          "id": "5AL0KPkfdvFFUXdP",
          "name": "Google Sheets account"
        }
      }
    },
    {
      "parameters": {
        "content": "",
        "height": 240,
        "color": 3
      },
      "type": "n8n-nodes-base.stickyNote",
      "typeVersion": 1,
      "position": [
        4352,
        464
      ],
      "id": "96c5dd86-8e2e-4a61-b6f9-cbb2aee5afcf",
      "name": "Sticky Note23"
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
        832,
        448
      ],
      "id": "88c9ca4c-52cf-4e10-b892-9c81f25447c2",
      "name": "GPT 4.1 MINI1",
      "credentials": {
        "openAiApi": {
          "id": "EPBmvTYfgROzhEq9",
          "name": "OpenAi account"
        }
      }
    },
    {
      "parameters": {
        "assignments": {
          "assignments": [
            {
              "id": "524be3ec-fcff-4dc3-a119-368505f6d88c",
              "name": "output",
              "value": "={{ $json.output}}",
              "type": "string"
            },
            {
              "id": "55eb9623-5cea-432c-bdfe-c458473099e0",
              "name": "sessionId",
              "value": "={{ $('chat').item.json.body.sessionId }}",
              "type": "string"
            },
            {
              "id": "cadf8c33-e169-4c89-8f72-2c506c424d5d",
              "name": "link",
              "value": "={{\n  $if($(\"Generate Link Texto1\").isExecuted, $(\"Generate Link Texto1\").item.json.link, \"\") ||\n  $if($(\"Generate Link Imagen1\").isExecuted, $(\"Generate Link Imagen1\").item.json.link, \"\") ||\n  $if($(\"Generate Link Audio1\").isExecuted, $(\"Generate Link Audio1\").item.json.link, \"\") ||\n  $if($(\"Generate Link Texto Predefinido\").isExecuted, $(\"Generate Link Texto Predefinido\").item.json.link, \"\")\n}}",
              "type": "string"
            }
          ]
        },
        "options": {}
      },
      "type": "n8n-nodes-base.set",
      "typeVersion": 3.4,
      "position": [
        3904,
        528
      ],
      "id": "ca437e93-f449-446e-8b7e-e9c32e748462",
      "name": "Edit Fields2"
    },
    {
      "parameters": {
        "options": {}
      },
      "type": "n8n-nodes-base.respondToWebhook",
      "typeVersion": 1.4,
      "position": [
        4400,
        528
      ],
      "id": "98612fef-fba9-44a5-9c59-f734391148e8",
      "name": "Respond to Webhook1"
    },
    {
      "parameters": {
        "inputText": "={{ $json.input }} ",
        "options": {
          "systemPromptTemplate": "Eres el encargado de categorizar y hacer un análisis de sentimiento de los mensajes de clientes de la empresa Winkle, de filamentos 3D. Solo quiero que coloques el mensaje en un sentimiento negativo cuando sea MUY CLARO este sentimiento, debe estar MUY enfadado.\nTambien, cuando el cliente especificamente mencione que quiere hablar con un humano, se le colocará como en sentimiento negativo. "
        }
      },
      "type": "@n8n/n8n-nodes-langchain.sentimentAnalysis",
      "typeVersion": 1.1,
      "position": [
        2352,
        528
      ],
      "id": "67393232-17b2-41fa-8f30-e175ef135207",
      "name": "analizador"
    },
    {
      "parameters": {
        "promptType": "define",
        "text": "={{ \n$json.input + \n($(\"Mapeo Chat Imagen1\").isExecuted ? \n    \"\\nDescripcion de la foto: \" + $(\"Mapeo Chat Imagen1\").item.json.explicacionImagen \n    : \"\"\n) \n}}",
        "needsFallback": true,
        "options": {
          "systemMessage": "IDENTIDAD Y COMPORTAMIENTO\nEres un agente de atención al cliente del equipo de soporte de Winkle. Tu comportamiento debe ser profesional, técnico, amable y cercano, como si fueras una persona real del equipo. Nunca reveles que eres una IA o un asistente virtual. Tu misión es resolver la consulta del cliente aplicando las normas del tipo de caso adecuado.\n----\nCuando contestes una cuestión, NO hagas preguntas al usuario con el siguiente paso, simplemente contesta la pregunta y ya está. No pongas nada de: ¿Quieres que te ayude a...? o ¿Quieres que haga...? Simplemente contesta la pregunta y ya.\n----\nCONTEXTO DE NEGOCIO\nWinkle es una marca española que fabrica y comercializa filamentos 3D en Salamanca. También comercializa resina 3D, aunque no la fabrica directamente (esta información es privada y no debe compartirse con clientes). No se realiza venta directa desde el chatbot. Para compras normales, los clientes deben dirigirse a winkle.shop.\nRecogida Local\nLa recogida local está disponible únicamente para pedidos ya realizados en la siguiente dirección:\n----\nDirección: Calle Primera número 3, Carbajosa de la Sagrada, Salamanca\nHorario de lunes a jueves: 16:00 a 19:00\nHorario de viernes: 9:00 a 15:00\nImportante: Los clientes deben dejar un mínimo de 24 horas entre la realización del pedido y la recogida para que el pedido esté preparado.\n----\nEnvíos\nLos envíos nacionales se realizan en un plazo de 24 a 48 horas, aunque pueden ocurrir incidencias puntuales. Nunca debes mencionar el nombre de la empresa de transporte. Si el cliente pregunta específicamente por la empresa de transporte, debes derivar siempre su consulta a transporte@winkle.shop.\n----\nTienda Física\nWinkle NO tiene tienda física propia. Los clientes pueden comprar físicamente productos Winkle en el Hipermercado E.Leclerc de Salamanca. Para recogidas de pedidos online, deben usar la dirección de recogida local indicada anteriormente.\n----\nHERRAMIENTAS DISPONIBLES\nTienes acceso a las siguientes herramientas para resolver consultas:\n1- Google Sheets con fichas técnicas por material: Contiene información técnica detallada de cada tipo de filamento que comercializa Winkle.\n2- XML con catálogo de productos: Contiene el listado completo de productos Winkle, incluyendo materiales, colores, pesos, diámetros y formatos disponibles.\n3- Google Sheets con parámetros de impresión: Contiene los parámetros recomendados de impresión para cada material (temperaturas, velocidades, etc.).\n4- Gmail: Para generar y enviar tickets cuando sea necesaria atención humana especializada. Es tu principal herramienta, debes utilizarla siempre\n--\nCRÍTICO: USO DE LA HERRAMIENTA GMAIL\nESTA ES LA PARTE MÁS IMPORTANTE DEL SISTEMA:\nCuando necesites generar un ticket o gestionar una incidencia que requiera atención del equipo de Winkle, DEBES USAR OBLIGATORIAMENTE LA HERRAMIENTA GMAIL.\n--\nCÓMO USAR LA HERRAMIENTA GMAIL:\nSIEMPRE que un caso requiera generar un ticket, llama a la herramienta Gmail inmediatamente.\nEn el campo \"to\" (destinatario), coloca el correo electrónico correspondiente según el tipo de caso:\n\ntransporte@winkle.shop -> problemas de envío, pedido no llega, dirección incorrecta)\nbackoffice@winkle.shop ->producto defectuoso, escalados generales\nfacturacion@ecotisa.com -> modificaciones de factura)\nana.manchado@winkle.shop -> distribuidores, compras al por mayor, operaciones extracomunitarias fuera de europa\nmateo.herrero@winkle.shop -> envíos y compras en Europa\ncomunicación@winkle.shop -> colaboraciones comerciales, marketing\n\n\nEn el campo \"subject\" (asunto), escribe un resumen breve y claro del caso, por ejemplo:\n\"Incidencia pedido #12345 - No ha llegado\"\n\"Producto defectuoso - Pedido #67890\"\n\"Solicitud modificación factura - Pedido #11111\"\n\"Consulta distribuidor - [Nombre cliente]\"\n\nEn el campo \"body\" (cuerpo del mensaje), incluye TODOS los datos del cliente que hayas recopilado y un resumen detallado del caso. Estructura clara:\nDatos del cliente (nombre, email, teléfono si aplica, número de pedido si aplica)\nDescripción detallada del problema o consulta\nCualquier información adicional relevante (material, peso, color, número de bobinas, etc.)\n\nDespués de enviar el email con la herramienta Gmail, informa al cliente de manera natural en el chat que su consulta ha sido registrada y que el equipo correspondiente se pondrá en contacto con él. NO muestres el contenido del ticket en el chat.\n\nEJEMPLO DE USO CORRECTO:\nSi un cliente reporta que su pedido #12345 no ha llegado:\n\nRecopila: número de pedido (12345) y email del cliente (cliente@ejemplo.com)\nUSA LA HERRAMIENTA GMAIL con:\n\nto: transporte@winkle.shop\nsubject: \"Incidencia pedido #12345 - Pedido no recibido\"\nbody: \"Número de pedido: 12345\\nEmail del cliente: cliente@ejemplo.com\\n\\nResumen: El cliente reporta que su pedido no ha llegado. Realizó el pedido hace X días y aún no ha recibido el paquete.\"\n\nResponde al cliente: \"He registrado tu incidencia. El equipo de transporte revisará tu pedido #12345 y se pondrá en contacto contigo por email para resolver el problema lo antes posible.\"\n\nNO hagas esto:\nNo intentes enviar emails manualmente escribiendo el contenido en el chat\nNo olvides usar la herramienta Gmail cuando se necesite un ticket\nNo omitas datos importantes del cliente en el cuerpo del email\nNo envíes a otras direcciones que no sean las estipuladas aqui\n\nSÍ haz esto:\nUSA LA HERRAMIENTA GMAIL cada vez que necesites generar un ticket\nIncluye todos los datos recopilados del cliente en el cuerpo del email\nEnvía el email al destinatario correcto según el tipo de caso\nInforma al cliente de manera natural que su caso ha sido registrado\n-------\nREGLA DE FEEDBACK\nDebes solicitar feedback únicamente cuando detectes que la conversación está llegando a su fin. Las señales típicas de cierre son expresiones como: \"ok\", \"gracias\", \"perfecto\", \"me sirve\", \"vale\", \"todo claro\", \"genial\", \"ya está\", etc.\nCuando detectes estas señales, añade al final de tu respuesta este mensaje:\n\"Antes de terminar, ¿podrías valorar tu experiencia con el chatbot del 1 al 5? (1 = Muy mala, 5 = Excelente)\"\nSi no detectas señales claras de que la conversación está terminando, NO pidas feedback.\nLÓGICA MULTIAGENTE\nDebes analizar el mensaje del cliente y decidir automáticamente qué módulo aplicar según el tipo de consulta. A continuación se detallan todos los módulos disponibles:\n-------\nMÓDULO 1: AGENTE LOGÍSTICO\nAplica este módulo para incidencias relacionadas con pedidos, envíos, errores de recepción o productos defectuosos.\nCasos típicos:\n\nEl pedido no llega\nEl pedido llega a una dirección incorrecta\nEl pedido recibido es incorrecto\nEl producto recibido es defectuoso\n\n- Caso A: Gestión de transporte\nSi el problema debe ser gestionado por el departamento de transporte (pedido no llega, dirección incorrecta, retrasos, etc.):\nInformación a solicitar:\n\nNúmero de pedido\nEmail del cliente\n\nAcción OBLIGATORIA:\nUSA LA HERRAMIENTA GMAIL para enviar un ticket a transporte@winkle.shop con:\n\nto: transporte@winkle.shop\nsubject: \"Incidencia pedido #[número] - [breve descripción]\"\nbody: Incluye número de pedido, email del cliente y resumen detallado del problema\n\nMensaje al cliente:\nInforma de manera natural que has registrado su consulta y que el equipo de transporte se pondrá en contacto con él para resolver la incidencia.\n\n- Caso B: Producto erróneo o defectuoso\nSi el producto recibido es incorrecto o tiene defectos:\nInformación a solicitar:\n\nNombre del cliente\nNúmero de pedido\nMaterial afectado\nPeso del producto\nDiámetro del filamento\nColor del producto\nNúmero de bobinas afectadas\n\nAcción OBLIGATORIA:\nUSA LA HERRAMIENTA GMAIL para enviar un ticket a backoffice@winkle.shop con:\n\nto: backoffice@winkle.shop\nsubject: \"Producto defectuoso - Pedido #[número]\"\nbody: Incluye nombre, número de pedido, material, peso, diámetro, color, número de bobinas afectadas y resumen detallado del problema\n\nMensaje al cliente:\nInforma de manera natural que has registrado su caso y que el equipo se pondrá en contacto con él para gestionar la reposición o solución correspondiente.\n\n- Caso C: Escalado general logístico\nSi no puedes resolver la consulta logística con la información disponible:\nInformación a solicitar:\n\nNombre del cliente\nEmail del cliente\n\nAcción OBLIGATORIA:\nUSA LA HERRAMIENTA GMAIL para enviar un ticket a backoffice@winkle.shop con:\n\nto: backoffice@winkle.shop\nsubject: \"Consulta logística - [Nombre cliente]\"\nbody: Incluye nombre, email y resumen detallado de la consulta\n--------------\nMÓDULO 2: AGENTE MODIFICACIÓN DE DATOS\nAplica este módulo cuando el cliente desee modificar datos personales o de facturación.\n- Caso A: Modificación de datos personales para futuras compras\nSi el cliente quiere actualizar sus datos personales (dirección, teléfono, etc.) para futuras compras:\nAcción:\nRedirige al cliente a la sección \"Mi Cuenta\" en winkle.shop, donde puede gestionar sus datos personales de forma autónoma. No es necesario usar la herramienta Gmail ni generar ticket.\n\n- Caso B: Modificación de datos de factura\nSi el cliente necesita modificar los datos de una factura ya emitida:\nInformación a solicitar:\n\nNúmero de pedido\nEmail del cliente\n\nAcción OBLIGATORIA:\nUSA LA HERRAMIENTA GMAIL para enviar un ticket a cobros@winkle.shop con:\n\nto: facturacion@ecotisa.com\nsubject: \"Modificación factura - Pedido #[número]\"\nbody: Incluye número de pedido, email del cliente y resumen de los datos que necesita modificar\n\nMensaje al cliente:\nInforma de manera natural que has registrado su solicitud y que el departamento de facturación se pondrá en contacto con él.\n\n- Caso C: Escalado\nSi no puedes resolver la consulta de modificación de datos:\nAcción OBLIGATORIA:\nUSA LA HERRAMIENTA GMAIL para enviar un ticket a backoffice@winkle.shop con los datos del cliente y el resumen del caso.\n----------------\nMÓDULO 3: AGENTE CATÁLOGO\nAplica este módulo para consultas sobre información de filamentos, formatos disponibles, colores, características técnicas, pesos, diámetros, etc.\nAcción principal:\nUsa siempre las herramientas disponibles para responder:\n\nConsulta el XML con el catálogo de productos para información sobre materiales, colores, pesos y diámetros disponibles.\nConsulta las Google Sheets con fichas técnicas para propiedades y características de cada material.\nProporciona respuestas detalladas y precisas basadas en la información oficial de Winkle.\n\nSi no encuentras la información:\nUSA LA HERRAMIENTA GMAIL para enviar un ticket a backoffice@winkle.shop con:\n\nto: backoffice@winkle.shop\nsubject: \"Consulta catálogo - [breve descripción]\"\nbody: Incluye datos del cliente y resumen de la consulta que no has podido resolver\n--------------------\nMÓDULO 4: AGENTE DISTRIBUIDOR\nAplica este módulo para consultas relacionadas con distribución, compras al por mayor, pedidos recurrentes o volúmenes grandes.\nInformación a solicitar:\n\nNombre del cliente\nEmail del cliente\nTeléfono del cliente (opcional)\n\nAcción OBLIGATORIA:\nUSA LA HERRAMIENTA GMAIL para enviar un ticket a ana.manchado@winkle.shop con:\n\nto: ana.manchado@winkle.shop\nsubject: \"Consulta distribuidor - [Nombre cliente]\"\nbody: Incluye nombre, email, teléfono (si disponible) y resumen de la consulta sobre distribución\n\nMensaje al cliente:\nInforma de manera natural que has registrado su interés y que el departamento comercial se pondrá en contacto con él para tratar su consulta sobre distribución.\nSi no puedes resolver:\nUSA LA HERRAMIENTA GMAIL para enviar un ticket a elia.rivero@winkle.shop con los datos del cliente y el resumen del caso.\n------------------\nMÓDULO 5: AGENTE CANARIAS Y EXTRANJERO\n- Caso A: Consultas desde Canarias\nWinkle NO realiza envíos a Canarias. Debes derivar al cliente a las siguientes opciones:\nPara Las Palmas / Gran Canaria:\n\nPuede recoger productos Winkle en:\nEcotisa\nDirección: Calle Barbería 5, Telde\nTeléfono: 623 47 74 17\n\nPara Tenerife u otras islas:\nPuede contactar con el mayorista:\n\nMAYORISTA CANARIO DE SISTEMAS INFORMATICOS SLU\nDirección: C/ HERMIGUA 5 LOCAL - LAS MORADITAS DE TACO, Santa Cruz de Tenerife\nTeléfono: 922626243\nMóvil: 601222705\n\nNo es necesario usar la herramienta Gmail para consultas desde Canarias, simplemente proporciona esta información.\n\n- Caso B: Consultas desde Europa\nPara consultas de clientes ubicados fuera de España pero dentro de Europa:\nInformación a solicitar:\n\nNombre del cliente\nEmail del cliente\nTeléfono del cliente (opcional)\n\nAcción OBLIGATORIA:\nUSA LA HERRAMIENTA GMAIL para enviar un ticket a mateo.herrero@winkle.shop con:\n\nto: mateo.herrero@winkle.shop\nsubject: \"Consulta envío en Europa - [País] - [Nombre cliente]\"\nbody: Incluye nombre, email, teléfono (si disponible), país del cliente y resumen de la consulta\n\nMensaje al cliente:\nInforma de manera natural que has registrado su consulta y que el departamento de envíos internacionales se pondrá en contacto con él.\n\n- Caso C: Consultas desde Extranjero\nPara consultas de clientes extracomunitarios de fuera de Europa:\nInformación a solicitar:\n\nNombre del cliente\nEmail del cliente\nTeléfono del cliente (opcional)\n\nAcción OBLIGATORIA:\nUSA LA HERRAMIENTA GMAIL para enviar un ticket a ana.manchado@winkle.shop con:\n\nto: ana.manchado@winkle.shop\nsubject: \"Consulta envío internacional - [País] - [Nombre cliente]\"\nbody: Incluye nombre, email, teléfono (si disponible), país del cliente y resumen de la consulta\n\nMensaje al cliente:\nInforma de manera natural que has registrado su consulta y que el departamento de envíos internacionales se pondrá en contacto con él.\n\nSi no puedes resolver:\nUSA LA HERRAMIENTA GMAIL para enviar un ticket a backoffice@winkle.shop con los datos del cliente y el resumen del caso.\n---------------------------------\nMÓDULO 6: AGENTE ELECCIÓN DE FILAMENTO\nAplica este módulo para consultas técnicas donde el cliente necesita ayuda para elegir el material correcto para su proyecto.\nAcción principal:\n\nUsa las Google Sheets con fichas técnicas y parámetros de impresión para proporcionar información especializada.\nExplica detalladamente las ventajas y desventajas de cada material relevante para el caso del cliente.\nConsidera factores como: resistencia mecánica, temperatura de trabajo, facilidad de impresión, acabado superficial, resistencia química, aplicación final, etc.\nProporciona recomendaciones específicas basándote en las necesidades expresadas por el cliente.\n\nSi no puedes resolver:\nUSA LA HERRAMIENTA GMAIL para enviar un ticket a backoffice@winkle.shop con:\n\nto: backoffice@winkle.shop\nsubject: \"Consulta técnica elección material - [breve descripción]\"\nbody: Incluye datos del cliente y resumen de la consulta técnica que no has podido resolver\n---------------------------------------\nMÓDULO 7: AGENTE COLABORACIÓN COMERCIAL\nAplica este módulo para consultas relacionadas con marketing, investigación, colaboraciones con Winkle, patrocinios, etc.\nInformación a solicitar:\n\nNombre del cliente\nEmail del cliente\nMotivo de la colaboración (breve descripción)\n\nAcción OBLIGATORIA:\nUSA LA HERRAMIENTA GMAIL para enviar un ticket a comunicación@winkle.shop con:\n\nto: comunicación@winkle.shop\nsubject: \"Propuesta colaboración - [Nombre cliente]\"\nbody: Incluye nombre, email y descripción detallada del motivo de colaboración\n\nMensaje al cliente:\nInforma de manera natural que has registrado su propuesta de colaboración y que el departamento de comunicación se pondrá en contacto con él.\nSi no puedes resolver:\nUSA LA HERRAMIENTA GMAIL para enviar un ticket a backoffice@winkle.shop con los datos del cliente y el resumen del caso.\n-------------------------------\nMÓDULO 8: AGENTE AMAZON\nWinkle vende productos a través de Amazon, pero NO se responsabiliza de los problemas logísticos relacionados con pedidos realizados en Amazon.\nRegla general:\nCuando un cliente tenga un problema con un pedido realizado en Amazon, debes derivarlo siempre a Amazon para que gestione la incidencia directamente con ellos.\nExcepciones (Winkle sí gestiona):\n\nProblema de etiquetado de la bobina de filamento 3D\nProblema técnico del producto en sí (calidad, defectos de fabricación)\n\nPara estas excepciones, aplica el módulo de Agente Logístico (producto defectuoso) y USA LA HERRAMIENTA GMAIL para generar el ticket correspondiente a las persona correspondiente\n\nREGLAS GENERALES OBLIGATORIAS\n\nCRÍTICO: SIEMPRE USA LA HERRAMIENTA GMAIL cuando necesites generar un ticket o gestionar una incidencia. Esta es la parte más importante del sistema. No intentes crear tickets manualmente ni olvides usar esta herramienta.\nSIEMPRE pide el email del cliente y envíalo por mail o ponlo en el ticket, NUNCA ENVIES UN TICKET O CORREO SIN PONER EL EMAIL DEL CLIENTE, ES MUY IMPORTANTE ESTO.\nNUNCA menciones el nombre de la empresa de transporte. Si el cliente pregunta específicamente, deriva a transporte@winkle.shop.\nNUNCA reveles que eres una IA o asistente virtual. Actúa como un miembro real del equipo de soporte.\nDebes ser amable, técnico y muy claro en todas tus respuestas.\nCuando uses la herramienta Gmail para generar un ticket, NO muestres el contenido del ticket en el chat. Simplemente informa al cliente de manera natural que su consulta ha sido registrada.\nCuando contestes una cuestión, NO hagas preguntas al usuario con el siguiente paso, simplemente contesta la pregunta y ya está. \n\nEl ticket enviado por Gmail siempre debe incluir:\n\nEl destinatario correcto en el campo \"to\" según el tipo de caso\nUn asunto claro y descriptivo en el campo \"subject\"\nTodos los datos del cliente recopilados en el campo \"body\"\nUn resumen claro y detallado del problema o consulta en el campo \"body\"\n\n\nSi no puedes resolver una consulta con las herramientas disponibles, siempre escala usando LA HERRAMIENTA GMAIL para generar un ticket a la persona correspondiente.\nUsa las herramientas disponibles (Google Sheets y XML) para proporcionar información precisa y actualizada sobre productos y parámetros técnicos.\nMantén un tono profesional pero cercano, como si fueras un compañero de trabajo del cliente ayudándole con su consulta.\nRECORDATORIO FINAL: La herramienta Gmail es tu forma de generar tickets. Úsala SIEMPRE que un caso requiera atención del equipo de Winkle."
        }
      },
      "type": "@n8n/n8n-nodes-langchain.agent",
      "typeVersion": 3,
      "position": [
        3120,
        512
      ],
      "id": "285d835a-84f3-41a4-b903-63a9f4f17ede",
      "name": "AI Agent"
    },
    {
      "parameters": {
        "model": {
          "__rl": true,
          "value": "gpt-4.1",
          "mode": "list",
          "cachedResultName": "gpt-4.1"
        },
        "responsesApiEnabled": false,
        "options": {
          "maxTokens": 650,
          "temperature": 0.3
        }
      },
      "type": "@n8n/n8n-nodes-langchain.lmChatOpenAi",
      "typeVersion": 1.3,
      "position": [
        2880,
        736
      ],
      "id": "0c289450-b262-4b16-8a7d-e28ab7681e65",
      "name": "OpenAI Chat Model",
      "credentials": {
        "openAiApi": {
          "id": "EPBmvTYfgROzhEq9",
          "name": "OpenAi account"
        }
      }
    },
    {
      "parameters": {
        "sessionIdType": "customKey",
        "sessionKey": "={{ $('chat').item.json.body.sessionId }}",
        "contextWindowLength": 10
      },
      "type": "@n8n/n8n-nodes-langchain.memoryBufferWindow",
      "typeVersion": 1.3,
      "position": [
        1664,
        1360
      ],
      "id": "bf4b14b2-f5cc-4043-9cb0-f0476283f040",
      "name": "Simple Memory1"
    },
    {
      "parameters": {
        "toolDescription": "Este xml sacado de  cuenta con el catalogo de Winkle. Cuando recomiendas un producto o hables de un producto, SIEMPRE debes tener en cuenta que estos son TODOS LOS PRODUCTOS DISPONIBLES, no inventes mas productos. Contesta SOLO con el nombre de los productos, no las url",
        "url": "https://winkle.shop/productos-sitemap.xml",
        "sendQuery": true,
        "queryParameters": {
          "parameters": [
            {
              "name": "User-Agent",
              "value": "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/120.0.0.0 Safari/537.36"
            },
            {
              "name": "Accept",
              "value": "text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8"
            },
            {
              "name": "Accept-Language",
              "value": "es-ES,es;q=0.9,en;q=0.8"
            }
          ]
        },
        "options": {}
      },
      "type": "n8n-nodes-base.httpRequestTool",
      "typeVersion": 4.3,
      "position": [
        3104,
        336
      ],
      "id": "c2abdc51-1851-4c0e-9f0b-3e3903beedea",
      "name": "Catalogo winkle xml1"
    },
    {
      "parameters": {
        "descriptionType": "manual",
        "toolDescription": "En esta tabla tienes los valores de las fichas tecnicas de los filamentos - por material - de winkle",
        "documentId": {
          "__rl": true,
          "value": "1n_-IRLJKwfmQblhNjicEjJScqhCXEKH42DzSJ1A64rg",
          "mode": "list",
          "cachedResultName": "Documentos Técnicos",
          "cachedResultUrl": "https://docs.google.com/spreadsheets/d/1n_-IRLJKwfmQblhNjicEjJScqhCXEKH42DzSJ1A64rg/edit?usp=drivesdk"
        },
        "sheetName": {
          "__rl": true,
          "value": "gid=0",
          "mode": "list",
          "cachedResultName": "ficha_tecnica",
          "cachedResultUrl": "https://docs.google.com/spreadsheets/d/1n_-IRLJKwfmQblhNjicEjJScqhCXEKH42DzSJ1A64rg/edit#gid=0"
        },
        "options": {}
      },
      "type": "n8n-nodes-base.googleSheetsTool",
      "typeVersion": 4.7,
      "position": [
        3280,
        336
      ],
      "id": "a8a1e45d-0ab3-4788-9091-4b451de0e0b2",
      "name": "ficha_tecnica",
      "credentials": {
        "googleSheetsOAuth2Api": {
          "id": "5AL0KPkfdvFFUXdP",
          "name": "Google Sheets account"
        }
      }
    },
    {
      "parameters": {
        "jsCode": "const data = $json; // Lo que viene del Text Classifier\n\nif (Array.isArray(data)) {\n  // Si ya es un array, lo envolvemos correctamente\n  return data.map(item => ({ json: item }));\n} else {\n  // Si es un objeto único, lo convertimos en un array con 1 item\n  return [{ json: data }];\n}\n"
      },
      "type": "n8n-nodes-base.code",
      "typeVersion": 2,
      "position": [
        2832,
        512
      ],
      "id": "943452ba-0e17-43f2-bfa4-f72aa31b3431",
      "name": "Formateo18"
    },
    {
      "parameters": {
        "model": {
          "__rl": true,
          "value": "gpt-4.1-mini",
          "mode": "list",
          "cachedResultName": "gpt-4.1-mini"
        },
        "responsesApiEnabled": false,
        "options": {
          "temperature": 0.2
        }
      },
      "type": "@n8n/n8n-nodes-langchain.lmChatOpenAi",
      "typeVersion": 1.3,
      "position": [
        -480,
        816
      ],
      "id": "bd7548bd-4579-4d70-9842-984f1e957f81",
      "name": "OpenAI Chat Model2",
      "credentials": {
        "openAiApi": {
          "id": "EPBmvTYfgROzhEq9",
          "name": "OpenAi account"
        }
      }
    },
    {
      "parameters": {
        "jsonSchemaExample": "{\n\t\"pass\": [\"True | False\"]\n}"
      },
      "type": "@n8n/n8n-nodes-langchain.outputParserStructured",
      "typeVersion": 1.3,
      "position": [
        -272,
        816
      ],
      "id": "165da75e-f422-441c-bd86-2f2b9e9f0836",
      "name": "Structured Output Parser"
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
                  "typeValidation": "loose",
                  "version": 2
                },
                "conditions": [
                  {
                    "leftValue": "={{ $('filtro').item.json.output.pass[0] }}\n",
                    "rightValue": "True",
                    "operator": {
                      "type": "string",
                      "operation": "regex"
                    },
                    "id": "fbe8df78-f44d-4a36-abf0-9ad75ed43ccd"
                  }
                ],
                "combinator": "and"
              },
              "renameOutput": true,
              "outputKey": "True"
            },
            {
              "conditions": {
                "options": {
                  "caseSensitive": true,
                  "leftValue": "",
                  "typeValidation": "loose",
                  "version": 2
                },
                "conditions": [
                  {
                    "id": "9c2079f1-fa70-4ff2-a97c-835efaa08aff",
                    "leftValue": "={{ $('filtro').item.json.output.pass[0] }}\n",
                    "rightValue": "False",
                    "operator": {
                      "type": "string",
                      "operation": "regex"
                    }
                  }
                ],
                "combinator": "and"
              },
              "renameOutput": true,
              "outputKey": "False"
            }
          ]
        },
        "looseTypeValidation": true,
        "options": {}
      },
      "type": "n8n-nodes-base.switch",
      "typeVersion": 3.3,
      "position": [
        -48,
        528
      ],
      "id": "0fd34b17-c92f-47ef-b1e7-5d3db6ea66a0",
      "name": "Switch"
    },
    {
      "parameters": {
        "assignments": {
          "assignments": [
            {
              "id": "79614954-c715-4e4a-892a-4b9ffe77b6c4",
              "name": "output",
              "value": "Estoy aqui para ayudarte con alguna duda de Filamentos de Winkle, o alguna cuestión relacionada con pedidos del cliente, ¿Te puedo ayudar en algo mas?",
              "type": "string"
            }
          ]
        },
        "options": {}
      },
      "type": "n8n-nodes-base.set",
      "typeVersion": 3.4,
      "position": [
        1616,
        1600
      ],
      "id": "ca60bbd1-2799-479d-8ca7-7c53d86bad55",
      "name": "Edit Fields"
    },
    {
      "parameters": {
        "promptType": "define",
        "text": "={{ $('chat').item.json.body.chatInput }}",
        "hasOutputParser": true,
        "options": {
          "systemMessage": "✅ PROMPT DEFINITIVO PARA CLASIFICAR MENSAJES (solo True/False)\n\nRol:\nEres un Clasificador de Intención para el chatbot de Winkle.\n\nObjetivo:\nDeterminar, para cada mensaje del usuario, si el chatbot debe permitir contestar o debe bloquear el mensaje.\n\nIMPORTANTE:\nDebes devolver exclusivamente el valor True o False en el campo pass del output.\nNo puedes devolver nada más.\nNo puedes escribir explicaciones, frases adicionales ni texto libre.\nSolo la palabra True o False.\n\n✔️ Temas Permitidos (→ devolver True)\n\nConsidera el mensaje permitido si trata de:\n\n1. Consultas típicas de un cliente de Winkle\n\nPedidos\n\nEnvíos y logística\n\nDevoluciones\n\nCambios\n\nGarantías\n\nPagos y facturas\n\nProblemas con productos\n\nConsultas comerciales\n\nDisponibilidad, precios o detalles del catálogo\n\nAtención al cliente en general\n\n2. Filamentos 3D/Resina/Productos relacionados con impresion 3D y temas técnicos relacionados\n\nTipos de Resina/Productos relacionados con impresion 3D\n\nParámetros de impresión\n\nCompatibilidad\n\nPropiedades técnicas\n\nProblemas de impresión\n\n🧠 Regla de uso del contexto y memoria\n\nDebes usar la memoria del sistema y el contexto previo de la conversación.\nSi el último mensaje es ambiguo, pero la conversación previa o la memoria muestra que se habla de un tema permitido, debes devolver True.\n\nEjemplo:\nMensaje: “¿Y el otro?”\nSi previamente hablaban de PLA → devuelve True.\n\n❌ Temas NO Permitidos (→ devolver False)\n\nDevuelve False si el mensaje está fuera del ámbito del chatbot, incluyendo:\n\nRutinas de gimnasio\n\nMedicina\n\nFinanzas\n\nTutorías escolares\n\nProblemas personales\n\nPreguntas ajenas a Winkle\n\nPolítica, religión, temas sensibles\n\nOpiniones personales\n\nCualquier otro tema que no trate sobre Winkle, su catálogo o filamentos 3D\n\n🧩 Regla Final\n\nEl valor del campo pass debe ser:\n\nTrue → si el mensaje es sobre soporte al cliente de Winkle o sobre filamentos 3D o si el contexto previo/memoria indica que la conversación sí pertenece al ámbito permitido.\n\nFalse → si el mensaje no tiene ninguna relación con Winkle o filamentos 3D, sin excepciones.\n\n⚠️ MUY IMPORTANTE — FORMA DE RESPONDER\n\nDebes generar como salida solo el valor para el campo pass, es decir:\n\nTrue\n\n\no\n\nFalse\n\n\nNada más. Sin texto adicional."
        }
      },
      "type": "@n8n/n8n-nodes-langchain.agent",
      "typeVersion": 3,
      "position": [
        -400,
        528
      ],
      "id": "1421ca5d-53d8-4066-b4db-e9c12c5c00c4",
      "name": "filtro"
    },
    {
      "parameters": {
        "operation": "append",
        "documentId": {
          "__rl": true,
          "value": "1AoaykyVTjFzRmPiJh3CbO3nTUyyuGq6WtLOvRGg2CwM",
          "mode": "list",
          "cachedResultName": "Prompts",
          "cachedResultUrl": "https://docs.google.com/spreadsheets/d/1AoaykyVTjFzRmPiJh3CbO3nTUyyuGq6WtLOvRGg2CwM/edit?usp=drivesdk"
        },
        "sheetName": {
          "__rl": true,
          "value": 1579569901,
          "mode": "list",
          "cachedResultName": "Test Clientes",
          "cachedResultUrl": "https://docs.google.com/spreadsheets/d/1AoaykyVTjFzRmPiJh3CbO3nTUyyuGq6WtLOvRGg2CwM/edit#gid=1579569901"
        },
        "columns": {
          "mappingMode": "defineBelow",
          "value": {
            "input": "={{ $('chat').item.json.body.chatInput }}",
            "id": "={{ $('chat').item.json.body.sessionId }}",
            "link": "={{ $json.link }}",
            "email": "={{ $('chat').item.json.body.email }}"
          },
          "matchingColumns": [
            "input"
          ],
          "schema": [
            {
              "id": "id",
              "displayName": "id",
              "required": false,
              "defaultMatch": true,
              "display": true,
              "type": "string",
              "canBeUsedToMatch": true,
              "removed": false
            },
            {
              "id": "email",
              "displayName": "email",
              "required": false,
              "defaultMatch": false,
              "display": true,
              "type": "string",
              "canBeUsedToMatch": true,
              "removed": false
            },
            {
              "id": "link",
              "displayName": "link",
              "required": false,
              "defaultMatch": false,
              "display": true,
              "type": "string",
              "canBeUsedToMatch": true,
              "removed": false
            },
            {
              "id": "comentarios",
              "displayName": "comentarios",
              "required": false,
              "defaultMatch": false,
              "display": true,
              "type": "string",
              "canBeUsedToMatch": true,
              "removed": true
            },
            {
              "id": "input",
              "displayName": "input",
              "required": false,
              "defaultMatch": false,
              "display": true,
              "type": "string",
              "canBeUsedToMatch": true,
              "removed": false
            },
            {
              "id": "Explicación Imagen",
              "displayName": "Explicación Imagen",
              "required": false,
              "defaultMatch": false,
              "display": true,
              "type": "string",
              "canBeUsedToMatch": true,
              "removed": true
            },
            {
              "id": "output",
              "displayName": "output",
              "required": false,
              "defaultMatch": false,
              "display": true,
              "type": "string",
              "canBeUsedToMatch": true,
              "removed": true
            }
          ],
          "attemptToConvertTypes": false,
          "convertFieldsToString": false
        },
        "options": {}
      },
      "type": "n8n-nodes-base.googleSheets",
      "typeVersion": 4.7,
      "position": [
        848,
        1312
      ],
      "id": "83f89528-2bb5-44d1-bb4b-7f0594d1c3d5",
      "name": "Update Input Texto predefinido",
      "retryOnFail": true,
      "credentials": {
        "googleSheetsOAuth2Api": {
          "id": "5AL0KPkfdvFFUXdP",
          "name": "Google Sheets account"
        }
      }
    },
    {
      "parameters": {
        "assignments": {
          "assignments": [
            {
              "id": "716793bd-8b85-449e-b4a5-31051cfd5ee1",
              "name": "chatInput",
              "value": "={{ $('chat').item.json.body.chatInput }}",
              "type": "string"
            },
            {
              "id": "37455e13-ce96-470a-952f-43cab4686f66",
              "name": "sessionId",
              "value": "={{ $('chat').item.json.body.sessionId }}",
              "type": "string"
            }
          ]
        },
        "options": {}
      },
      "type": "n8n-nodes-base.set",
      "typeVersion": 3.4,
      "position": [
        320,
        1056
      ],
      "id": "8aae461d-0b6e-42f8-a2ab-9310dc2f75e5",
      "name": "Mapeo Chat"
    },
    {
      "parameters": {
        "jsCode": "// Accedemos al JSON del nodo anterior\nconst chatInput = $input.first().json.chatInput;\nconst sessionId = $input.first().json.sessionId;\n\n// Concatenamos ambos valores con un separador (puedes cambiarlo por lo que prefieras)\nconst link = `${sessionId} - ${chatInput}`;\n\n// Devolvemos un nuevo objeto con la propiedad 'link'\nreturn [\n  {\n    json: {\n      link: link\n    }\n  }\n];\n"
      },
      "type": "n8n-nodes-base.code",
      "typeVersion": 2,
      "position": [
        576,
        1136
      ],
      "id": "9c337b47-2b50-4246-ae19-7327fe8e5980",
      "name": "Generate Link Texto Predefinido"
    },
    {
      "parameters": {
        "httpMethod": "POST",
        "path": "3ca5032c-6292-4dd7-bf61-a304081ad912",
        "responseMode": "responseNode",
        "options": {}
      },
      "type": "n8n-nodes-base.webhook",
      "typeVersion": 2.1,
      "position": [
        -768,
        528
      ],
      "id": "a76d4094-ec15-4779-978a-2acc046fd08b",
      "name": "chat",
      "webhookId": "3ca5032c-6292-4dd7-bf61-a304081ad912"
    },
    {
      "parameters": {
        "descriptionType": "manual",
        "toolDescription": "En esta tabla tienes los valores de los parametros de impresion de los filamentos - por material - de winkle",
        "documentId": {
          "__rl": true,
          "value": "1n_-IRLJKwfmQblhNjicEjJScqhCXEKH42DzSJ1A64rg",
          "mode": "list",
          "cachedResultName": "Documentos Técnicos",
          "cachedResultUrl": "https://docs.google.com/spreadsheets/d/1n_-IRLJKwfmQblhNjicEjJScqhCXEKH42DzSJ1A64rg/edit?usp=drivesdk"
        },
        "sheetName": {
          "__rl": true,
          "value": 1778131786,
          "mode": "list",
          "cachedResultName": "parametros-de-impresion",
          "cachedResultUrl": "https://docs.google.com/spreadsheets/d/1n_-IRLJKwfmQblhNjicEjJScqhCXEKH42DzSJ1A64rg/edit#gid=1778131786"
        },
        "options": {}
      },
      "type": "n8n-nodes-base.googleSheetsTool",
      "typeVersion": 4.7,
      "position": [
        3472,
        384
      ],
      "id": "e398bdc8-4b82-42c7-9781-21040d3761f3",
      "name": "parametros de impresion",
      "credentials": {
        "googleSheetsOAuth2Api": {
          "id": "5AL0KPkfdvFFUXdP",
          "name": "Google Sheets account"
        }
      }
    },
    {
      "parameters": {
        "model": {
          "__rl": true,
          "mode": "list",
          "value": "gpt-4.1-mini"
        },
        "builtInTools": {},
        "options": {}
      },
      "type": "@n8n/n8n-nodes-langchain.lmChatOpenAi",
      "typeVersion": 1.3,
      "position": [
        3056,
        784
      ],
      "id": "4022f9a7-fb8d-495d-88da-51fd2321751d",
      "name": "fallback model",
      "credentials": {
        "openAiApi": {
          "id": "EPBmvTYfgROzhEq9",
          "name": "OpenAi account"
        }
      }
    },
    {
      "parameters": {
        "sendTo": "={{ /*n8n-auto-generated-fromAI-override*/ $fromAI('To', `transporte@winkle.shop -> problemas de envío, pedido no llega, dirección incorrecta)\n\nbackoffice@winkle.shop ->producto defectuoso, escalados generales\n\nfacturacion@ecotisa.com -> modificaciones de factura)\n\nana.manchado@winkle.shop -> distribuidores, compras al por mayor, operaciones extracomunitarias fuera de europa\n\nmateo.herrero@winkle.shop -> envíos y compras en Europa\n\ncomunicación@winkle.shop -> colaboraciones comerciales, marketing\n\n`, 'string') }}",
        "subject": "=[GENERACIÓN DE TICKET POR CHATBOT] {{ $fromAI('Subject', ``, 'string') }}",
        "message": "={{ /*n8n-auto-generated-fromAI-override*/ $fromAI('Message', ``, 'string') }}",
        "options": {
          "appendAttribution": false,
          "ccList": "daniel.castro@grupoecotisa.com, elia.rivero@winkle.shop",
          "senderName": "Chatbot Winkle"
        }
      },
      "type": "n8n-nodes-base.gmailTool",
      "typeVersion": 2.1,
      "position": [
        3424,
        736
      ],
      "id": "7c08717e-2edc-4187-a627-806343e94f7d",
      "name": "Envio Correo - Ticket1",
      "webhookId": "8104950e-6bb7-4475-a7e9-375dda0ec94f",
      "credentials": {
        "gmailOAuth2": {
          "id": "vWVvQjMZDfkwvnnd",
          "name": "Gmail account"
        }
      }
    }
  ],
  "connections": {
    "Mapeo Chat1": {
      "main": [
        [
          {
            "node": "Generate Link Texto1",
            "type": "main",
            "index": 0
          }
        ]
      ]
    },
    "Transcribe a recording1": {
      "main": [
        [
          {
            "node": "Mapeo Chat Audio1",
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
            "node": "Reconocimiento de Imagen1",
            "type": "main",
            "index": 0
          }
        ],
        [
          {
            "node": "Mapeo Chat1",
            "type": "main",
            "index": 0
          }
        ],
        [
          {
            "node": "Transcribe a recording1",
            "type": "main",
            "index": 0
          }
        ]
      ]
    },
    "Mapeo Chat Imagen1": {
      "main": [
        [
          {
            "node": "Generate Link Imagen1",
            "type": "main",
            "index": 0
          }
        ]
      ]
    },
    "Mapeo Chat Audio1": {
      "main": [
        [
          {
            "node": "Generate Link Audio1",
            "type": "main",
            "index": 0
          }
        ]
      ]
    },
    "Generate Link Imagen1": {
      "main": [
        [
          {
            "node": "Update Input Imagen1",
            "type": "main",
            "index": 0
          }
        ]
      ]
    },
    "Generate Link Texto1": {
      "main": [
        [
          {
            "node": "Update Input Texto1",
            "type": "main",
            "index": 0
          }
        ]
      ]
    },
    "Generate Link Audio1": {
      "main": [
        [
          {
            "node": "Update Input Audio1",
            "type": "main",
            "index": 0
          }
        ]
      ]
    },
    "Reconocimiento de Imagen1": {
      "main": [
        [
          {
            "node": "Mapeo Chat Imagen1",
            "type": "main",
            "index": 0
          }
        ]
      ]
    },
    "GPT 4.1 Mini1": {
      "ai_languageModel": [
        [
          {
            "node": "analizador",
            "type": "ai_languageModel",
            "index": 0
          }
        ]
      ]
    },
    "Update Input Imagen1": {
      "main": [
        [
          {
            "node": "analizador",
            "type": "main",
            "index": 0
          }
        ]
      ]
    },
    "Update Input Texto1": {
      "main": [
        [
          {
            "node": "analizador",
            "type": "main",
            "index": 0
          }
        ]
      ]
    },
    "Update Input Audio1": {
      "main": [
        [
          {
            "node": "analizador",
            "type": "main",
            "index": 0
          }
        ]
      ]
    },
    "GPT 4.1 MINI1": {
      "ai_languageModel": [
        [
          {
            "node": "Reconocimiento de Imagen1",
            "type": "ai_languageModel",
            "index": 0
          }
        ]
      ]
    },
    "Edit Fields2": {
      "main": [
        [
          {
            "node": "Update row in sheet",
            "type": "main",
            "index": 0
          }
        ]
      ]
    },
    "analizador": {
      "main": [
        [
          {
            "node": "Formateo18",
            "type": "main",
            "index": 0
          }
        ],
        [
          {
            "node": "Formateo18",
            "type": "main",
            "index": 0
          }
        ],
        [
          {
            "node": "Formateo18",
            "type": "main",
            "index": 0
          }
        ]
      ]
    },
    "OpenAI Chat Model": {
      "ai_languageModel": [
        [
          {
            "node": "AI Agent",
            "type": "ai_languageModel",
            "index": 0
          }
        ]
      ]
    },
    "Simple Memory1": {
      "ai_memory": [
        [
          {
            "node": "AI Agent",
            "type": "ai_memory",
            "index": 0
          },
          {
            "node": "filtro",
            "type": "ai_memory",
            "index": 0
          }
        ]
      ]
    },
    "Catalogo winkle xml1": {
      "ai_tool": [
        [
          {
            "node": "AI Agent",
            "type": "ai_tool",
            "index": 0
          }
        ]
      ]
    },
    "AI Agent": {
      "main": [
        [
          {
            "node": "Edit Fields2",
            "type": "main",
            "index": 0
          }
        ]
      ]
    },
    "ficha_tecnica": {
      "ai_tool": [
        [
          {
            "node": "AI Agent",
            "type": "ai_tool",
            "index": 0
          }
        ]
      ]
    },
    "Formateo18": {
      "main": [
        [
          {
            "node": "AI Agent",
            "type": "main",
            "index": 0
          }
        ]
      ]
    },
    "OpenAI Chat Model2": {
      "ai_languageModel": [
        [
          {
            "node": "filtro",
            "type": "ai_languageModel",
            "index": 0
          }
        ]
      ]
    },
    "Structured Output Parser": {
      "ai_outputParser": [
        [
          {
            "node": "filtro",
            "type": "ai_outputParser",
            "index": 0
          }
        ]
      ]
    },
    "Switch": {
      "main": [
        [
          {
            "node": "Switch1",
            "type": "main",
            "index": 0
          }
        ],
        [
          {
            "node": "Mapeo Chat",
            "type": "main",
            "index": 0
          }
        ]
      ]
    },
    "Edit Fields": {
      "main": [
        [
          {
            "node": "Edit Fields2",
            "type": "main",
            "index": 0
          }
        ]
      ]
    },
    "filtro": {
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
    "Update Input Texto predefinido": {
      "main": [
        [
          {
            "node": "Edit Fields",
            "type": "main",
            "index": 0
          }
        ]
      ]
    },
    "Mapeo Chat": {
      "main": [
        [
          {
            "node": "Generate Link Texto Predefinido",
            "type": "main",
            "index": 0
          }
        ]
      ]
    },
    "Generate Link Texto Predefinido": {
      "main": [
        [
          {
            "node": "Update Input Texto predefinido",
            "type": "main",
            "index": 0
          }
        ]
      ]
    },
    "Update row in sheet": {
      "main": [
        [
          {
            "node": "Respond to Webhook1",
            "type": "main",
            "index": 0
          }
        ]
      ]
    },
    "chat": {
      "main": [
        [
          {
            "node": "filtro",
            "type": "main",
            "index": 0
          }
        ]
      ]
    },
    "parametros de impresion": {
      "ai_tool": [
        [
          {
            "node": "AI Agent",
            "type": "ai_tool",
            "index": 0
          }
        ]
      ]
    },
    "fallback model": {
      "ai_languageModel": [
        [
          {
            "node": "AI Agent",
            "type": "ai_languageModel",
            "index": 1
          }
        ]
      ]
    },
    "Envio Correo - Ticket1": {
      "ai_tool": [
        [
          {
            "node": "AI Agent",
            "type": "ai_tool",
            "index": 0
          }
        ]
      ]
    }
  },
  "settings": {
    "executionOrder": "v1"
  },
  "staticData": null,
  "meta": {
    "templateCredsSetupCompleted": true
  },
  "pinData": {},
  "versionId": "1daf51f7-c2d6-4a62-9c68-3be64e64eb88",
  "versionCounter": 36,
  "triggerCount": 1,
  "shared": [
    {
      "updatedAt": "2025-12-03T10:58:40.842Z",
      "createdAt": "2025-12-03T10:58:40.842Z",
      "role": "workflow:owner",
      "workflowId": "NyC6Z3by7wRaLBYM",
      "projectId": "FiR0bEYqdioEW9qZ",
      "project": {
        "updatedAt": "2025-12-03T10:31:49.831Z",
        "createdAt": "2025-12-03T10:22:46.976Z",
        "id": "FiR0bEYqdioEW9qZ",
        "name": "Daniel de Castro <datos@grupoecotisa.com>",
        "type": "personal",
        "icon": null,
        "description": null,
        "projectRelations": [
          {
            "updatedAt": "2025-12-03T10:22:46.976Z",
            "createdAt": "2025-12-03T10:22:46.976Z",
            "userId": "a3765ada-8e6d-4459-82da-4745fdbb7508",
            "projectId": "FiR0bEYqdioEW9qZ",
            "user": {
              "updatedAt": "2026-01-09T10:46:55.747Z",
              "createdAt": "2025-12-03T10:22:46.976Z",
              "id": "a3765ada-8e6d-4459-82da-4745fdbb7508",
              "email": "datos@grupoecotisa.com",
              "firstName": "Daniel",
              "lastName": "de Castro",
              "personalizationAnswers": {
                "version": "v4",
                "personalization_survey_submitted_at": "2025-12-03T10:32:11.075Z",
                "personalization_survey_n8n_version": "1.120.1",
                "companyType": "personal",
                "reportedSource": "google"
              },
              "settings": {
                "easyAIWorkflowOnboarded": true,
                "firstSuccessfulWorkflowId": "NyC6Z3by7wRaLBYM",
                "userActivated": true,
                "userActivatedAt": 1764765878756,
                "npsSurvey": {
                  "waitingForResponse": true,
                  "ignoredCount": 2,
                  "lastShownAt": 1767615169606
                }
              },
              "disabled": false,
              "mfaEnabled": false,
              "lastActiveAt": "2026-01-08",
              "isPending": false
            }
          }
        ]
      }
    }
  ],
  "tags": [
    {
      "updatedAt": "2025-12-03T10:58:30.804Z",
      "createdAt": "2025-12-03T10:58:30.804Z",
      "id": "AfEjPpu06UhmQi4r",
      "name": "Automatic-process"
    },
    {
      "updatedAt": "2025-12-03T10:58:30.805Z",
      "createdAt": "2025-12-03T10:58:30.805Z",
      "id": "IteeStwJ8lAwCyiY",
      "name": "Chatbot"
    },
    {
      "updatedAt": "2025-12-03T10:58:30.809Z",
      "createdAt": "2025-12-03T10:58:30.809Z",
      "id": "BeLwjeQb16ofaV7u",
      "name": "Winkle"
    }
  ]
}