# API - Tests - Postman

## 1. Visão geral do projeto

Este projeto tem como objetivo demonstrar conhecimentos fundamentais de Quality Assurance (QA) e testes de APIs REST, utilizando o Postman e a API de demonstração JSONPlaceholder.

O projeto inclui a criação e execução de pedidos HTTP, validação de respostas, testes automatizados com scripts do Postman, execução de coleções através do Collection Runner e análise de cenários positivos e negativos.

O objetivo é praticar competências aplicáveis a uma função de QA Junior, incluindo desenho de testes, validação de requisitos, análise de resultados e documentação de limitações.

## 2. Objetivos

- Testar endpoints de uma API REST.
- Praticar os métodos HTTP GET, POST, PUT e DELETE.
- Validar códigos de estado HTTP e conteúdo das respostas.
- Criar asserções automatizadas com scripts do Postman.
- Executar uma coleção completa através do Collection Runner.
- Comparar resultados esperados com resultados observados.
- Explorar cenários positivos e negativos.
- Analisar falhas de teste sem assumir que representam defeitos confirmados.
- Documentar resultados e limitações da API utilizada.

## 3. Ferramentas utilizadas

- **Postman:** criação e execução de pedidos HTTP, organização de coleções e automatização de verificações.
- **JSONPlaceholder:** API REST de demonstração utilizada para praticar testes.
- **GitHub:** documentação e publicação do portfólio de QA.

## 4. Métodos HTTP testados

| Método | Objetivo | Cenário de teste |
|---|---|---|
| GET | Consultar recursos | Consultar utilizadores existentes e inexistentes |
| POST | Enviar dados para criação de recursos | Enviar dados válidos e explorar dados inválidos |
| PUT | Atualizar um recurso | Enviar dados atualizados para um utilizador |
| DELETE | Solicitar a eliminação de um recurso | Enviar um pedido de eliminação de um utilizador |

**Nota:** A JSONPlaceholder simula operações de criação, atualização e eliminação. As respostas recebidas não garantem que as alterações sejam guardadas de forma persistente.

## 5. Cenários de teste e resultados observados

| Cenário | Resultado esperado | Resultado observado |
|---|---|---|
| Consultar um utilizador existente | HTTP 200 e ID correspondente | HTTP 200; ID correspondente |
| Consultar um utilizador inexistente | Resposta compatível com o comportamento esperado para um recurso inexistente | HTTP 404 no cenário testado |
| Criar utilizador com dados válidos | HTTP 201 e dados correspondentes | HTTP 201; dados enviados devolvidos na resposta |
| Enviar email inválido | Rejeição, de acordo com o requisito definido para o teste | HTTP 201; email inválido devolvido |
| Atualizar utilizador (PUT) | Resposta com os dados atualizados e status compatível com o contrato esperado | Resposta de atualização validada com testes no Postman |
| Eliminar utilizador (DELETE) | Resposta compatível com o comportamento esperado para a operação | HTTP 200; resposta representada por um objeto JSON vazio (`{}`) |

**Nota:** Os resultados correspondem aos cenários executados na JSONPlaceholder. Como esta API é de demonstração, os resultados de PUT e DELETE não comprovam a persistência das alterações nem a eliminação permanente do recurso.

## 6. Análise de cenário negativo — Email inválido

**Requisito hipotético:** A API deve rejeitar endereços de email com formato inválido.

**Dados de entrada:**

`maria-sem-email`

**Resultado esperado:** A API deve rejeitar o pedido, por exemplo, com HTTP 400 ou HTTP 422, conforme o contrato definido para o exercício.

**Resultado observado:** A API devolveu HTTP 201 Created e incluiu na resposta o email inválido enviado.

**Resultado do teste automatizado:** FAIL, porque o código de estado recebido não corresponde ao resultado esperado no teste.

**Conclusão:** O comportamento observado não corresponde ao requisito hipotético definido para este exercício. No entanto, como a JSONPlaceholder é uma API de demonstração e não implementa necessariamente esta regra de validação, o resultado não constitui, por si só, evidência de um defeito confirmado num sistema real.

Este cenário demonstra a utilização de testes negativos, a comparação entre resultados esperados e obtidos e a análise crítica dos resultados de execução.

## 7. Testes automatizados e execução da coleção

Foram criados scripts de teste no Postman para verificar:

- Códigos de estado HTTP.
- Correspondência entre os dados esperados e os dados devolvidos.
- Presença e tipo de campos nas respostas JSON.
- Formato básico de endereços de email.
- Correspondência entre os dados enviados e os dados devolvidos.
- Respostas observadas nos cenários de atualização e eliminação.

A coleção foi executada através do **Postman Collection Runner**, permitindo executar vários pedidos e analisar os resultados em conjunto.

**Resultados da execução:**

- **Testes aprovados:** 15
- **Testes falhados:** 1

O teste falhado foi `POST - Invalid Email - Expected Rejection`, que verifica o requisito hipotético de rejeição de emails inválidos.

Os resultados refletem o comportamento observado na API de demonstração e as verificações definidas para este projeto.

## 8. Principais aprendizagens

- Métodos HTTP e funcionamento básico de APIs REST.
- Validação de códigos de estado e respostas JSON.
- Criação de asserções automatizadas no Postman.
- Testes positivos e negativos.
- Execução de coleções com o Collection Runner.
- Análise de resultados PASS e FAIL.
- Comparação entre requisitos e comportamento observado.
- Documentação de cenários de teste e limitações técnicas.
- Distinção entre uma falha de teste e um defeito confirmado.

## 9. Limitações do projeto

Este projeto utiliza a JSONPlaceholder, uma API pública de demonstração. O seu comportamento não deve ser interpretado como representativo de todas as APIs reais.

As operações de criação, atualização e eliminação são simuladas e não garantem persistência real. Além disso, o cenário de rejeição de email inválido baseia-se num requisito hipotético criado para fins de aprendizagem.

Os resultados e conclusões devem, por isso, ser interpretados no contexto desta API e dos objetivos de aprendizagem definidos.

