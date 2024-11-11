# Segurança e Responsabilidade

Este documento descreve as diretrizes de segurança e responsabilidade para o uso deste projeto de *secrets-detection* dentro de pipelines de CI/CD.

## Privacidade e Exposição de Dados na Pipeline

Este projeto realiza varreduras em busca de segredos sensíveis (como chaves de API, senhas, e outros dados confidenciais) em código-fonte. A ferramenta utiliza apenas recursos nativos do Python. No entanto, a exposição de dados sensíveis pode ocorrer no contexto da execução dentro de pipelines de CI/CD, dependendo de como a ferramenta é configurada.

### Responsabilidade do Usuário:

1. **Execução da ferramenta dentro de pipelines seguras**: A ferramenta foi projetada para ser executada em pipelines de CI/CD. É fundamental garantir que esses pipelines estejam protegidos contra acessos não autorizados e que os dados sensíveis não sejam expostos em logs ou arquivos temporários.

2. **Proteção dos resultados da varredura**: Os resultados da varredura (`secrets_report.json` ou outros arquivos gerados) podem conter segredos identificados no código. É importante armazenar esses relatórios de maneira segura, para evitar que dados sensíveis vazem para sistemas ou repositórios públicos.

3. **Uso exclusivo em repositórios e ambientes autorizados**: A ferramenta deve ser utilizada apenas em repositórios e ambientes nos quais você tenha permissão para realizar a varredura de segredos. O uso indevido pode resultar em riscos de exposição não autorizada de dados.

4. **Cuidados ao utilizar em ambientes compartilhados**: Caso a pipeline de CI/CD seja compartilhada com outros projetos ou equipes, é crucial configurar controles de acesso adequados para evitar que segredos de um projeto sejam expostos para outros.

5. **Tratamento responsável de dados sensíveis**: Embora a ferramenta em si não envie dados para fora, a forma como os dados (segredos identificados) são tratados após a varredura é de responsabilidade do usuário. Certifique-se de que nenhuma informação sensível seja armazenada ou compartilhada indevidamente.

### Limitação de Responsabilidade

O desenvolvedor e os contribuidores não se responsabilizam por qualquer dano, perda ou exposição de dados sensíveis resultante do uso desta ferramenta, especialmente no contexto de pipelines de CI/CD. A responsabilidade de configurar corretamente os pipelines, proteger os dados sensíveis e assegurar o uso ético da ferramenta é do usuário.

Em caso de dúvidas sobre como proteger seus dados ou utilizar esta ferramenta de forma segura na pipeline, consulte as diretrizes de segurança de sua organização ou procure ajuda de profissionais de segurança.

**Obrigado por usar este projeto de maneira ética e responsável.**
