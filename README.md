# Núcleo

Aplicativo mobile gamificado, feito em **Flutter** (Android, iOS e Web), que ajuda a
população a entender a energia nuclear de forma leve, didática e sem medo.

> Projeto da disciplina Mobile Application Development — **Entrega do 1º Sprint**.

## Integrantes da equipe

- Cassio Alexandre Ribeiro de Moraes — RM 567295
- Davi Isac Colin Pereira — RM 567265
- Hugo Souza de Jesus — RM 568542
- Matheus Peres Moraes de Jesus — RM 567300
- Pedro Gonçalves Rodrigues — RM 567651

## Empresa / parceiro

**Amazul** — a dor do cliente é a falta de informação sobre energia nuclear para todos
os públicos e o medo que isso gera na população.

## Descrição da solução

O Núcleo transforma o tema "energia nuclear" em jogos curtos, com ranking e convites entre
usuários (com bonificações, como _skins_, em evolução futura).

| Tela                 | Rota         | O que faz                                                                                                                       |
| -------------------- | ------------ | ------------------------------------------------------------------------------------------------------------------------------- |
| Home                 | `/`          | Explica o projeto, mostra os benefícios da tecnologia nuclear, os desafios, o nível e o ranking da semana                       |
| Mito ou Verdade      | `/mito`      | Cartões de arrastar (direita = verdade, esquerda = mito) com explicação imediata após cada resposta                             |
| Equilíbrio da Cidade | `/cidade`    | O jogador monta a matriz energética e equilibra carbono, custo e estabilidade. Só vence com a energia nuclear como base estável |
| Login / Cadastro     | `/login`     | Formulário com validação (e-mail, senha, nome e aceite de termos)                                                               |
| CRUD de perguntas    | `/perguntas` | Cria, edita e exclui as afirmações usadas no jogo Mito ou Verdade                                                               |

> Nesta Sprint os dados são **mockados** (ficam apenas em memória). Não há banco de dados
> nem serviços externos.

## Requisitos da Sprint atendidos

- **Navegação entre telas:** `Navigator` com rotas nomeadas (`onGenerateRoute`), 5 telas,
  botão voltar, barra inferior e passagem de parâmetros (nome do usuário enviado do Login
  para a Home via `arguments`; formulário de pergunta recebe a pergunta e devolve os dados
  com `Navigator.pop`).
- **Protótipo visual funcional:** `Scaffold`, `AppBar`/cabeçalho próprio, `Column`, `Row`,
  `Container`, `Padding`, `SizedBox`, `Card`, `Image`, `Icon`, `ListView` e `GridView`,
  com paleta e tipografia padronizadas em `lib/theme`.
- **Gerenciamento de estado:** `StatefulWidget` + `setState()` nos jogos (pontuação,
  carta arrastada, contadores de fontes de energia), no formulário e no login. Um
  `ChangeNotifier` simples (`lib/state/app_state.dart`) só compartilha os dados mockados
  entre as telas (XP, ranking, perguntas).
- **Formulário e validação:** `Form`, `GlobalKey<FormState>`, `TextFormField`, `Checkbox`,
  validações de campo e resposta ao usuário com `SnackBar` e `Dialog`.

## Identidade visual

Paleta com a regra 60/30/10:

| Uso                        | Cor   | Hex       |
| -------------------------- | ----- | --------- |
| 60% — fundos e superfícies | Creme | `#FFF5F5` |
| 30% — ações e destaques    | Azul  | `#1971C2` |
| 10% — contraste e texto    | Navy  | `#0B1F3A` |

## Como executar

**Pré-requisitos:** [Flutter](https://docs.flutter.dev/get-started/install) instalado
(`flutter doctor` sem erros), Git e, para Android, o Android Studio com um emulador criado
(ou um celular com depuração USB ativada).

```bash
# 1. Clonar o repositório
git clone https://github.com/nucleo-challenge/Mobile-Application-Development.git
cd Mobile-Application-Development

# 2. Baixar as dependências
flutter pub get

# 3. Ver os dispositivos disponíveis (emulador, celular, Chrome)
flutter devices

# 4. Executar
flutter run                # usa o dispositivo disponível
flutter run -d chrome      # versão Web
flutter run -d <id>        # dispositivo específico (id mostrado no passo 3)
```

Se as pastas `android/`, `ios/` e `web/` ainda não existirem no projeto, gere-as uma única vez:

```bash
flutter create . --project-name nucleo_app --platforms=android,ios,web
```

Testes automatizados:

```bash
flutter test
```

## Como usar o aplicativo

1. **Home:** leia a apresentação do projeto e toque em **Começar jornada** ou escolha um
   desafio. Seu nível, o progresso nos jogos e o ranking da semana aparecem aqui.
2. **Mito ou Verdade:** leia a afirmação do cartão e **arraste para a direita (Verdade)** ou
   **para a esquerda (Mito)**. Também é possível usar os botões na parte de baixo. Depois de
   cada resposta, uma explicação aparece na tela. Cada acerto vale 100 XP.
3. **Equilíbrio da Cidade:** use **+** e **−** para montar a matriz energética (até 8 fontes
   no total, no máximo 3 de cada). Acompanhe as barras de **carbono**, **custo** e
   **estabilidade** e toque em **Avaliar minha cidade**. A cidade só fica equilibrada com
   energia nuclear como base estável.
4. **Login:** toque no avatar no canto superior direito. Informe um e-mail válido e uma senha
   com pelo menos 6 caracteres, ou toque em **Criar uma conta**. Os dados são fictícios:
   qualquer e-mail e senha válidos funcionam.
5. **Perguntas (CRUD):** na barra inferior, abra **Perguntas** para criar uma nova pergunta
   (**Nova pergunta**), **editar** ou **excluir** as existentes. As mudanças já valem para o
   jogo Mito ou Verdade.
6. **Convide amigos:** na Home, toque em **Convide amigos** para ver e copiar seu código.

> Os dados ficam apenas em memória: ao fechar o app, tudo volta ao estado inicial.

## Estrutura do projeto

```
lib/
├── main.dart              # MaterialApp, rotas e layout responsivo
├── routes.dart            # Nomes das rotas e navegação da barra inferior
├── theme/                 # Paleta de cores e tema
├── models/                # Question, RankEntry
├── data/                  # Dados mockados
├── state/                 # Estado compartilhado entre as telas
├── widgets/               # Botão, cabeçalho, barra inferior e componentes comuns
└── screens/               # Home, jogos, login e CRUD de perguntas
assets/images/logo.png     # Logo do Núcleo
```

## Tecnologias utilizadas

- Flutter e Dart
- Material Design 3
- Git e GitHub
- Figma (protótipo de interface)

## Vídeo de demonstração

[Assistir ao vídeo](https://youtu.be/UMFL_F24nl4)
