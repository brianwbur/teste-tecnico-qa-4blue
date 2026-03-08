# Teste Técnico QA Tester - 4blue

## 1. Objetivo

Este repositório contém a documentação dos problemas identificados no microssistema web disponibilizado para o teste técnico de QA Tester. A análise contempla falhas funcionais, problemas básicos de segurança, inconsistências de experiência do usuário, sugestões de melhoria e uma proposta de automação para validação dos cenários encontrados.

## 2. Escopo analisado

Foram avaliadas as seguintes telas:
- Login
- Criação de conta
- Sucesso

## 3. Critérios adotados na análise

A análise foi realizada com foco em:
- funcionamento dos fluxos principais
- validação de campos
- autenticação e cadastro
- segurança básica
- usabilidade
- consistência visual
- experiência do usuário

## 4. Bugs encontrados

## Bug 01. Campo de e-mail no login aceita valores sem formato válido de e-mail

**Descrição:**  
O campo de e-mail na tela de login aceita textos sem formato válido de e-mail. Por exemplo, ao informar apenas uma sequência aleatória de caracteres, o sistema não bloqueia o valor inserido.

**Passos para reproduzir:**  
1. Acessar a tela de login.  
2. Informar no campo e-mail o valor `4blue.com`.  
3. Preencher ou não o campo senha.  
4. Tentar prosseguir no fluxo.

**Resultado atual:**  
O sistema aceita valor sem formato válido de e-mail.

**Resultado esperado:**  
O sistema deve validar o formato do e-mail e aceitar apenas valores no padrão adequado, como `usuario@dominio.com`.

**Severidade:** Alto  
**Prioridade:** Alta

---

## Bug 02. Campo nome aceita números

**Descrição:**  
O campo nome permite a entrada de números, comprometendo a qualidade e a consistência dos dados cadastrados.

**Passos para reproduzir:**  
1. Acessar a tela de criação de conta.  
2. Inserir no campo nome um valor como `4blue123`.  
3. Preencher os demais campos.  
4. Concluir o cadastro.

**Resultado atual:**  
O sistema aceita números no campo nome.

**Resultado esperado:**  
O campo nome deve aceitar apenas caracteres compatíveis com nomes de pessoas, conforme regra de negócio definida.

**Severidade:** Médio  
**Prioridade:** Média

---

## Bug 03. Campo telefone aceita letras, não possui máscara e não possui limite de caracteres

**Descrição:**  
O campo telefone permite letras, não aplica máscara de formatação e não limita a quantidade de caracteres digitados.

**Passos para reproduzir:**  
1. Acessar a tela de criação de conta.  
2. Informar letras ou uma sequência extensa no campo telefone.  
3. Concluir o cadastro.

**Resultado atual:**  
O campo aceita conteúdo inválido e sem padronização.

**Resultado esperado:**  
O campo deve aceitar apenas números, aplicar máscara adequada e limitar a quantidade de caracteres conforme o padrão esperado.

**Severidade:** Médio  
**Prioridade:** Média

---

## Bug 04. Campos e caixas de texto apresentam desalinhamento visual

**Descrição:**  
Os elementos visuais da interface não seguem um padrão consistente de alinhamento, o que prejudica a percepção de qualidade e a experiência do usuário.

**Passos para reproduzir:**  
1. Acessar as telas de login e criação de conta.  
2. Observar o alinhamento dos campos, rótulos e caixas de texto.

**Resultado atual:**  
Os componentes visuais apresentam desalinhamento.

**Resultado esperado:**  
A interface deve manter alinhamento e espaçamento padronizados entre os elementos.

**Severidade:** Baixo  
**Prioridade:** Baixa

---

## Bug 05. Sistema permite criar conta sem caractere especial na senha

**Descrição:**  
O cadastro é concluído mesmo quando a senha não possui caractere especial, indicando ausência de validação de complexidade.

