# jmeter-backend

Plano de teste de carga com Apache JMeter para a API REST backend-api-nodejs, cobrindo GET e POST com 10 usuários simultâneos.

## O que é

Teste de performance construído com Apache JMeter 5.6.3 validando o comportamento da API sob carga. O plano simula 10 usuários simultâneos executando 5 loops cada, totalizando 100 requisições distribuídas entre GET e POST.

## Stack

- Apache JMeter 5.6.3
- Java 21
- API testada: backend-api-nodejs (Node.js + MongoDB)

## Estrutura

```
jmeter-backend/
└── backend-load-test.jmx    # Plano de teste JMeter
```

## Como executar

**Interface gráfica:**
```bash
# Abre o JMeter
C:\Users\ivanj\apache-jmeter-5.6.3\apache-jmeter-5.6.3\bin\jmeter.bat

# Abre o arquivo backend-load-test.jmx e clica em Play
```

**Linha de comando:**
```bash
jmeter -n -t backend-load-test.jmx -l resultado.jtl
```

## Configuração do plano

| Configuração | Valor |
|---|---|
| Threads (usuários) | 10 |
| Ramp-Up Period | 10s |
| Loop Count | 5 |
| Total de requisições | 100 |

## Endpoints testados

| Endpoint | Método | O que valida |
|---|---|---|
| /api/recommendation | GET | Listagem sob carga |
| /api/recommendation | POST | Criação sob carga |

## Resultados obtidos

| Endpoint | Amostras | Média | Mín | Máx | Erro % | Throughput |
|---|---|---|---|---|---|---|
| GET - Listar Recomendações | 50 | 34ms | 20ms | 194ms | 0.00% | 5.5/sec |
| POST - Criar Recomendação | 50 | 7ms | 4ms | 78ms | 0.00% | 5.7/sec |
| TOTAL | 100 | 20ms | 4ms | 194ms | 0.00% | 11.1/sec |

## Pré-requisitos

- Java 8+
- Backend rodando em `http://127.0.0.1:3001`
