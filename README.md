# Fix-It — Cuidando da Nossa Cidade

## 1. Integrantes da Equipe
- **Gabriel Sbrana Campos** | RM: 565849 | Turma: 2TDSPF
- **Moisés Waidemann Molinillo** | RM: 563719 | Turma: 2TDSPF
- **Richard Freitas** | RM: 566127 | Turma: 2TDSPF
- **Thiago Rodrigues da Mota** | RM: 563650 | Turma: 2TDSPF

## 3. A Solução Fix-It

### Qual é o problema? (A dor)
As ruas das cidades sofrem com buracos no asfalto, lâmpadas de postes queimadas, lixo jogado em lugares errados e bueiros entupidos. Avisar a prefeitura sobre isso costuma ser complicado, lento e quase nunca as pessoas sabem quando o problema vai ser consertado.

### O que o Fix-It resolve?
O Fix-It é um aplicativo fácil de usar:
1. O cidadão vê um problema na rua e tira uma foto com o celular.
2. A Inteligência Artificial analisa a imagem na hora, descobre o que quebrou (ex: buraco na via) e avalia a gravidade.
3. O pedido é enviado automaticamente para o setor responsável da prefeitura, sem papelada e sem complicação.
4. O morador acompanha pelo próprio app quando a equipe for até o local consertar.

### Por que isso é importante?
Ajuda a deixar a cidade mais segura e organizada, garante que bairros afastados também sejam ouvidos e ajuda a prefeitura a consertar o que é mais urgente mais rápido.

---

## 4. Arquitetura e Como Tudo Funciona Junto

Abaixo explicamos o caminho que a informação faz de ponta a ponta de forma simples:

1. **No Celular (App React Native):** O usuário faz login, fotografa o problema na rua e o aplicativo pega a localização exata pelo GPS.
2. **O Servidor Central (API Backend):** Recebe os dados com segurança, confere se o usuário está logado e impede que a mesma pessoa mande centenas de fotos seguidas (evitando travar o sistema).
3. **A Inteligência Artificial:** Analisa a foto para confirmar o estrago e classifica se é um risco leve, médio ou urgente.
4. **Fila de Tarefas (RabbitMQ):** Funciona como uma esteira organizada, distribuindo os chamados para que o aplicativo continue rápido mesmo com muita gente usando ao mesmo tempo.
5. **Onde as informações ficam guardadas (Bancos de Dados):**
   - **Oracle:** Guarda os dados das pessoas, histórico de consertos e registros que ninguém pode apagar.
   - **MongoDB:** Guarda os pontos no mapa e os detalhes das fotos.
6. **Colocando o Sistema no Ar (Azure & DevOps):** A infraestrutura fica na nuvem, com testes automáticos que garantem que tudo funcione antes de qualquer nova versão ir ao ar.

| O que é | Ferramenta | O que faz no projeto |
| :--- | :--- | :--- |
| **Aplicativo no Celular** | React Native | Onde o morador tira a foto e vê o mapa |
| **Servidor Central** | Java (Spring Boot) ou .NET | Recebe os dados e cuida das regras |
| **Inteligência Artificial** | Visão Computacional + LLM | Identifica o estrago pela foto e mede o perigo |
| **Fila de Mensagens** | RabbitMQ | Organiza os pedidos para não sobrecarregar |
| **Bancos de Dados** | Oracle e MongoDB | Guardam usuários, relatórios e locais no mapa |
| **Nuvem e Testes** | Azure DevOps | Testa o código sozinho e mantém tudo online |