**Passos para reproduzir:**  
1. Acessar a tela de criação de conta.  
2. Preencher os dados do formulário.  
3. Informar uma senha sem caractere especial.  
4. Concluir o cadastro.

**Resultado atual:**  
A conta é criada com senha sem caractere especial.

**Resultado esperado:**  
O sistema deve impedir o cadastro e exibir mensagem clara informando os requisitos mínimos de senha.

**Severidade:** Alto  
**Prioridade:** Alta

---

## Bug 06. Sistema permite criar conta sem preencher nenhum campo

**Descrição:**  
É possível criar uma conta sem preencher qualquer campo do formulário. Além disso, essa conta permanece válida para tentativa de autenticação posterior.

**Passos para reproduzir:**  
1. Acessar a tela de criação de conta.  
2. Deixar todos os campos em branco.  
3. Clicar em criar conta.

**Resultado atual:**  
A conta é criada mesmo sem dados preenchidos.

**Resultado esperado:**  
O sistema deve bloquear a criação da conta e exibir validação de obrigatoriedade nos campos.

**Severidade:** Crítico  
**Prioridade:** Alta

---

## Bug 07. Sistema permite criar conta com senha e confirmação de senha divergentes

**Descrição:**  
O sistema permite finalizar o cadastro mesmo quando os campos senha e repetir senha possuem valores diferentes.

**Passos para reproduzir:**  
1. Acessar a tela de criação de conta.  
2. Preencher os dados do formulário.  
3. Informar uma senha no campo senha.  
4. Informar outra senha diferente no campo repetir senha.  
5. Finalizar o cadastro.

**Resultado atual:**  
A conta é criada com senhas divergentes.

**Resultado esperado:**  
O sistema deve impedir a criação da conta e informar que os campos de senha precisam coincidir. Esse é justamente o propósito deste campo.

**Severidade:** Crítico  
**Prioridade:** Alta

---

## Bug 08. Mensagem de erro é exibida no canto inferior direito após o login

**Descrição:**  
Após o login, é apresentada uma mensagem de erro no canto inferior direito da tela, indicando falha no fluxo ou tratamento inadequado da resposta do sistema.

<img width="1165" height="710" alt="image" src="https://github.com/user-attachments/assets/a3042734-39f9-43f7-8be4-2dc95500783b" />

**Passos para reproduzir:**  
1. Acessar a tela de login.  
2. Informar credenciais válidas.  
3. Realizar login.  
4. Observar o canto inferior direito da tela.

**Resultado atual:**  
Uma mensagem de erro é exibida após o login.

**Resultado esperado:**  
Após login válido, o sistema deve redirecionar corretamente sem apresentar mensagens de erro indevidas.

**Severidade:** Alto  
**Prioridade:** Alta

---

## Bug 09. Dados das contas ficam expostos no console do navegador

**Descrição:**  
Informações de contas cadastradas estão sendo exibidas no console do navegador, caracterizando exposição indevida de dados e falha básica de segurança.

<img width="1728" height="622" alt="image" src="https://github.com/user-attachments/assets/53928e76-9fc9-4519-bb92-48d20764a8e7" />


**Passos para reproduzir:**  
1. Acessar o sistema.  
2. Abrir o console do navegador.  
3. Criar conta ou realizar login.  
4. Verificar os dados exibidos.

**Resultado atual:**  
Dados de usuários e contas ficam visíveis no console.

**Resultado esperado:**  
O sistema não deve expor dados sensíveis ou informações de usuários no console do navegador.

**Severidade:** Crítico  
**Prioridade:** Alta

---

## Bug 10. Login permite acesso sem preenchimento de credenciais

**Descrição:**  
O sistema permite fluxo de login sem dados válidos, especialmente quando previamente foi criada uma conta sem informações.

**Passos para reproduzir:**  
1. Criar uma conta sem preencher os campos, caso o sistema permita.  
2. Ir para a tela de login.  
3. Deixar os campos vazios.  
4. Tentar entrar.

