# AWS_Re/Start

## Trabalho de Conclusão de Curso da Escola da Nuvem

[![dataHub.png](https://i.postimg.cc/jSQ11SRS/dataHub.png)](https://postimg.cc/xX8gJYkw)


## OBJETIVO 
- Evoluir a infraestrutura da startup Nova Tech, priorizando a robustez e a escalabilidade de suas aplicações de e-commerce, com ênfase na **otimização e gerenciamento de bancos de dados na AWS.**

- Com um aporte inicial de até $10.000, planejamos investimentos estratégicos para fortalecer a base tecnológica.

## SITUAÇÃO ATUAL DA APLICAÇÃO NA AWS

> Atualmente, a Nova Tech conta com uma arquitetura simplificada e limitada hospedada na AWS. A infraestrutura utiliza apenas uma Região (Norte da Virgínia) e está configurada com uma única VPC contendo uma zona de disponibilidade. 

> Há uma única instância do Amazon EC2 em execução em uma sub-rede pública, enquanto a sub-rede privada permanece inativa. O acesso à aplicação é realizado exclusivamente por meio de um Internet Gateway.

> Essa configuração apresenta fragilidades, como a falta de alta disponibilidade, resiliência e segurança, que podem comprometer o desempenho e a continuidade do serviço em caso de falhas.

[![estado-atual.png](https://i.postimg.cc/kGz6NC2Q/estado-atual.png)](https://postimg.cc/1V03PLcX)

## PILARES DO WELL-ARCHITECTED FRAMEWORK

Nossa solução de arquitetura foi planejada para incorporar todos os princípios do AWS Well-Architected Framework.
Que é um conjunto de práticas e princípios desenvolvidos pela AWS que orienta arquitetos de soluções no planejamento e construção de arquiteturas, fundamentando-se em seis pilares essenciais.

Os seis pilares são:
- Excelência operacional;
- Segurança;
- Confiabilidade;
- Eficiência de desempenho;
- Otimização de custos;
- Sustentabilidade.
### EXCELÊNCIA OPERACIONAL

Foca na execução e monitoramento de sistemas e na melhoria contínua.

Pensando neste requisito utilizamos os serviços:

* [![Arch-AWS-Cloud-Trail-32.png](https://i.postimg.cc/PqygFzmx/Arch-AWS-Cloud-Trail-32.png)](https://postimg.cc/cKKkv3ky) Amazon CloudTrail

 Registra atividade da conta AWS, capturando eventos e ações realizadas pelos usuários, funções IAM e outros serviços. 
Mantém registros das chamadas de API feitas na conta.

* [![Arch-AWS-Lambda-32.png](https://i.postimg.cc/Wz1bH1FR/Arch-AWS-Lambda-32.png)](https://postimg.cc/CB9gZYsJ) AWS Lambda

O AWS Lambda é um serviço de computação sem servidor que permite executar código sem a necessidade de provisionar e gerenciar servidores.
Será utilizado para processar a lógica de negócios, como gestão de carrinho, controle de estoque e processamento de pedidos.

* [![Arch-Amazon-API-Gateway-32.png](https://i.postimg.cc/mkPW9z1r/Arch-Amazon-API-Gateway-32.png)](https://postimg.cc/SYbPFKr0) API Gateway

Intermedia a comunicação entre o frontend e as aplicações lambdas.
Irá expor APIs RESTful seguras para operações como adicionar itens ao carrinho, finalizar compra e consultar pedidos.

* [![Arch-Amazon-Cloud-Watch-32.png](https://i.postimg.cc/pr3bJWKJ/Arch-Amazon-Cloud-Watch-32.png)](https://postimg.cc/LgkbHMCJ) Amazon CloudWatch

Monitoramento e gerencia de recursos, ajudando a operar e melhorar continuamente os processos, oferece uma visão detalhada do desempenho operacional dos recursos AWS.

### SEGURANÇA
Princípio de proteção de informações e sistemas, utilizamos os serviços:

* [![Arch-AWS-WAF-32.png](https://i.postimg.cc/1t2sJrQF/Arch-AWS-WAF-32.png)](https://postimg.cc/TLVzPmh2) WAF

O Web Application Firewall irá minimizar riscos e proteger tanto a aplicação quanto os dados do e-commerce, garantindo um ambiente seguro e confiável para os usuários e para os administradores.

* [![Arch-Amazon-Cognito-32.png](https://i.postimg.cc/0QWqrdQ3/Arch-Amazon-Cognito-32.png)](https://postimg.cc/phFS6jKY) Amazon Cognito

Irá gerenciar a autenticação e autorização dos usuários, permitindo que os clientes se registrem, façam login e acessem suas contas com segurança.

* [![Arch-AWS-Identity-and-Access-Management-32.png](https://i.postimg.cc/wjQxgNXK/Arch-AWS-Identity-and-Access-Management-32.png)](https://postimg.cc/3kWQZdf9) Role do IAM

Implementa um controle robusto de segurança, garantindo que cada recurso ou serviço da AWS tenha permissões precisas para executar apenas ações necessárias, seguindo o princípio de menor privilégio.

### CONFIABILIDADE
Princípio de recuperação rápida de falhas, utilizamos os serviços:

* [![Arch-Amazon-Route-53-32.png](https://i.postimg.cc/qvVHt7Jk/Arch-Amazon-Route-53-32.png)](https://postimg.cc/Xp8zm4Bh) Amazon Route 53

Gerencia o DNS e facilita o roteamento de tráfego para o site.
Irá garantir uma navegação estável e confiável para os usuários.

* [![Arch-Amazon-Virtual-Private-Cloud-32.png](https://i.postimg.cc/Nj6qRwFR/Arch-Amazon-Virtual-Private-Cloud-32.png)](https://postimg.cc/zyGc16nf) amazon VPC

O Amazon VPC (Virtual Private Cloud) é um serviço que permite criar redes isoladas logicamente na AWS.<br>
* [![Public-subnet-32.png](https://i.postimg.cc/6QH9GNbY/Public-subnet-32.png)](https://postimg.cc/WDkRQxvk) Sub-rede pública
 
As subredes públicas são para os recursos que precisam de acesso à internet. <br>

* [![Private-subnet-32.png](https://i.postimg.cc/HkgWqz74/Private-subnet-32.png)](https://postimg.cc/hf2qx9sf) Sub-rede privada
 
As subredes privadas permitem proteger recursos que não devem estar diretamente acessíveis na internet.

* [![GLOBALTABLES-DYNAMO-32.png](https://i.postimg.cc/1RFQy6SW/GLOBALTABLES-DYNAMO-32.png)](https://postimg.cc/nMn5kXC7) DynamoDB Global Tables

Irá garantir alta disponibilidade, baixa latência e consistência dos dados entre diferentes regiões geográficas.

### EFICIÊNCIA DE PERFORMANCE

Princípio de alocação eficiente de recursos e monitoramento contínuo, utilizamos os serviços:
* [![Arch-Amazon-Cloud-Front-32.png](https://i.postimg.cc/vBHsQSQf/Arch-Amazon-Cloud-Front-32.png)](https://postimg.cc/kVZZssRg) Amazon CloudFront

Rede de entrega de conteúdo (CDN).
Irá distribuir o conteúdo do S3 de maneira rápida e segura para os clientes em várias regiões, reduzindo a latência e otimizando a experiência do usuário.

* [![Arch-Amazon-Simple-Storage-Service-32.png](https://i.postimg.cc/J4BW4XW6/Arch-Amazon-Simple-Storage-Service-32.png)](https://postimg.cc/nCZW3CrB) Amazon S3 (Simple storage service)

Discos rígidos na nuvem:
Armazena um grande volume de dados estáticos, como imagens de produtos, vídeos e arquivos de log, proporcionando alto desempenho.
* [![Res-Amazon-Dynamo-DB-Amazon-Dynamo-DB-Accelerator-48.png](https://i.postimg.cc/MTvz7rhx/Res-Amazon-Dynamo-DB-Amazon-Dynamo-DB-Accelerator-48.png)](https://postimg.cc/VrPy14fH) DynamoDB Accelerator (DAX)

Será utilizado para aumentar a performance de leitura do Dynamo DB, reduzindo a latência das consultas, servindo como cache especialmente em operações de leitura intensiva.

### OTIMIZAÇÃO DE CUSTOS
Princípio criado para evitar custos desnecessários, utilizamos os serviços:

* [![Arch-AWS-Backup-32.png](https://i.postimg.cc/wB9KVbRZ/Arch-AWS-Backup-32.png)](https://postimg.cc/w14bx2VQ) Amazon S3 Backup

Garante um uso eficiente de armazenamento e reduz custos operacionais.

* [![Arch-AWS-Lambda-32.png](https://i.postimg.cc/Wz1bH1FR/Arch-AWS-Lambda-32.png)](https://postimg.cc/CB9gZYsJ) AWS Lambda

Pagamento por uso, reduzindo custos ao executar códigos apenas quando necessário.

* [![Arch-Amazon-Dynamo-DB-32.png](https://i.postimg.cc/Wpyvvnxq/Arch-Amazon-Dynamo-DB-32.png)](https://postimg.cc/Bt2y5xSJ) DynamoDB

Solução de banco de dados NoSQL altamente escalável, gerenciada e sem servidores.

* [![Res-AWS-Backup-Database-48.png](https://i.postimg.cc/5NqWCV6L/Res-AWS-Backup-Database-48.png)](https://postimg.cc/mtD5vK3g) Backup Database

Permite que a aplicação recupere de falhas de maneira rápida e eficiente, minimizando os custos com o tempo de atividade e recuperação de desastres.

### SUSTENTABILIDADE

Princípio que visa a minimização dos impactos ambientais, utilizamos os serviços:
* [![Arch-Amazon-Simple-Storage-Service-32.png](https://i.postimg.cc/J4BW4XW6/Arch-Amazon-Simple-Storage-Service-32.png)](https://postimg.cc/nCZW3CrB) Amazon S3 (Simple storage service)

Armazenamento eficiente que pode ser otimizado para reduzir o consumo de energia.

* [![Arch-AWS-Lambda-32.png](https://i.postimg.cc/Wz1bH1FR/Arch-AWS-Lambda-32.png)](https://postimg.cc/CB9gZYsJ) AWS Lambda 

 Eficiência Energética ao executar código apenas quando necessário, reduzindo o consumo de recursos.

## SOLUÇÃO DE ARQUITETURA
- Este é o diagrama da nossa solução de arquitetura utilizando todos os serviços descritos acima:
[![FINAL-do-e-commerce-serveless-grupo3-2regioes-P-gina-1.png](https://i.postimg.cc/J46bTwkB/FINAL-do-e-commerce-serveless-grupo3-2regioes-P-gina-1.png)](https://postimg.cc/8jvJ50w1)

## PROPOSTA

* Custo total de 12 meses: 
   #### 6.469,32 USD
* Custo mensal:
  #### 539,11 USD

Confira todas as configurações de custos na calculadora da AWS:
[clique aqui](https://calculator.aws/#/estimate?id=25387a49913d2bdcba56a104ae3ff7d3660b204d)

> Podemos concluir que permanecemos dentro do aporte inicial de $10.000,00, alcançando o objetivo de desenvolver uma arquitetura robusta e escalável. Além do foco em banco de dados, também priorizamos segurança, monitoramento e eficiência de performance, garantindo um ambiente confiável e de alta qualidade para o nosso cliente.
## DESAFIOS

Principais desafios que encontramos durante o projeto e o que foi feito para contorná-lo:
* Falta de domínio sobre a calculadora da AWS:
  * Realizar diversos esboços de arquitetura até definirmos serviços que se adequassem ao nosso orçamento. Além de utilizar os guias da AWS, que oferecem tutoriais detalhados sobre como utilizar a ferramenta de forma eficiente.

* Compreender o contexto de negócio e adaptar as versões das arquitetura:
  * Realizar um levantamento e análise detalhada dos requisitos do negócio para garantir que os serviços atenderão às demandas reais e futuras da empresa. Além disso, foi analisado arquiteturas distintas do mercado para identificar práticas eficazes e projetar soluções flexíveis que se adaptem a mudanças de contexto.
 
* Projetar uma arquitetura que escale horizontal e verticalmente para lidar com variações na carga de trabalho:
  * Adotar os recursos nativos do AWS Lambda, que escala automaticamente ao criar novas instâncias de execução conforme a demanda, e configurar triggers no API Gateway para acionar as funções Lambda apenas quando necessário, garantindo uma escalabilidade eficiente e otimizada.

* Garantir que a arquitetura cumpra padrões de segurança, conformidade e privacidade:
  * Seguir as recomendações de segurança da WAF e as boas práticas de segurança, como a utilização de princípios de menor privilégio e gestão rigorosa de identidades e acessos por meio o IAM. Além de utilizar CloudTrail para registrar e monitorar todas as atividades da conta, garantindo auditoria completa das ações realizadas pelos usuários e serviços.

* Manter a aplicação resiliente em caso de falhas de serviço ou zona de disponibilidade:
  * Para maior resiliência, pode-se projetar a aplicação para operar em múltiplas regiões da AWS. Caso uma região inteira sofra uma falha, a aplicação pode ser redirecionada para uma outra região que esteja operando normalmente.Isso envolve a replicação de dados e serviços críticos em diferentes regiões e a utilização de Route 53 para failover DNS automático.

## QUEM SOMOS?

> A Data Hub é uma consultoria criada com o objetivo de trazer soluções para
a Startup Nova Tech. Este trabalho de conclusão de curso foi desenvolvido no contexto do programa AWS Re/Start, em parceria com a Escola da Nuvem.

Durante nosso trabalho, tivemos que assumir papéis importantes para o desenvolvimento, organização e desempenho das nossas soluções, confira cada um dos participantes através do LinkedIn:

* Engenheiro(a) de Dados:
[Ana Beatriz Santos](https://www.linkedin.com/in/anabsantoss/)

* Gerente de Projetos:
[Danilo dos Santos](https://www.linkedin.com/in/daniloasc/)

* Especialista em Banco de Dados:
[Gabriel Castilho](https://www.linkedin.com/in/gabriel-castilho-8781492b0/)

* Analista de Sistemas:
[Luiz Santos](https://www.linkedin.com/in/luiz-santos7/)

* Especialista em Custos e Otimização Cloud:
[Milena Carvalho](https://www.linkedin.com/in/milenatech/)

* Administradora Cloud:
[Raquel Dias](https://www.linkedin.com/in/raqueldiasds/)

* Arquiteto de Soluções:
[William Paludo](https://www.linkedin.com/in/william-paludo/)


[![escoladanuvem.png](https://i.postimg.cc/bJR9RZPQ/escoladanuvem.png)](https://postimg.cc/8JjvpPj5)
