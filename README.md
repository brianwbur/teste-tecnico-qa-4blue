# Teste Técnico QA Tester - 4blue

## Objetivo
Este repositório contém a documentação dos problemas identificados no microssistema disponibilizado para o teste técnico de QA Tester, conforme solicitado no enunciado.

## Ambiente avaliado
- Tela de Login
- Tela de Criação de Conta
- Tela de Sucesso

## Metodologia
Foi realizada exploração livre da aplicação, com foco em:
- bugs funcionais
- inconsistências de experiência do usuário
- problemas básicos de segurança
- validação de campos
- fluxo de autenticação e cadastro

## Bugs encontrados

---

## Bug 01: Campo de e-mail no login aceita valores inválidos

**Descrição:**  
O campo de e-mail na tela de login aceita textos sem formato válido de e-mail, como sequências aleatórias de caracteres, sem exigir estrutura mínima como `texto@dominio.com`.

**Passos para reproduzir:**  
1. Acessar a tela de login.  
2. No campo e-mail, digitar um valor inválido, por exemplo: `jkahsvdbkhjiqasvdeb`.  
3. Preencher o campo de senha.  
4. Tentar realizar o login.

**Resultado atual:**  
O sistema aceita um valor que não possui formato válido de e-mail.

**Resultado esperado:**  
O sistema deve validar o formato do e-mail e impedir o envio de valores inválidos.

**Severidade:** Alto  
**Prioridade:** Alta

---

## Bug 02: Campo nome aceita números

**Descrição:**  
O campo nome na criação de conta está aceitando números, o que compromete a consistência e a qualidade dos dados cadastrados.

**Passos para reproduzir:**  
1. Acessar a tela de criação de conta.  
2. No campo nome, inserir um valor contendo números, por exemplo: `Brian123`.  
3. Preencher os demais campos e concluir o cadastro.

**Resultado atual:**  
O sistema aceita números no campo nome.

**Resultado esperado:**  
O campo nome deve aceitar apenas caracteres válidos para nomes de pessoa, conforme a regra definida pelo negócio.

**Severidade:** Médio  
**Prioridade:** Média

---

## Bug 03: Campo telefone aceita letras, não possui máscara e não possui limite

**Descrição:**  
O campo telefone permite inserir letras, não aplica máscara de formatação e não limita a quantidade de caracteres.

**Passos para reproduzir:**  
1. Acessar a tela de criação de conta.  
2. No campo telefone, inserir letras ou uma sequência extensa de caracteres.  
3. Finalizar o cadastro.

**Resultado atual:**  
O sistema aceita conteúdo inválido no telefone, sem qualquer controle de formato ou tamanho.

**Resultado esperado:**  
O campo telefone deve aceitar apenas números, aplicar máscara adequada e limitar a quantidade de caracteres conforme o padrão esperado.

**Severidade:** Médio  
**Prioridade:** Média

---

## Bug 04: Boxes de texto estão desalinhadas

**Descrição:**  
Há inconsistência visual no alinhamento dos campos/textboxes da interface, prejudicando a experiência do usuário e a percepção de qualidade da aplicação.

**Passos para reproduzir:**  
1. Acessar as telas do sistema.  
2. Observar o posicionamento visual dos campos e caixas de texto.

**Resultado atual:**  
Os elementos visuais apresentam desalinhamento.

**Resultado esperado:**  
Todos os campos devem seguir um padrão visual consistente, com alinhamento adequado.

**Severidade:** Baixo  
**Prioridade:** Baixa

---

## Bug 05: Sistema permite criar conta sem caractere especial na senha

**Descrição:**  
O cadastro é concluído mesmo quando a senha não possui caractere especial, indicando ausência de validação de complexidade.

**Passos para reproduzir:**  
1. Acessar a tela de criação de conta.  
2. Preencher os campos obrigatórios.  
3. Informar uma senha sem caractere especial.  
4. Concluir o cadastro.

**Resultado atual:**  
A conta é criada com senha sem caractere especial.

**Resultado esperado:**  
O sistema deve bloquear o cadastro e informar claramente os requisitos mínimos da senha, caso a política exija caractere especial.

**Severidade:** Alto  
**Prioridade:** Alta

---

## Bug 06: Sistema permite criar conta sem preencher nenhum campo

**Descrição:**  
É possível criar uma conta sem preencher os campos do formulário, e esse usuário fica registrado e apto para autenticação posterior.

**Passos para reproduzir:**  
1. Acessar a tela de criação de conta.  
2. Deixar todos os campos em branco.  
3. Clicar para criar conta.

**Resultado atual:**  
O sistema cria a conta mesmo sem qualquer dado preenchido.

**Resultado esperado:**  
O sistema deve impedir a criação da conta e exibir mensagens de validação para os campos obrigatórios.

**Severidade:** Crítico  
**Prioridade:** Alta

---

## Bug 07: Sistema permite criar conta com senhas diferentes entre si

**Descrição:**  
O sistema conclui o cadastro mesmo quando os campos de senha e confirmação de senha possuem valores divergentes.

**Passos para reproduzir:**  
1. Acessar a tela de criação de conta.  
2. Preencher os demais campos.  
3. Informar uma senha no campo senha.  
4. Informar um valor diferente no campo de confirmação de senha.  
5. Concluir o cadastro.