**Resultado atual:**  
O sistema permite autenticação sem credenciais válidas.

**Resultado esperado:**  
O login deve exigir credenciais válidas e bloquear tentativas com campos vazios.

**Severidade:** Crítico  
**Prioridade:** Alta

---

## Bug 11. Sistema permite criar conta com senha menor que 8 caracteres

**Descrição:**  
O sistema aceita senhas com menos de 8 caracteres, contrariando uma política mínima de segurança.

**Passos para reproduzir:**  
1. Acessar a tela de criação de conta.  
2. Preencher os dados.  
3. Informar senha com menos de 8 caracteres.  
4. Finalizar o cadastro.

**Resultado atual:**  
A conta é criada com senha curta.

**Resultado esperado:**  
O sistema deve bloquear o cadastro e exigir senha com no mínimo 8 caracteres.

**Severidade:** Alto  
**Prioridade:** Alta

---

## Bug 12. Sistema permite criar contas duplicadas com os mesmos dados

**Descrição:**  
É possível cadastrar mais de uma conta com os mesmos dados já utilizados, demonstrando ausência de validação de unicidade.

**Passos para reproduzir:**  
1. Criar uma conta com dados válidos.  
2. Voltar para a tela de cadastro.  
3. Repetir exatamente os mesmos dados.  
4. Finalizar o cadastro novamente.

**Resultado atual:**  
O sistema permite múltiplos cadastros com dados idênticos.

**Resultado esperado:**  
O sistema deve impedir duplicidade, especialmente em campos que deveriam ser únicos, como e-mail.

**Severidade:** Alto  
**Prioridade:** Alta

---

## Bug 13. Sistema apresenta problemas de responsividade

**Descrição:**  
A interface não se adapta adequadamente a diferentes tamanhos de tela, comprometendo a navegação e a visualização dos elementos.

<img width="660" height="825" alt="image" src="https://github.com/user-attachments/assets/ee313ea8-6bf3-40a5-9961-cf0e73044ebf" />

**Passos para reproduzir:**  
1. Acessar a aplicação em resoluções diferentes ou utilizar o modo responsivo do navegador.  
2. Navegar entre as telas do sistema.  
3. Observar o comportamento dos componentes.

**Resultado atual:**  
Alguns elementos não se ajustam corretamente à tela, prejudicando a experiência do usuário.

**Resultado esperado:**  
A interface deve ser responsiva e manter usabilidade adequada em diferentes resoluções.

**Severidade:** Médio  
**Prioridade:** Média

---

## Bug 14. Feedback de erro é exibido por alert nativo do navegador

**Descrição:**  
Mensagens de erro são exibidas por meio de alertas nativos do navegador, o que prejudica a experiência do usuário e gera uma interface inconsistente com o restante do sistema.

<img width="499" height="757" alt="image" src="https://github.com/user-attachments/assets/27d11fd7-aa74-4137-948b-12696de9c1d4" />

**Passos para reproduzir:**  
1. Executar login com uma conta não criada.  
2. Observar a forma como a mensagem é exibida.

**Resultado atual:**  
O feedback aparece em alert padrão do navegador.

**Resultado esperado:**  
O sistema deve exibir mensagens de erro dentro da própria interface, de forma padronizada e contextual (Toast).

**Severidade:** Médio  
**Prioridade:** Média

---

## Bug 15. Sistema não apresenta feedbacks de validação em tela para erros de preenchimento

**Descrição:**  
Mesmo quando o usuário informa dados incorretos, o sistema não apresenta feedback claro e contextual na interface. Isso ocorre, por exemplo, em casos de senha divergente, telefone inválido, e-mail inválido, nome com números, senha sem requisito mínimo de caracteres ou sem caractere especial.

<img width="749" height="723" alt="image" src="https://github.com/user-attachments/assets/3139ffaf-e416-4027-8c58-8268f6c4c108" />

