# Rust Commands

#### Criar novo projeto rust

```rust
$ cargo new [--lib] [nome_projeto]
```

O comando que você forneceu é utilizado para criar um novo projeto Rust usando o Cargo, que é o gerenciador de pacotes e sistema de build do Rust. Vamos detalhar o comando e suas partes:

- `$ cargo new`: Este é o comando básico para criar um novo projeto Rust. `cargo` é a ferramenta de linha de comando para gerenciar projetos Rust, e `new` é o subcomando usado para criar um novo projeto.

- `[--lib]`: Este é um argumento opcional que especifica o tipo de projeto a ser criado. Se você incluir `--lib`, o Cargo irá criar uma biblioteca Rust em vez de um projeto de aplicativo binário. Se você omitir este argumento, o Cargo criará um projeto de aplicativo binário por padrão. Os colchetes (`[]`) são usados na documentação para indicar que um argumento é opcional; você não os incluiria no comando real.

- `[nome_projeto]`: Este é o nome do seu novo projeto Rust. Você deve substituir `[nome_projeto]` pelo nome que deseja dar ao seu projeto. Este nome será usado como o nome do diretório que contém seu projeto e também como o nome do pacote para o seu projeto. Novamente, os colchetes são usados na documentação para indicar que este é um local onde você deve inserir um valor específico, e não são digitados literalmente.

Portanto, ao usar o comando `cargo new` sem `--lib`, você cria um novo projeto de aplicativo binário com um diretório chamado `nome_projeto`, que inclui uma estrutura de diretório padrão para um projeto Rust e um arquivo `Cargo.toml` inicial, que contém metadados do projeto necessários para o Cargo gerenciar dependências e build. Se você adicionar `--lib`, você instrui o Cargo a criar uma estrutura de projeto voltada para uma biblioteca Rust, o que muda ligeiramente a estrutura do diretório e o conteúdo do `Cargo.toml` para refletir esse propósito.