# My8Way

link : https://youtu.be/-TgrZK7HE4I

Jogo 2D individual feito na Unity. O jogador se move em 8 direções pela cena e coleta objetos. Quando todos os coletáveis são pegos, aparece a tela de fim de jogo.

## Como jogar

- **Mover:** setas ou `W` `A` `S` `D` (eixos `Horizontal` e `Vertical` do Input Manager).
- **Objetivo:** coletar os 5 objetos com a tag `Coletavel`.
- Cada coletável pego toca um som de moeda e é removido da cena.
- Ao coletar todos, o painel de fim de jogo é exibido e é possível voltar ao menu.

## Requisitos

- Unity **6000.3.26f1** (Unity 6.3)
- Render pipeline: Universal Render Pipeline (2D)

## Como rodar

1. Clone o repositório.
2. No Unity Hub, clique em **Add** e selecione a pasta `My8Way/`.
3. Abra o projeto com a versão da Unity indicada acima.
4. Abra a cena `Assets/Scenes/MainMenu.unity` e aperte **Play**.

## Estrutura

```
My8Way/
├── Assets/
│   ├── Scenes/
│   │   ├── MainMenu.unity      # cena 0: menu inicial
│   │   └── SampleScene.unity   # cena 1: o jogo
│   ├── _Scripts/
│   │   ├── GameController.cs   # estado do jogo (contagem de coletáveis)
│   │   ├── MenuActions.cs      # botões: iniciar jogo e voltar ao menu
│   │   ├── PlayerMovement.cs   # movimento 8 direções e coleta
│   │   └── UIManager.cs        # mostra o painel de fim de jogo
│   ├── Player.prefab
│   └── Triangle.prefab
├── Packages/
└── ProjectSettings/
```

## Scripts

| Script | Função |
| --- | --- |
| `GameController` | Classe estática. `Init()` define 5 coletáveis, `Collect()` desconta um e `gameOver` fica `true` quando chegam a 0. |
| `PlayerMovement` | Move o `Rigidbody2D` com velocidade `speed` (direção normalizada, então na diagonal não é mais rápido). Detecta o trigger com a tag `Coletavel`, toca o áudio e destrói o objeto. |
| `MenuActions` | `IniciaJogo()` reinicia o contador e carrega a cena 1. `Menu()` carrega a cena 0. |
| `UIManager` | Ativa o `endGamePanel` quando `GameController.gameOver` é verdadeiro. |

## Créditos

- Efeito sonoro de moeda: [Freesound](https://freesound.org/) (`freesound_gamestudio-drop-coin-384921.mp3`).