**Passos para reproduzir:**  
1. Acessar a tela de criação de conta.  
2. Informar dados inválidos em diferentes campos.  
3. Tentar concluir o cadastro.  
4. Observar os feedbacks apresentados.

**Resultado atual:**  
Não há validação visível ou feedback adequado em tela para orientar o usuário.

**Resultado esperado:**  
O sistema deve validar os campos e apresentar mensagens claras, específicas e contextuais para cada erro de preenchimento, de preferência antes do usuário clicar em criar conta. Em termos de usabilidade poderia estar sendo exibido na tela para o usuário por meio de um toast ou em um dropdown/popup na tela.

**Severidade:** Alto  
**Prioridade:** Alta

---

## Bug 16. Nenhum campo do formulário é tratado como obrigatório, comprometendo a prevenção de erros e a orientação do usuário

**Descrição:**  
Os campos do formulário não possuem obrigatoriedade efetiva, permitindo o envio de dados incompletos ou vazios. Além de ser uma falha funcional, esse comportamento também representa um problema de usabilidade, pois vai contra as heurísticas de Nielsen, especialmente a de **prevenção de erros**, já que o sistema não impede ações inválidas antes do envio. Também há impacto na heurística de **visibilidade do status do sistema**, porque o usuário não recebe indicação clara sobre quais campos precisam ser preenchidos, e na heurística de **ajuda os usuários a reconhecer, diagnosticar e corrigir erros**, pois não há feedback adequado orientando a correção.

**Passos para reproduzir:**  
1. Acessar a tela de criação de conta.  
2. Deixar um ou mais campos vazios.  
3. Tentar finalizar o cadastro.

**Resultado atual:**  
O sistema permite envio do formulário sem preenchimento obrigatório e sem orientar adequadamente o usuário sobre os campos faltantes.

**Resultado esperado:**  
Os campos obrigatórios devem ser claramente indicados na interface e validados antes do envio. Em caso de ausência de preenchimento, o sistema deve bloquear a ação e apresentar feedback específico, claro e contextual para orientar o usuário.

**Severidade:** Crítico  
**Prioridade:** Alta

## 5. Quais 2 bugs eu corrigiria primeiro e por quê

### Bug 10. Login permite acesso sem preenchimento de credenciais

Este seria o primeiro bug a ser corrigido, pois compromete diretamente a autenticação e o controle de acesso do sistema. Trata-se de uma falha crítica de segurança, com impacto direto na integridade da aplicação.

### Bug 09. Dados das contas ficam expostos no console do navegador

Este seria o segundo bug priorizado, pois envolve exposição indevida de informações de usuários. Além do risco de vazamento de dados, o problema demonstra ausência de boas práticas mínimas de segurança e tratamento de informações sensíveis.

## 6. Justificativa da priorização

Os bugs 09 e 10 foram priorizados por apresentarem maior risco técnico e de negócio. Ambos afetam segurança, privacidade e confiabilidade do sistema, superando em criticidade os problemas visuais e de validação simples.

## 7. Sugestões de melhoria

### Melhorar a exibição de mensagens de feedback

Como melhoria de experiência do usuário, as mensagens de sucesso, aviso e erro poderiam ser exibidas por meio de componentes visuais padronizados na própria interface, como toast, popup contextual ou mensagem abaixo do campo. Caso seja adotado toast, uma posição como o canto superior direito tende a oferecer melhor visibilidade sem prejudicar a navegação.

### Implementar fluxo de “Esqueci minha senha”

Seria recomendável adicionar a funcionalidade de recuperação de senha, permitindo ao usuário redefinir o acesso em caso de esquecimento. Essa melhoria fortalece a experiência do usuário e aproxima a aplicação de um fluxo real de autenticação.

### Reforçar validações com foco em prevenção de erros

Os problemas encontrados demonstram ausência de mecanismos de prevenção de erro e de comunicação clara com o usuário. Sob a ótica de usabilidade, isso vai contra princípios reconhecidos de UX, especialmente no aspecto de prevenção de erros. O sistema deveria antecipar falhas de preenchimento por meio de validações em tempo real, mensagens orientativas e requisitos claramente visíveis.