**Resultado atual:**  
A conta é criada mesmo com senhas não coincidentes.

**Resultado esperado:**  
O sistema deve impedir o cadastro e informar que os campos de senha precisam ser idênticos.

**Severidade:** Crítico  
**Prioridade:** Alta

---

## Bug 08: Erro exibido no canto inferior direito após o login

**Descrição:**  
Após realizar login, é exibida uma mensagem de erro no canto inferior direito da tela, indicando falha no fluxo ou tratamento inadequado de exceções.

**Passos para reproduzir:**  
1. Acessar a tela de login.  
2. Informar credenciais válidas.  
3. Realizar login.  
4. Observar o canto inferior direito da tela.

**Resultado atual:**  
Uma mensagem de erro é exibida logo após o login.

**Resultado esperado:**  
Após login bem-sucedido, o sistema deve redirecionar o usuário sem apresentar mensagens de erro indevidas.

**Severidade:** Alto  
**Prioridade:** Alta

---

## Bug 09: Dados das contas ficam expostos no console do navegador

**Descrição:**  
Informações das contas cadastradas estão sendo exibidas no console do navegador, caracterizando exposição indevida de dados sensíveis e falha básica de segurança.

**Passos para reproduzir:**  
1. Acessar o sistema.  
2. Abrir o console do navegador.  
3. Criar uma conta ou realizar ações relacionadas ao cadastro/login.  
4. Observar os dados exibidos no console.

**Resultado atual:**  
Dados de contas e usuários ficam visíveis no console.

**Resultado esperado:**  
O sistema não deve expor dados sensíveis no console do navegador.

**Severidade:** Crítico  
**Prioridade:** Alta

---

## Bug 10: Login permite acesso sem informar credenciais

**Descrição:**  
O fluxo de login permite acesso mesmo sem preenchimento das informações, especialmente quando existe uma conta criada anteriormente sem dados válidos.

**Passos para reproduzir:**  
1. Criar uma conta sem preencher dados, caso o sistema permita.  
2. Acessar a tela de login.  
3. Deixar os campos vazios.  
4. Tentar entrar no sistema.

**Resultado atual:**  
O sistema permite login sem credenciais válidas.

**Resultado esperado:**  
O sistema deve exigir credenciais válidas e impedir login com campos vazios.

**Severidade:** Crítico  
**Prioridade:** Alta

---

## Bug 11: Sistema permite criar senha com menos de 8 caracteres

**Descrição:**  
O cadastro aceita senhas com menos de 8 caracteres, contrariando uma política mínima comum de segurança.

**Passos para reproduzir:**  
1. Acessar a tela de criação de conta.  
2. Preencher os campos necessários.  
3. Informar uma senha com menos de 8 caracteres.  
4. Finalizar o cadastro.

**Resultado atual:**  
A conta é criada com senha curta.

**Resultado esperado:**  
O sistema deve impedir o cadastro e exigir senha com no mínimo 8 caracteres.

**Severidade:** Alto  
**Prioridade:** Alta

---

## Bug 12: Sistema permite criar contas duplicadas com os mesmos dados

**Descrição:**  
É possível cadastrar mais de uma conta com os mesmos dados já utilizados anteriormente, indicando ausência de validação de unicidade.

**Passos para reproduzir:**  
1. Criar uma conta com um conjunto de dados válidos.  
2. Retornar à tela de criação de conta.  
3. Repetir exatamente os mesmos dados.  
4. Concluir o cadastro novamente.

**Resultado atual:**  
O sistema cria múltiplas contas com os mesmos dados.

**Resultado esperado:**  
O sistema deve impedir duplicidade de cadastro, principalmente para campos únicos como e-mail.

**Severidade:** Alto  
**Prioridade:** Alta

---

## Quais 2 bugs eu corrigiria primeiro e por quê?

### 1. Bug 10: Login permite acesso sem informar credenciais
Eu corrigiria este bug primeiro porque ele compromete diretamente a segurança e a autenticação do sistema. Permitir acesso sem validação adequada quebra a regra mais básica de controle de acesso e pode permitir uso indevido da aplicação.

### 2. Bug 09: Dados das contas ficam expostos no console do navegador
Esse seria o segundo bug priorizado, pois representa exposição de dados sensíveis. Além do risco de segurança, esse comportamento pode gerar vazamento de informações de usuários e comprometer a confiabilidade do sistema.

## Justificativa da priorização
Ambos os problemas impactam segurança, privacidade e integridade do sistema, sendo mais graves do que inconsistências visuais ou validações de formato. Corrigir esses pontos primeiro reduz o maior risco técnico e de negócio.

## Sugestões de melhoria

1. Implementar validação de campos no front-end e no back-end.
2. Exibir mensagens de erro claras e orientativas para o usuário.
3. Definir política de senha com critérios explícitos na interface.
4. Aplicar máscara e validação de formato em campos como telefone e e-mail.
5. Impedir duplicidade de cadastro com validação de unicidade do e-mail.
6. Revisar tratamento de logs para evitar exposição de dados sensíveis.
7. Melhorar alinhamento visual e padronização dos componentes da interface.
8. Bloquear envio de formulários com campos obrigatórios vazios.

## Observação final
Os bugs foram classificados considerando impacto funcional, risco de segurança, experiência do usuário e prioridade de correção dentro de um cenário real de produto.
