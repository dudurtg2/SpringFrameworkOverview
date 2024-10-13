# Docker commands and overview <!-- omit in toc -->

## Contents <!-- omit in toc -->

- [1. O que é Spring?](#1-o-que-é-spring)
  - [1.1. O problema](#11-o-problema)
  - [1.2. Solução Spring Boot](#12-solução-spring-boot)
  - [1.3. Spring Boot e Spring](#13-spring-boot-e-spring)
  - [1.4. Spring Boot Embedded Server](#14-servidor-incorporado-spring-boot)
  - [1.5. Executando aplicativos Spring Boot](#15-executando-aplicativos-spring-boot)
  - [1.6. Implantando aplicativos Spring Boot](#16-implantando-aplicativos-spring-boot)
  - [1.7. Perguntas gerais](#17-perguntas-gerais)
- [2. Inicialização Spring](#2-spring-initializr)
  - [2.1. start.spring.io](#21-startspringio)
  - [2.2. CLI do Spring Boot](#22-cli-spring-boot)
- [3. Controlador REST](#3-controlador-rest)
- [4. Projetos Spring](#4-projetos-spring)
- [5. Projetos Spring Boot](#5-projetos-spring-boot)
  - [5.1. Estrutura de diretório padrão do Maven com Spring Boot](#51-estrutura-de-diretório-padrão-do-maven-com-spring-boot)
  - [5.2. Arquivos do wrapper do Maven](#52-arquivos-do-maven-wrapper)
  - [5.3. Arquivo POM do Maven com Spring Boot](#53-arquivo-pom-do-maven-com-spring-boot)
- [6. Iniciadores do Spring Boot](#6-iniciadores-do-spring-boot)
- [7. Spring Boot Dev Tools](#7-spring-boot-dev-tools)
  - [7.1. IntelliJ Community Edition - DevTools](#71-intellij-community-edition---devtools)
- [8. Spring Boot Actuator](#8-spring-boot-actuator)
  - [8.1. Health Endpoint](#81-endpoint-de-saúde-health-endpoint)
  - [8.2. Expondo Endpoints](#82-expondo-endpoints)
  - [8.3. Info Endpoint](#83-info-endpoint)
  - [8.4. Endpoints do Spring Boot Actuator](#84-endpoints-do-spring-boot-actuator)
  - [8.5. Expondo Endpoints](#85-expondo-endpoints)
  - [8.6. Obter uma lista de beans](#86-obter-uma-lista-de-beans)
  - [8.7. Processo de Desenvolvimento](#87-processo-de-desenvolvimento)
  - [8.8. Segurança](#88-segurança)
  - [8.8.1. Endpoints protegidos](#881-endpoints-protegidos)
  - [8.9. Excluindo Endpoints](#89-excluindo-endpoints)
  - [8.9.1. Processo de Desenvolvimento](#891-processo-de-desenvolvimento)
  - [8.10. Exemplo de Actuator](#810-exemplo-de-actuator)
- [9. Propriedades do Aplicativo Personalizado](#9-propriedades-personalizadas-do-aplicativo)
  - [9.1. Processo de Desenvolvimento](#91-processo-de-desenvolvimento)
  - [9.2. Propriedades do Spring Boot](#92-propriedades-do-spring-boot)
    - [9.2.1. Propriedades Core](#921-propriedades-core)
    - [9.2.2. Propriedades Web](#922-propriedades-web)
    - [9.2.3. Propriedades do Actuator](#923-propriedades-do-actuator)
    - [9.2.4. Propriedades de Segurança](#924-propriedades-de-segurança)
    - [9.2.5. Propriedades de Dados](#925-propriedades-de-dados)
- [10. Inversão de Controle e Injeção de Dependência](#10-inversão-de-controle-e-injeção-de-dependência)
  - [10.1. Tipos de Injeção](#101-tipos-de-injeção)
    - [10.1.1. Tipos de Injeção - Qual usar?](#1011-tipos-de-injeção---qual-usar)
    - [10.1.2. O que é Spring AutoWiring](#1012-o-que-é-o-spring-autowiring)
  - [10.2. Exemplo de Autowiring](#102-exemplo-de-autowiring)
  - [10.3. Aplicativo de Exemplo](#103-aplicativo-de-exemplo)
  - [10.4. Processo de Desenvolvimento - Injeção de Construtor](#104-processo-de-desenvolvimento---injeção-de-construtor)
  - [10.5. Spring para Aplicações Corporativas](#105-spring-para-aplicações-corporativas)
  - [10.6. Scaneamento de Classes de Componente](#106-scaneamento-de-classes-de-componente)
  - [10.7. Anotações](#107-anotações)
  - [10.8. Mais sobre a Varredura de Componentes](#108-mais-sobre-o-escaneamento-de-componentes)
  - [10.9. Injeção de Setter](#109-injeção-de-setter)
  - [10.10. Anotação @Primary](#1010-anotação-primary)
    - [10.10.1. Solução Alternativa](#10101-solução-alternativa)
    - [10.10.2. @Primary - Apenas um](#10102-primary---apenas-um)
    - [10.10.3. Qual usar: @Primary ou @Qualifier?](#10103-qual-usar-primary-ou-qualifier)
  - [10.11. Inicialização Preguiçosa (Lazy Initialization)](#1011-inicialização-preguiçosa-lazy-initialization)
    - [10.11.1. Inicialização Preguiçosa](#10111-inicialização-preguiçosa)
    - [10.11.2. Vantagens e Desvantagens](#10112-vantagens-e-desvantagens)
  - [10.12. Escopos do Bean](#1012-escopos-de-bean)
    - [10.12.1. Escopo Padrão](#10121-escopo-padrão)
  - [10.13. Escopos Adicionais do Spring Bean](#1013-escopos-adicionais-de-bean-do-spring)
  - [10.14. Métodos do Ciclo de Vida do Bean - Anotações](#1014-métodos-do-ciclo-de-vida-do-bean---anotações)
- [11. Comandos - Executar a partir da Linha de Comando](#11-comandos---executar-a-partir-da-linha-de-comando)
  - [11.1. Comandos do Maven](#111-comandos-maven)
  - [11.2. Comandos Spring](#112-comandos-spring)

# 1. O que é Spring?

- Framework muito popular para construir aplicativos Java.
- Fornece um grande número de classes auxiliares e anotações.

## 1.1. O problema

- Construir um aplicativo Spring tradicional é realmente DIFÍCIL!!!
  - P: Quais dependências JAR eu preciso?
  - P: Como faço para configurar (xml ou Java)?
  - P: Como faço para instalar o servidor? (Tomcat, JBoss etc...)
- E isso é APENAS o básico para começar.

## 1.2. Solução Spring Boot

- Facilite o início do desenvolvimento Spring.
- Minimize a quantidade de configuração manual.
  - Execute a configuração automática com base em arquivos props e classpath JAR.
- Ajude a resolver conflitos de dependência (Maven ou Gradle).
- Forneça um servidor HTTP incorporado para que possamos começar rapidamente.
- Tomcat, Jetty, Undertow, ...

## 1.3. Spring Boot e Spring

- Spring Boot usa Spring nos bastidores
- Spring Boot simplesmente torna mais fácil usar Spring

## 1.4. Servidor incorporado Spring Boot

- Não há necessidade de instalar um servidor separadamente.
- **Unidade independente Nada mais para instalar!**

## 1.5. Executando aplicativos Spring Boot

- Os aplicativos Spring Boot podem ser executados de forma independente (inclui servidor incorporado).
- Execute o aplicativo Spring Boot a partir do IDE ou da linha de comando.
- `java -jar <name_jar_file>.jar`

## 1.6. Implantando aplicativos Spring Boot

- Os aplicativos Spring Boot também podem ser implantados da maneira tradicional.
- Implante o arquivo Web Application Archive (WAR) em um servidor externo:
  - Tomcat, JBoss, WebSphere etc ...

## 1.7. Perguntas gerais

- **P: O Spring Boot substitui o Spring MVC, Spring REST etc...?**
  - Não. Em vez disso, o Spring Boot realmente usa essas tecnologias.
    - ![Visão do Spring Boot](/Images/SpringBootOverview.png)
- **P: O Spring Boot executa o código mais rápido do que o código Spring normal?**
  - Não.
    - Nos bastidores, o Spring Boot usa o mesmo código do Spring Framework.
    - Lembre-se, o Spring Boot visa facilitar o início.
    - Minimizar a configuração etc...
- **P: Preciso de um IDE especial para o Spring Boot?**
  - Não.
    - Podemos usar qualquer IDE para aplicativos Spring Boot... até mesmo usar um editor de texto simples.
    - A equipe do Spring fornece o Spring Tool Suite (STS) [plugins IDE] gratuito.
    - Alguns IDEs fornecem suporte sofisticado para ferramentas Spring.
    - Não é um requisito.

# 2. Spring Initializr

## 2.1. start.spring.io

- Crie rapidamente um projeto inicial do Spring Boot.
- Selecione suas dependências.
- Cria um projeto Maven/Gradle.
- Importa o projeto para seu IDE.
- Eclipse, IntelliJ, NetBeans etc...
- [start.spring.io](https://start.spring.io/)
- Se estivermos construindo um aplicativo Spring que precisa de: Web, Segurança, ...
- Basta selecionar as dependências no Spring Initializr.
- Ele adicionará os iniciadores Spring Boot apropriados ao seu `pom.xml`.

## 2.2. CLI Spring Boot

- Alternativa para [start.spring.io](https://start.spring.io/).

# 3. Controlador REST

- Estrutura básica:
```java
@RestController
public class HelloWorldController {
  @GetMapping("/")
  public String sayHello() {
    return "Hello World!";
  }
}
```
- [Exemplo](/Examples/first-rest-controller/)

# 4. Projetos Spring

- Módulos Spring adicionais criados sobre o Spring Framework principal
- Use apenas o que precisamos...
- Spring Cloud, Spring Data.
- Spring Batch, Spring Security.
- Spring Web Services, Spring LDAP.
- outros...

# 5. Projetos Spring Boot

## 5.1. Estrutura de diretório padrão do Maven com Spring Boot

![Estrutura de diretório padrão do Maven com Spring Boot](/Images/MavenStandardDirectoryStructureWithSpringBoot.png)

## 5.2. Arquivos do Maven Wrapper

- `mvnw` permite que executemos um projeto Maven.
  - Não é necessário ter o Maven instalado ou presente no seu caminho.
  - Se a versão correta do Maven **NÃO** for encontrada no seu computador.
    - **Baixa automaticamente** a versão correta e executa o Maven.
- Dois arquivos são fornecidos:
  - `mvnw.cmd` para MS Windows.
    - `mvnw clean compile test`
  - `mvnw.sh` para Linux/Mac.
    - `./mvnw clean compile test`
- Se já tivermos o Maven instalado anteriormente.
  - Então podemos ignorar/excluir os arquivos `mvnw`.
    - ![Arquivos do wrapper Maven](/Images/MavenWrapperFiles.png)
- Basta usar o Maven normalmente.
  - `mvn clean compile test`

## 5.3. Arquivo POM do Maven com Spring Boot

- pom.xml inclui informações que você inseriu no site Spring Initializr.
```xml
  <groupId>com.starterspringbootproject</groupId>
  <artifactId>starter-spring-boot-project</artifactId>
  <version>0.0.1-SNAPSHOT</version>
```
- Spring Boot Starters, uma coleção de dependências do Maven (versões compatíveis).
  ```xml
    <dependencies>
      ...
      <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter</artifactId>
      </dependency>

      <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-test</artifactId>
        <scope>test</scope>
      </dependency>
      ...
    </dependencies>
  ```

- To package executable `jar` or `war` archive, can also easily run the app.
  ```xml
    <build>
      <plugins>
        <plugin>
          <groupId>org.springframework.boot</groupId>
          <artifactId>spring-boot-maven-plugin</artifactId>
        </plugin>
      </plugins>
    </build>
  ```

# 6. Iniciadores do Spring Boot

- **O problema...**
  - Construir um aplicativo Spring é realmente DIFÍCIL!!!
- **Por que é tão difícil?**
  - Seria ótimo se houvesse uma lista simples de dependências do Maven.
  - Reunidas como um grupo de dependências... um balcão único.
  - Então não preciso procurar por cada dependência.
- **Spring Boot Starters**
  - Uma lista selecionada de dependências do Maven.
  - Uma coleção de dependências agrupadas.
  - Testado e verificado pela equipe de desenvolvimento do Spring.
  - Torna muito mais fácil para o desenvolvedor começar a usar o Spring.
  - Reduz a quantidade de configuração do Maven.
- Há mais de 30 Spring Boot Starters da equipe de desenvolvimento do Spring.
  | Nome | Descrição |
  |------------------------------|---------------------------------------------------------------------------------------|
  | spring-boot-starter-web | Construindo aplicativos da web, inclui validação, REST. Usa o Tomcat como servidor incorporado padrão. |
  | spring-boot-starter-security | Adicionando suporte ao Spring Security. |
  | spring-boot-starter-data-jpa | Suporte ao banco de dados Spring com JPA e Hibernate. |
  | ... | |
- [Lista completa](https://github.com/spring-projects/spring-boot/tree/main/spring-boot-project/spring-boot-starters)

# 7. Spring Boot Dev Tools

- **O problema...**
  - Ao executar aplicativos Spring Boot.
    - Se você fizer alterações no seu código-fonte.
    - Então temos que reiniciar manualmente seu aplicativo.
- **Solução:** Spring Boot Dev Tools.
  - `spring-boot-devtools` para o resgate!
  - Reinicia automaticamente seu aplicativo quando o código é atualizado.
  - Basta adicionar a dependência ao seu arquivo POM.
  - Não há necessidade de escrever código adicional :-).
  - Para IntelliJ, é preciso definir configurações adicionais...
- Adicionando a dependência ao seu arquivo POM:
```xml
  <dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-devtools</artifactId>
    <scope>runtime</scope>
    <optional>true</optional>
  </dependency>
```
- Reinicia automaticamente seu aplicativo quando o código é atualizado.

## 7.1. IntelliJ Community Edition - DevTools
1. IntelliJ Community Edition não suporta DevTools por padrão.
   - **Selecione:** File > Settings > Build, Execution, Deployment > Compiler.
   - **Marque a caixa:** Build project automatically.
   - **Selecione:** File > Settings > Advanced Settings.
   - Marque a caixa: Allow auto-make to ...

2. Aplique as configurações do IntelliJ.

3. Edite `pom.xml` e adicione spring-boot-devtools.

4. Adicione um novo endpoint REST ao nosso aplicativo.

5. Verifique se o aplicativo é recarregado automaticamente.

## 8. Spring Boot Actuator
- **Problema...**
   - Como podemos monitorar e gerenciar meu aplicativo?
   - Como podemos verificar a saúde do aplicativo?
   - Como podemos acessar as métricas do aplicativo?

- **Solução: Spring Boot Actuator**
   - Expõe endpoints para monitorar e gerenciar seu aplicativo.
   - Facilmente obtemos funcionalidades de DevOps prontas para uso.
   - Basta adicionar a dependência ao seu arquivo POM.
   - Endpoints REST são **automaticamente** adicionados ao seu aplicativo.
   - Não é necessário escrever código adicional!
   - Obtemos novos endpoints REST de GRAÇA!
   - Adicionando a dependência ao seu arquivo POM:
     ```xml
       <dependency>
         <groupId>org.springframework.boot</groupId>
         <artifactId>spring-boot-starter-actuator</artifactId>
       </dependency>
     ```

   - Automaticamente expõe endpoints para métricas prontas para uso.
   - Endpoints são prefixados com: `/actuator`.

## 8.1. Endpoint de Saúde (Health Endpoint)
- `/health` verifica o status do seu aplicativo.
- Normalmente usado por aplicativos de monitoramento para ver se seu aplicativo está ativo ou inativo.
   - O status de saúde é personalizável com base na sua própria lógica de negócios.

## 8.2. Expondo Endpoints
- Por padrão, apenas `/health` é exposto.
- O endpoint `/info` pode fornecer informações sobre seu aplicativo.
- Para expor `/info`.
   - Arquivo: `src/main/resources/application.properties`.
   ```properties
     management.endpoints.web.exposure.include=health,info
     management.info.env.enabled=true
  ```

## 8.3. Info Endpoint
- `/info` dá informações sobre o seu aplicativo.
  - Por padrão, está vazio.
  - Atualize `application.properties` com as informações do seu app.
  - Arquivo: `src/main/resources/application.properties`
    ```properties
    info.app.name=Actuator Project
    info.app.description=An example project using Spring Boot Actuator.
    info.app.version=1.0.0
    ```

## 8.4. Endpoints do Spring Boot Actuator
- Existem mais de 10 endpoints do Spring Boot Actuator:
  | Nome        | Descrição                                                      |
  |-------------|----------------------------------------------------------------|
  | /auditevents| Eventos de auditoria do seu aplicativo                         |
  | /beans      | Lista de todos os beans registrados no contexto do Spring      |
  | /mappings   | Lista de todos os caminhos @RequestMapping                     |
  | ...         | ...                                                            |

## 8.5. Expondo Endpoints
- Por padrão, apenas `/health` é exposto.
- Para expor todos os endpoints do actuator via HTTP:
  - Arquivo: `src/main/resources/application.properties`
    ```properties
    # Use wildcard "*" para expor todos os endpoints
    # Também pode expor endpoints individuais com uma lista delimitada por vírgulas
    management.endpoints.web.exposure.include=*
    ```

## 8.6. Obter uma Lista de Beans
- Acesse http://localhost:8080/actuator/beans

## 8.7. Processo de Desenvolvimento
1. Edite `pom.xml` e adicione `spring-boot-starter-actuator`.
2. Veja os endpoints do actuator para: `/health`.
3. Edite `application.properties` para customizar `/info`.

## 8.8. Segurança
- **E a Segurança?**
  - Podemos **NÃO** querer expor todas essas informações.
- **Solução**
  - Adicione Spring Security ao projeto e os endpoints são protegidos.
    ```xml
    <dependency>
      <groupId>org.springframework.boot</groupId>
      <artifactId>spring-boot-starter-security</artifactId>
    </dependency>
    ```

### 8.8.1. Endpoints Protegidos
- Agora, quando acessarmos: `/actuator/beans`.
  - Spring Security solicitará login.
  - Nome de usuário padrão: **user**.
  - Verifique os logs do console para a senha.
- Podemos substituir o nome de usuário padrão e a senha gerada.
  - Arquivo: `src/main/resources/application.properties`
    ```properties
    spring.security.user.name=jefte
    spring.security.user.password=euamojesus
    ```
- Podemos customizar o Spring Security para o Spring Boot Actuator.
- Use um banco de dados para roles, senhas criptografadas, etc...

## 8.9. Excluindo Endpoints
- Para excluir `/health`
  - Arquivo: `src/main/resources/application.properties`
    ```properties
    management.endpoints.web.exposure.exclude=health
    ```
    
### 8.9.1. Processo de Desenvolvimento
1. Edite `pom.xml` e adicione `spring-boot-starter-security`.
2. Verifique a segurança nos endpoints do actuator para: `/beans` etc.
3. Desative endpoints para `/health` e `/info`.

## 8.10. Exemplo de Actuator
[Exemplo de Actuator](/Examples/actuator-project/)

# 9. Propriedades Personalizadas do Aplicativo
- **Problema**
  - Você precisa que seu app seja configurável ... sem valores codificados.
  - Você precisa ler a configuração do app a partir de um arquivo de propriedades.

- **Solução:**
  - Arquivo de Propriedades do Aplicativo.
  - Por padrão, o Spring Boot lê informações de um arquivo de propriedades padrão.
    - Localizado em: `src/main/resources/application.properties`
      - Nome de arquivo padrão do Spring Boot.
  - Você pode definir QUALQUER propriedade personalizada neste arquivo.
  - Seu app Spring Boot pode acessar propriedades usando `@Value`.
    - Nenhuma codificação ou configuração adicional necessária.

## 9.1. Processo de Desenvolvimento
1. Defina propriedades personalizadas em `application.properties`.
   1. Arquivo: `src/main/resources/application.properties`.
   2. ```properties
        books.name=Bíblia
        authors.name=Deus
      ```

2. Injete propriedades no aplicativo Spring Boot usando `@Value`.
```java
  @RestController
  public class MyRestController {
      @Value("${books.name}")
      private String book;

      @Value("${authors.name}")
      private String author;

      @GetMapping("/")
      public String GetBook() {
          return "Book: " + book + " By " + author;
      }
  }
```

## 9.2. Propriedades do Spring Boot
- O Spring Boot pode ser configurado no arquivo `application.properties`.
- Porta do servidor, caminho de contexto, actuator, segurança, etc ...
- O Spring Boot tem mais de 1.000 propriedades.
- As propriedades são agrupadas aproximadamente nas seguintes categorias:
  - Core
  - Web
  - Security
  - Actuator
  - Integration
  - DevTools
  - Data
  - Testing


### 9.2.1. Propriedades Core

```properties
  # Mapeamento de níveis de severidade de log
  logging.level.org.springframework=DEBUG
  logging.level.org.hibernate=TRACE
  logging.level.com.myfirstapp=INFO
  # Nome do arquivo de log
  logging.file.name=my-crazy-stuff.log
  logging.file.path=c:/myapps/demo
```

### 9.2.2. Propriedades Web

```properties
  # Porta do servidor HTTP
  server.port=7070
  # Caminho de contexto da aplicação
  server.servlet.context-path=/my-first-app
  # Tempo padrão de expiração da sessão HTTP
  server.servlet.session.timeout=
```

### 9.2.3. Propriedades do Actuator

```properties
  # Endpoints a serem incluídos por nome ou wildcard
  management.endpoints.web.exposure.include=*
  # Endpoints a serem excluídos por nome ou wildcard
  management.endpoints.web.exposure.exclude=beans,mapping
  # Caminho base para endpoints do actuator
  management.endpoints.web.base-path=/actuator
```

### 9.2.4. Propriedades de Segurança

```properties
  # Nome de usuário padrão
  spring.security.user.name=admin
  # Senha para o usuário padrão
  spring.security.user.password=
```

### 9.2.5. Propriedades de Dados

```properties
  # URL JDBC do banco de dados
  spring.datasource.url=jdbc:mysql://localhost:3306/ecommerce
  # Nome de usuário de login do banco de dados
  spring.datasource.username=admin
  # Senha de login do banco de dados
  spring.datasource.password=admin@123
```

# 10. Inversão de Controle e Injeção de Dependência
[IoC e Injeção de Dependência](https://github.com/jeftegoes/IoCAndDependencyInjectionOverviewWithExamples)

## 10.1. Tipos de Injeção
- Existem vários tipos de injeção com Spring.
- **Vamos abordar os dois tipos recomendados de injeção**
  - Injeção de Construtor
  - Injeção de Setter

### 10.1.1. Tipos de Injeção - Qual usar?
- **Injeção de Construtor**
  - Use isso quando você tiver dependências obrigatórias.
  - Geralmente recomendado pela equipe de desenvolvimento da spring.io como primeira escolha.

- **Injeção de Setter**
  - Use isso quando você tiver dependências opcionais.
  - Se a dependência não for fornecida, seu aplicativo pode fornecer uma lógica padrão razoável.

- **Injeção de Campo**
  - Não recomendado pela equipe de desenvolvimento da spring.io.
  - Nos primeiros dias, a injeção de campo era popular em projetos Spring.
    - Nos últimos anos, caiu em desuso.
  - Em geral, torna o código mais difícil de testar.
  - Como resultado, a equipe da spring.io não recomenda a injeção de campo.
    - No entanto, você ainda verá sendo usada em projetos legados.

### 10.1.2. O que é o Spring AutoWiring
- Para a injeção de dependência, o Spring pode usar `autowiring`.
- O Spring procurará uma classe que corresponda.
  - _corresponde por tipo: classe ou interface._
- O Spring irá injetá-lo automaticamente ... daí ser `autowired`.

## 10.2. Exemplo de Autowiring
- Injetando uma implementação `Payment`.
- O Spring fará a varredura por `@Components`.
- Alguém implementa a interface `Payment`???
- Se sim, vamos injetá-los. Por exemplo: `PixPayment`.

## 10.3. Aplicativo de Exemplo
![Aplicativo de Exemplo](/Images/DependencyInjectionExample.png)

## 10.4. Processo de Desenvolvimento - Injeção de Construtor
1. Defina a interface e classe da dependência.
2. Crie um Controller REST de Demonstração.
3. Crie um construtor na sua classe para injeções.
4. Adicione `@GetMapping` para `/discount`.

## 10.5. Spring para Aplicações Corporativas
- Spring é direcionado para aplicações corporativas, em tempo real / mundo real.
- O Spring fornece recursos como:
  - Acesso a banco de dados e Transações.
  - APIs REST e Web MVC.
  - Segurança.
  - etc ...

## 10.6. Scaneamento de Classes de Componente
- O Spring vai escanear suas classes Java para anotações especiais.
  - `@Component`, etc ...
- Registra automaticamente os beans no contêiner Spring.

## 10.7. Anotações
- `@SpringBootApplication` é composta pelas seguintes anotações:
  | Anotação              | Descrição                                                                 |
  |-----------------------|--------------------------------------------------------------------------|
  | @EnableAutoConfiguration | Habilita o suporte à auto-configuração do Spring Boot.                  |
  | @ComponentScan        | Habilita o escaneamento de componentes do pacote atual e subpacotes recursivamente. |
  | @Configuration        | Permite registrar beans extras ou importar outras classes de configuração.      |

## 10.8. Mais sobre o Escaneamento de Componentes
- Por padrão, o Spring Boot inicia o escaneamento de componentes.
  - Do mesmo pacote que sua aplicação principal do Spring Boot.
  - Também escaneia subpacotes recursivamente.
- Isso define implicitamente um pacote de busca base
  - Permite que você aproveite o escaneamento de componentes padrão.
  - Não é necessário referenciar explicitamente o nome do pacote base.

## 10.9. Injeção de Setter
- Injeção de Construtor.
- Injeção de Setter.
- **Injete dependências chamando métodos setter na sua classe**.
- Injetando uma implementação de Payment.
- O Spring vai escanear `@Components`
- Alguém implementa a interface Payment???
- Se sim, vamos injetá-los ... ops, qual deles?

## 10.10. Anotação @Primary
- Resolvendo problema com múltiplas implementações de Payment.
  - No caso de múltiplas implementações de Payment.
    - Resolvemos usando `@Qualifier`
    - Especificamos um pagamento pelo nome.
  - Solução alternativa disponível...

### 10.10.1. Solução Alternativa
- Em vez de especificar um pagamento pelo nome usando `@Qualifier`
- Eu simplesmente preciso de um pagamento ... não me importa qual pagamento
- Se houver múltiplos pagamentos
- Então, que os pagamentos resolvam ... e me digam qual é o `primary` pagamento

### 10.10.2. @Primary - Apenas um
- Ao usar `@Primary`, só pode haver um para múltiplas implementações.
- Se você marcar várias classes com @Primary ... bem, temos um problema.
- Misturando @Primary e @Qualifier
- Se misturarmos `@Primary` e `@Qualifier`
  - `@Qualifier` tem maior prioridade

### 10.10.3. Qual usar: @Primary ou @Qualifier?
- `@Primary` deixa para as classes de implementação decidirem.
  - Pode haver o problema de múltiplas classes `@Primary`, levando a um erro.
- `@Qualifier` permite que você seja bem específico sobre qual bean você quer.
- Em geral, recomendo usar `@Qualifier`
  - Mais específico.
  - Maior prioridade.

## 10.11. Inicialização Preguiçosa (Lazy Initialization)
- Por padrão, quando seu aplicativo inicia, todos os beans são inicializados.
  - `@Component`, etc ...
- O Spring criará uma instância de cada um e os disponibilizará.

### 10.11.1. Inicialização Preguiçosa
- Em vez de criar todos os beans de uma vez, podemos especificar inicialização preguiçosa.
- Um bean só será inicializado nos seguintes casos:
  - É necessário para injeção de dependência
  - Ou é explicitamente solicitado
- Adicione a anotação `@Lazy` a uma classe específica
- Para configurar outros beans para inicialização preguiçosa.
- Precisaríamos adicionar `@Lazy` a cada classe.
- Torna-se um trabalho tedioso para um grande número de classes.
- Eu gostaria que pudéssemos definir uma propriedade de configuração global ...

### 10.11.2. Vantagens e Desvantagens
- **Vantagens**
  - Criar objetos somente quando necessário.
  - Pode ajudar com o tempo de inicialização mais rápido se você tiver um grande número de componentes.
- **Desvantagens**
  - Pode não descobrir problemas de configuração até que seja tarde demais.
  - Se você tiver componentes relacionados à web, como @RestController, não serão criados até serem solicitados.
  - Precisa garantir que você tenha memória suficiente para todos os beans uma vez criados.
- **O recurso de inicialização preguiçosa é desativado por padrão.**
- **Você deve perfilar seu aplicativo antes de configurar a inicialização preguiçosa.**
- **Evite a armadilha comum da otimização prematura.**

## 10.12. Escopos de Bean
- Escopo refere-se ao ciclo de vida de um bean.
- Quanto tempo o bean vive?
- Quantas instâncias são criadas?
- Como o bean é compartilhado?

### 10.12.1. Escopo Padrão
- O escopo padrão é singleton
  - Relembrando: O que é um Singleton?
- O Spring Container cria apenas uma instância do bean, por padrão.
- Ele é armazenado em cache na memória.
- Todas as injeções de dependência para o bean
  - referenciarão o MESMO bean.

## 10.13. Escopos Adicionais de Bean do Spring
| Escopo       | Descrição                                                 |
|--------------|-----------------------------------------------------------|
| singleton    | Cria uma única instância compartilhada do bean. Escopo padrão. |
| prototype    | Cria uma nova instância de bean para cada solicitação do contêiner. |
| request      | Escopo para uma solicitação web HTTP. Usado apenas para aplicativos web. |
| session      | Escopo para uma sessão web HTTP. Usado apenas para aplicativos web. |
| application  | Escopo para um ServletContext de aplicativo web. Usado apenas para aplicativos web. |
| websocket    | Escopo para um web socket. Usado apenas para aplicativos web. |

## 10.14. Métodos do Ciclo de Vida do Bean - Anotações
- Podemos usar o Cliente Amazon S3 em nossa aplicação Spring
- A classe Cliente Amazon S3 não foi originalmente anotada com @Component
- No entanto, configuramos o Cliente S3 como um Bean Spring usando @Bean
- Agora é um Bean Spring e podemos injetá-lo em outros serviços da nossa aplicação
- Disponibilize uma classe de terceiros existente para o framework Spring

# 11. Comandos - Executar a partir da Linha de Comando
- Durante o desenvolvimento, passamos a maior parte do tempo na IDE.
- No entanto, podemos querer executar nosso aplicativo Spring Boot fora da IDE.
- Uma abordagem é executar a partir da linha de comando.
- Ao executar a partir da linha de comando.
- Não é necessário ter a IDE aberta/executando.
- Como estamos usando o Spring Boot, o servidor está embutido em nosso arquivo JAR.
- Não é necessário ter um servidor separado instalado/executando.
- Os aplicativos Spring Boot são **autossuficientes**.
- Duas opções para executar o aplicativo
  - Opção 1: Use `java -jar <my_jar_file.jar>`
  - Opção 2: Use o plugin Maven do Spring Boot
    - `mvnw spring-boot:run`
      
## 11.1. Comandos Maven
- **Execute a partir do prompt de comando!**
- Criar novo projeto Maven
  - `mvn archetype:generate -DgroupId=com.packagename -DartifactId=ClassName -DarchetypeArtifactId=maven-archetype-quickstart -DinteractiveMode=false`
- Executar projeto Spring Boot
  - `mvn spring-boot:run`
- Testar...
  - `mvn clean install -U`

## 11.2. Comandos Spring
- Lista de possibilidades
  - `spring init --list`
- Criar novo projeto Maven com Spring Boot
  - `spring init --type=maven-project --javaVersion=22 --artifactId=starter-spring-boot-project --groupId=com.starterpringbootproject`
  - `spring init --type=maven-project --javaVersion=22 --artifactId=starter-rest-controller --groupId=com.starterrestcontroller --dependencies=web,devtools,actuator,security`
    - spring-boot-devtools
    - spring-boot-starter-web
    - spring-boot-starter-security
    - spring-boot-starter-actuator
