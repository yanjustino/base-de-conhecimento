# Propriedades do Pool em Objetos de Conexão
Você pode editar as propriedades do pool de conexões na exibição Pool de uma conexão de banco de dados.

O número de bibliotecas do pool conexão depende do número de processos do Serviço de Integração de Dados ou do DTM em execução. Cada processo do Serviço de Integração de Dados ou do DTM mantém sua própria biblioteca de pool de conexões. Os valores das propriedades do pool destinam-se a cada biblioteca de pool de conexões.

Por exemplo, se você definir o máximo de conexões como 15, cada biblioteca de pools de conexão poderá ter no máximo 15 conexões inativas no pool. Se o Serviço de Integração de Dados executar os trabalhos em processos locais separados e três processos do DTM estiverem em execução, você poderá ter um máximo de 45 instâncias conexão ociosas.

Para reduzir o número total de instâncias de conexões inativas, defina o número mínimo de conexões como 0 e reduza o tempo máximo de inatividade para cada conexão de banco de dados.

A lista a seguir descreve as propriedades do pool de conexões de banco de dados que podem ser editadas na exibição Pool para uma conexão de banco de dados:

- Ativar Pool de Conexões
  - Ativa o pool de conexões. Quando você ativa o pool de conexões, cada pool de conexão retém as instâncias de conexões inativas na memória. Para excluir o pool de conexões inativas, você deve reiniciar o Serviço de Integração de Dados.
  - Se o pool de conexões for desativado, o processo do DTM ou o processo do Serviço de Integração de Dados interromperá todas as atividades de pool. O processo do DTM ou o processo do Serviço de Integração de Dados cria uma instância de conexão sempre que processa um trabalho. Ele descarta a instância ao concluir o processamento do trabalho.
  - O padrão é ativado para conexões DB2 para i5/OS, DB2 para z/OS, IBM DB2, Microsoft SQL Server, Oracle e ODBC. O padrão é desativado para conexões Adabas, IMS, Sequenciais e VSAM.
  - O padrão é ativado para Microsoft SQL Server, IBM DB2, Oracle e conexões ODBC.

- Nº Mínimo de Conexões
  - O número mínimo de instâncias de conexões inativas que um pool mantém para uma conexão de banco de dados depois que o tempo de inatividade máximo é atingido. Defina esse valor como igual ou menor que o número máximo de instâncias de conexões inativas. O padrão é 0.
- Nº Máximo de Conexões
  - O número máximo de instâncias de conexões inativas que um pool mantém para uma conexão de banco de dados antes que o tempo máximo de inatividade seja atingido. Defina esse valor como sendo maior que o número mínimo de instâncias de conexões inativas. O padrão é 15.
- Tempo de Inatividade Máximo
  - O número de segundos pelo qual uma instância de conexão que excede o número mínimo de instâncias de conexão pode permanecer inativa antes de ser descartada pelo pool de conexões. O pool de conexões ignora o tempo ocioso quando a instância de conexão não excede o número mínimo de instâncias de conexões inativas. O padrão é 120.

# Referência
- [Propriedades do Pool em Objetos de Conexão](https://docs.informatica.com/pt_pt/data-engineering/shared-content-for-data-engineering/10-2-2/guia-de-servicos-de-aplicativo/gerenciamento-do-servico-de-integracao-de-dados/manter-pools-de-conexoes/propriedades-do-pool-em-objetos-de-conexao.html)
