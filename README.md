# Spring learning step by step

## Aplicativo Simples com Arquitetura de Microsservices

![img.png](img.png)

- Controller- Controlador contém a *lógica do aplicativo, mapeando a solicitação do usuário para funções específicas e 
passando a entrada do usuário para a camada de serviço para aplicar a lógica de negócios.

- Service-  Esta é a camada entre o controlador e o repositório que executa a *lógica de negócios e a lógica de validação.
 O controlador passa a entrada do usuário para a camada de serviço e após aplicar a lógica de negócios, ela é passada 
para a camada de repositório.

- Repository- A camada que interage com as operações CRUD do banco de dados através dos DAOs (objetos de acesso a dados).

- Model-São as classes POJO** simples que estão atuando como DTO (Interação com transferência de dados no nível do aplicativo)
ou DAO (Interação com operações de banco de dados)

## Notas

* Lógica de negócios versus lógica de  aplicativo  - A lógica de negócios aborda as manipulações lógicas 
relacionadas ao domínio de negócios. Simplesmente lógicas de negócios mais específicas para o negócio.

Por outro lado, as lógicas do aplicativo representam as operações no nível do aplicativo, que não são específicas do
domínio de negócios, mas uma função do próprio aplicativo. Ex: Pressionar o botão e abrir o formulário de login é 
um exemplo da lógica da aplicação. Validar os dados de login do usuário é o requisito específico do domínio que vem 
sob a lógica de negócios.

** Plain Old Java Object ou POJO, são objetos Java que seguem um desenho extremamente simplificado. Um POJO é um 
JavaBean que segue definições rígidas de estrutura, sendo elas:

Possui um construtor default (padrão - sem argumentos) ou não declarar construtor (assim o compilador Java criara um 
construtor default automaticamente);

Possui todos os seus atributos, sejam eles tipos primitivos ou objetos, com a visibilidade privada;

Não possui métodos específicos, exceto aqueles que seguem o padrão de getter e setter para seus respectivos 
atributos

