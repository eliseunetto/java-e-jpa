# JAVA e JPA

## Persista seus objetos com a JPA2 e Hibernate

### Tópicos:
1. **Sobre a JAVA Persistence API** \
  1.1   Escrever SQL no código Java é trabalhoso e precisa de manutenção contínua \
  1.2   A JPA é um ORM (*Object Relacional Mapper*) Java 
    * Um ORM mapeia as classes para tabelas e gera o SQL de forma automática 

   1.3   Para inicializar a JPA, é preciso definir um arquivo de configuração, chamado **persistence.xml** 
    * Nele, colocamos as configurações mais importantes, como o driver e os dados da conexão 

   1.4   A classe `Persistence` lê a configuração e cria uma `EntityManagerFactory` \
  1.5   Podemos usar a JPA para gerar e atualizar as tabelas no banco de dados \
  1.6   Uma entidade deve usar as anotações `@Entity` e `@Id`
    *   `@GeneratedValue` não é obrigatório, mas pode ser útil para definir uma *chave auto-increment*

2. **Usando EntityManager** \
  2.1   A JPA sincroniza o estado de uma entidade gerenciada com o banco de dados 
    * Isto é, o SQL será gerado baseado na diferença entre a entidade em memória e o banco de dados 
    * Para essa sincronização acontecer, a entidade precisa estar gerenciada (*Managed*) 
  
   2.2   Os estados de uma entidade são: *Managed*, *Detached*, *Transient* e *Removed* \
   2.3   Os métodos do `EntityManager`, como `persist`, `merge` ou `remove` alteram o estado da entidade

3. **Mapeando Relacionamentos** \
  3.1   Relacionamentos entre entidades precisam ser configurados pelas anotações no atributo que define o relacionamento na classe \
  3.2   Um relacionamento do tipo *Muitos-para-Um* deve usar anotação a `@ManyToOne` 
    * A anotação `@ManyToOne` causa a criação de uma chave estrangeira

   3.3   A JPA carrega automaticamente o relacionamento ao carregar a entidade

4. **Relacionamento para Muitos** \
  4.1   Como relacionar uma entidade com uma coleção de uma outra entidade
    * Para tal, temos as anotações `@OneToMany` e `@ManyToMany`, dependendo da cardinalidade
    * Um relacionamento `@*ToMany` precisa de uma tabela extra para a representação no banco de dados

   4.2   Aprendemos também como relacionar uma entidade com uma outra entidade
    * Para tal, temos as anotações `@OneToOne` e `@ManyToOne`, dependendo da cardinalidade

   4.3   Ao persistir uma entidade, devemos persistir as entidades transientes do relacionamento

5. **Pesquisando com JPQL** \
  5.1   Como executar queries com JPA, usando **JPQL**
    * A linguagem JPQL é bem parecida com SQL, no entanto orientada a objetos
    * Com JPQL, usamos as classes e atributos (no lugar das tabelas e colunas) para definir a pesquisa
    * O objeto do tipo `javax.persistence.Query` encapsula a query `javax.persistence.TypedQuery` é a versão tipada do `javax.persistence.Query`
