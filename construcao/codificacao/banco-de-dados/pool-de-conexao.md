# Gerenciamento de Pool de Conexões
Quando um processo do DTM ou o processo do Serviço de Integração de Dados executa um trabalho, ele solicita uma instância de conexão do pool. Se existir uma instância de conexão inativa, o pool de conexões a liberará para o processo do DTM ou o processo do Serviço de Integração de Dados. Se o pool de conexões não tiver uma instância de conexão inativa, o processo do DTM ou o processo do Serviço de Integração de Dados criará uma instância de conexão ativa.

Quando o processo do DTM ou o processo do Serviço de Integração de Dados conclui o trabalho, ele libera a instância de conexão ativa para o pool como uma instância de conexão inativa. Se o pool de conexões contiver o número máximo de instâncias de conexão inativas, o Serviço de Integração de Dados descartará a instância de conexão ativa, em vez de liberá-la para o pool.

O processo do DTM ou o processo do Serviço de Integração de Dados descarta um instância de conexão inativa do pool quando as seguintes condições são verdadeiras:
- Uma instância de conexão alcança o tempo de inatividade máximo.
- O pool de conexões excede o número mínimo de conexões inativas.

Quando você atualiza o nome de usuário, a senha ou a cadeia de conexão para uma conexão de banco de dados que tenha o pool de conexões habilitado, as atualizações entram em vigor imediatamente. As solicitações de conexão subsequentes usam as informações atualizadas. Além disso, a biblioteca de pool de conexões descarta todas as conexões inativas e reinicia o pool de conexões. Ela não retorna nenhuma instância de conexão ativa no momento da reinicialização para o pool de conexões quando está concluída.

Se você alterar qualquer outra propriedade de conexão de banco de dados, deverá reiniciar o Serviço de Integração de Dados para aplicar as atualizações.

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

# Exemplo de um pool de conexões

Você deseja usar os pools de conexões para otimizar o desempenho da conexão. Você configurou o Serviço de Integração de Dados para executar tarefas em processos locais separados.

Você configura os seguintes parâmetros de pool para uma conexão:
- Pool de conexões: Ativado
- Mínimo de Conexões: 2
- Máximo de Conexões: 4
- Tempo máximo de inatividade: 120 segundos

Quando um processo do DTM executa cinco trabalhos, ele usa o seguinte processo para manter o pool de conexões:
1. O processo do DTM recebe uma solicitação para processar cinco trabalhos às 11h e cria cinco instâncias de conexão.
1. O processo do DTM conclui o processamento às 11h30 e libera quatro conexões para o pool de conexões como conexões inativas.
1. Ele descarta uma conexão porque ela excede o tamanho do pool de conexões.
1. Às 11:32, o tempo de inatividade máximo é atingido para as conexões inativas e o processo do DTM descarta duas conexões inativas.
1. O processo do DTM mantém duas conexões inativas porque o tamanho mínimo do pool de conexões é dois.


# Referência
- [Gerenciamento de Pool de Conexões](https://docs.informatica.com/pt_pt/data-engineering/shared-content-for-data-engineering/10-2-2/guia-de-servicos-de-aplicativo/gerenciamento-do-servico-de-integracao-de-dados/manter-pools-de-conexoes/gerenciamento-de-pool-de-conexoes.html)
- [Propriedades do Pool em Objetos de Conexão](https://docs.informatica.com/pt_pt/data-engineering/shared-content-for-data-engineering/10-2-2/guia-de-servicos-de-aplicativo/gerenciamento-do-servico-de-integracao-de-dados/manter-pools-de-conexoes/propriedades-do-pool-em-objetos-de-conexao.html)
- [Exemplo de um pool de conexões](https://docs.informatica.com/pt_pt/data-engineering/shared-content-for-data-engineering/10-2-2/guia-de-servicos-de-aplicativo/gerenciamento-do-servico-de-integracao-de-dados/manter-pools-de-conexoes/exemplo-de-um-pool-de-conexoes.html)