### Melhorar a responsividade da interface

A aplicação deveria se adaptar de forma consistente a diferentes resoluções e dispositivos, garantindo legibilidade, alinhamento e navegação adequada em diversos contextos de uso.

### Implementar controle de tamanho mínimo e máximo nos campos

É recomendável aplicar limites de caracteres em todos os campos do formulário, respeitando a regra de negócio de cada dado. Essa prática melhora a integridade das informações, previne entradas excessivas ou inconsistentes e reduz o acúmulo de dados inadequados no banco. Além disso, contribui para a validação da interface, para a padronização dos cadastros e para uma melhor experiência do usuário durante o preenchimento.

## 8. Proposta de automação dos testes

Como evolução do processo de qualidade, seria possível desenvolver uma automação para validar os principais cenários encontrados durante a análise.

### Objetivo da automação

Automatizar a verificação dos pontos críticos do sistema, incluindo:
- validação de campos
- fluxos de cadastro
- fluxos de login
- mensagens de erro
- responsividade básica
- evidências por captura de tela
- geração de relatório final

### Fluxo sugerido

1. Iniciar a aplicação e abrir o navegador.  
2. Executar cenários positivos e negativos de cadastro.  
3. Executar cenários positivos e negativos de login.  
4. Validar regras de campos obrigatórios.  
5. Verificar restrições de senha, e-mail, telefone e nome.  
6. Capturar screenshots quando houver falha.  
7. Consolidar os resultados em relatório final.

### Tecnologias e bibliotecas sugeridas

- Python
- Selenium
- Pytest
- webdriver-manager
- pytest-html ou Allure Report
- Faker, para geração de massa de dados
- pathlib ou os, para organização de evidências
- logging, para rastreabilidade da execução

## Conclusão

A execução dos testes evidenciou não conformidades relevantes nos fluxos de autenticação, cadastro, validação de entrada, tratamento de erros, segurança básica e responsividade da aplicação. Os achados demonstram ausência de controles essenciais tanto no front-end quanto nas regras de consistência esperadas para persistência e autenticação de dados, resultando em riscos funcionais, vulnerabilidades de segurança e degradação da experiência do usuário.

Sob a perspectiva de qualidade de software, os problemas identificados indicam falhas em camadas críticas da aplicação, especialmente nos mecanismos de validação de formulário, integridade cadastral, prevenção de estados inválidos, proteção de informações sensíveis e comunicação de erro com o usuário. A possibilidade de criação de contas com dados vazios, autenticação sem credenciais válidas, duplicidade cadastral e exposição de dados no console evidencia deficiência de controles mínimos de entrada, processamento e saída.

Do ponto de vista de usabilidade, também foram observadas inconsistências que impactam diretamente a interação do usuário com o sistema, como ausência de feedback contextual, uso inadequado de alertas nativos, falta de indicação de obrigatoriedade dos campos e baixa aderência a princípios reconhecidos de UX, incluindo heurísticas de Nielsen relacionadas à prevenção de erros, visibilidade do status do sistema e suporte ao reconhecimento e correção de falhas.

Em termos de priorização, os defeitos relacionados à autenticação indevida e à exposição de dados devem ser tratados com máxima urgência, por representarem maior criticidade técnica e maior impacto para o negócio. Na sequência, recomenda-se a correção das validações de formulário, da unicidade cadastral, da política de senha, da responsividade e do tratamento visual dos retornos da interface.

Por fim, a análise demonstra que a evolução da aplicação depende não apenas da correção pontual dos bugs identificados, mas também da adoção de práticas mais robustas de engenharia de qualidade, incluindo validações consistentes em múltiplas camadas, melhoria da observabilidade do fluxo de erro, padronização da experiência do usuário e implementação de testes automatizados para cobertura dos cenários críticos e prevenção de regressões.
