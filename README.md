# Spring learning step by step

## Aplicativo Simples com Arquitetura de Microsservices


![image](https://user-images.githubusercontent.com/52088444/161062804-90283781-4f0a-49a3-a7a6-9f43395a724d.png)

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

## Criação do projeto Spring

- O projeto foi criado através do [spring initializr](https://start.spring.io/).

- Depois o projeto foi importado para a IDE IntelliJ

## Criação da estrutura de Camada(controller-model-service-repository) 
![image](https://user-images.githubusercontent.com/52088444/161068508-3fac6bea-8f82-4faa-9a4f-5531b6c6a373.png)


## Aplicativo de Exemplo

**Anotações de Spring utilizadas**

- @Controller,@Repository,@Service

Na estrutura Spring, podemos usar a anotação de nível de classe @Component para criar um bean da classe automaticamente 
e registrar no contêiner Spring para liberá-lo sob demanda.

![image](https://user-images.githubusercontent.com/52088444/161069828-cd16af7f-18ad-471b-a42d-f00f3cf8559c.png)

As anotações @Controller, @Repository, @Service são herdadas da anotação @Component . Todos eles estão registrando beans
relevantes para as classes com as quais fizeram anotações. Além disso, podemos diferenciar claramente as classes na 
arquitetura em camadas por esses nomes de anotação em vez de usar o @Component para todos. A outra coisa importante 
é que essas três anotações têm alguns recursos especiais do que a anotação @Component.

Ex: A anotação @Controller não está apenas registrando um bean controlador no contêiner, mas também fornecendo a 
capacidade de lidar com os mapeamentos de solicitação (@RequestMapping) recebidos dos clientes.

@Autowired
O coração do Spring Framework é a injeção de dependência. Em vez de criar os objetos usando o construtor de classe com 
a palavra-chave 'new', estamos pedindo ao container spring para injetar o objeto bean na propriedade anotada com 
a anotação @Autowired.

@RequestMapping
Como mencionei anteriormente, a classe anotada com @Controller lida com os mapeamentos de caminho de solicitação. 
Portanto, pode conter vários mapeamentos de solicitação. @RequestMapping é usado para definir o caminho específico para
o qual a solicitação deve ser mapeada.

@Bean e @Configuration
Em vez de usar a anotação de nível de classe @Component para registrar classes de bean, podemos usar a anotação de nível
de método @Bean . Mas a classe deve ser anotada com @Configuration para indicar que esta classe tem os métodos para 
definições de bean.

@SpringBootApplication

Essa anotação consiste nas três anotações a seguir:
![image](https://user-images.githubusercontent.com/52088444/161070746-8c4467f7-a09b-44a0-bd80-5f9f07e5af31.png)


@EnableAutoConfiguration - É usado para obter as configurações padrão do Spring. O Spring boot reúne o componente 
necessário para executar o aplicativo a partir do caminho da classe e fornece automaticamente essas configurações e 
objetos das dependências que você já adicionou ao projeto. (Ex: Uma vez encontrado o driver do banco de dados no 
caminho da classe, ele adicionará automaticamente as configurações do banco de dados)

@ComponentScan - Esta anotação indica o aplicativo para verificar os componentes dentro do pacote para descobrir os 
beans, serviços e configuração necessários para executar o aplicativo.

@Configuration -Já descrito acima.


Conceitos de código para interface e injeção de dependência
Injeção de dependência é o conceito de obter o suporte de terceiros para injetar a dependência exigida pelas classes em vez de criá-las.