# Stocklite

Stocklite é um aplicativo mobile desenvolvido em Flutter para auxiliar no controle de estoque de produtos de uma despensa, estoque doméstico ou pequeno negócio. A proposta do projeto é oferecer uma experiência simples e visualmente limpa para cadastrar produtos, acompanhar quantidades, identificar itens com estoque baixo, organizar categorias e fornecedores, além de manter tudo sincronizado com Firebase em tempo real.

O projeto foi estruturado com uma arquitetura simples baseada em telas, controladores e serviços, separando responsabilidades para facilitar manutenção, expansão e entendimento do fluxo de dados. Ele combina autenticação de usuários, persistência em banco NoSQL (Firestore) e uma interface moderna com Material 3.

## O que o projeto faz

O aplicativo oferece um fluxo completo de gestão de estoque, incluindo:

- Cadastro, edição e exclusão de produtos.
- Controle de quantidade disponível em estoque.
- Definição de quantidade mínima para alertar itens que precisam ser repostos.
- Cálculo de custo estimado para reposição com base nos produtos abaixo do limite mínimo.
- Busca por nome de produto.
- Filtro por categoria.
- Ordenação de produtos por nome ou preço.
- Alternância entre visualização em lista e em grade.
- Gestão de categorias e fornecedores.
- Identificação visual de produtos com estoque baixo.
- Busca de nome de produto por código de barras utilizando a API pública OpenFoodFacts.
- Autenticação de usuários com login, cadastro, recuperação de senha e validação de senha forte.
- Armazenamento dos dados por usuário, garantindo isolamento dos dados no Firebase.

## O que o projeto é

Stocklite é um aplicativo de gestão de estoque com foco em usabilidade e simplicidade. Ele foi pensado para quem precisa controlar itens de casa, pequenos estoques de produtos de consumo, produtos vendidos em pequenas rotinas comerciais ou até um estoque básico para uso pessoal.

A aplicação não é um ERP completo, mas sim uma solução leve, prática e acessível para operações básicas de controle. O projeto mistura recursos de cadastro, consulta, organização e monitoramento de estoque em um fluxo de tela simples e responsivo.

## Funcionalidades principais

### 1. Autenticação e conta do usuário

A aplicação possui um fluxo completo de autenticação:

- Tela de login com e-mail e senha.
- Tela de cadastro com nome, telefone, e-mail e senha.
- Validação de senha com regras fortes: tamanho mínimo, letra maiúscula, letra minúscula, número e caractere especial.
- Recuperação de senha via envio de e-mail pelo Firebase Auth.
- Armazenamento de informações adicionais do usuário no Firestore.

### 2. Gestão de produtos

Na tela principal, o usuário pode:

- Adicionar um novo produto com nome, preço, quantidade, quantidade mínima, categoria e fornecedor.
- Editar um produto já existente.
- Excluir um produto com confirmação.
- Ajustar a quantidade diretamente com botões de + e -.
- Visualizar se o item está com estoque baixo.

### 3. Busca, filtros e organização

A tela de catálogo permite:

- Buscar produtos por nome.
- Filtrar produtos por categoria.
- Alternar entre lista e grade.
- Ordenar produtos por nome crescente/decrescente e por preço crescente/decrescente.

### 4. Gestão de categorias e fornecedores

O módulo de resumo permite:

- Criar categorias.
- Editar categorias.
- Excluir categorias.
- Criar fornecedores.
- Editar fornecedores.
- Excluir fornecedores.

Essas informações são usadas para organizar os produtos cadastrados e melhorar a navegação no catálogo.

### 5. Alertas de reposição

A tela de resumo mostra:

- Quantidade total de produtos únicos cadastrados.
- Custo estimado para repor os itens abaixo do estoque mínimo.
- Lista de produtos com estoque baixo ou igual ao mínimo.

### 6. Integração com código de barras

Na tela de cadastro de produto, há um campo para código de barras. Ao pesquisar, a aplicação consulta a API do OpenFoodFacts para tentar recuperar o nome do produto automaticamente. Isso facilita a inserção de produtos com base em dados públicos.

## Estrutura do projeto

A estrutura principal do projeto está organizada em:

- lib/main.dart: ponto de entrada da aplicação.
- lib/modules/auth: telas e controladores de autenticação, cadastro e recuperação de senha.
- lib/modules/home: telas e controladores da área principal do app, incluindo catálogo, resumo, busca, cadastro e edição de produtos.
- lib/modules/about: tela de informações sobre o projeto.
- lib/data/models: modelos de dados como produto, categoria, fornecedor.
- lib/data/services: serviços para comunicação com Firebase Firestore e lógica de persistência.
- lib/firebase_options.dart: configuração de conexão com o Firebase para cada plataforma.

## Tecnologias e bibliotecas utilizadas

O projeto utiliza principalmente:

- Flutter e Dart.
- Material 3 para a interface.
- Firebase Authentication para autenticação de usuários.
- Cloud Firestore para armazenamento de dados.
- Provider para gerenciamento de estado simples.
- Device Preview para visualização da interface em diferentes tamanhos de tela durante desenvolvimento.
- intl_phone_number_input para entrada de telefone com máscara e seleção de país.
- http para integração com a API OpenFoodFacts.

## Requisitos para rodar o projeto

Antes de executar o projeto, você precisará ter instalado:

- Flutter SDK 3.8.1 ou superior.
- Dart SDK compatível com a versão do Flutter instalada.
- Android Studio ou VS Code com extensões para Flutter e Dart.
- Um emulador Android ou um dispositivo Android conectado.
- Opcionalmente, Xcode para rodar em iOS, se você estiver em macOS.
- Uma conta no Firebase.
- Git para clonar o repositório.

## Como instalar o Flutter

Se ainda não tiver o Flutter instalado, siga os passos oficiais:

1. Acesse o site do Flutter.
2. Baixe a versão estável compatível com o seu sistema operacional.
3. Extraia o SDK para uma pasta de sua preferência.
4. Adicione o Flutter ao PATH do sistema.
5. Execute o comando:

```bash
flutter doctor
```

Esse comando valida se todas as dependências necessárias estão corretas.

## Como rodar o projeto

### 1. Clone o repositório

```bash
git clone <url-do-repositorio>
cd STOCKLITE
```

### 2. Instale as dependências

```bash
flutter pub get
```

### 3. Verifique se o ambiente está pronto

```bash
flutter doctor
```

### 4. Configure o Firebase

Este projeto já possui um arquivo de configuração de Firebase em [lib/firebase_options.dart](lib/firebase_options.dart), mas é importante garantir que ele corresponda ao seu projeto real no Firebase.

Se você estiver usando um projeto Firebase diferente, é recomendável regenerar as opções com o FlutterFire:

```bash
flutterfire configure
```

Além disso, certifique-se de que:

- o projeto Firebase esteja criado;
- o Authentication esteja habilitado com e-mail/senha;
- o Firestore esteja habilitado;
- o arquivo google-services.json esteja configurado para Android;
- o arquivo GoogleService-Info.plist esteja configurado para iOS.

### 5. Execute o aplicativo

Para Android:

```bash
flutter run
```

Ou para um dispositivo específico:

```bash
flutter run -d <device-id>
```

Para web:

```bash
flutter run -d chrome
```

Para um emulador Android já aberto:

```bash
flutter devices
flutter run -d <emulador>
```

## Estrutura de dados no Firebase

A aplicação utiliza o Firestore com a seguinte lógica de organização:

- Coleção usuarios
  - Documento por usuário autenticado
  - Subcoleção products: produtos do usuário
  - Subcoleção categories: categorias do usuário
  - Subcoleção suppliers: fornecedores do usuário

Essa estrutura permite que cada conta tenha seus próprios dados isolados.

## Observações importantes

- O projeto usa autenticação real, então um usuário precisa criar uma conta antes de utilizar o app de forma completa.
- O app depende de uma conexão com o Firebase para criar contas, logar, salvar produtos e sincronizar dados.
- A integração com a API OpenFoodFacts depende de conexão com a internet e pode não retornar resultados para todos os produtos.
- Para desenvolvimento, o Device Preview fica ativo em modo não release.

## Comandos úteis

Se precisar limpar e reinstalar dependências:

```bash
flutter clean
flutter pub get
```

Se quiser validar o projeto após alterações:

```bash
flutter analyze
```

## Resumo em uma frase

Stocklite é um aplicativo Flutter para controlar estoque de produtos com autenticação, persistência em Firebase, organização por categorias/fornecedores e alertas de reposição de itens.
