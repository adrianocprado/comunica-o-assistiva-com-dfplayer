# Comunicador Assistivo de 4 Botões (DFPlayer Mini)

Dispositivo portátil de comunicação alternativa, simples e de baixo custo. Ao apertar um dos **4 botões**, ele reproduz em voz alta uma frase pré-gravada. Os áudios ficam em um **cartão microSD** dentro do módulo **DFPlayer Mini**.

Não usa microcontrolador nem programação: os botões são ligados à entrada **ADKEY** do DFPlayer por **resistores** (esquema sugerido no datasheet do módulo), e o próprio DFPlayer toca o áudio correspondente.

> **Expansão:** o dispositivo pode ser expandido **até 14 botões**, cada um com uma frase diferente. Veja a seção [Expansão](#expansão-até-14-botões).

## Características

- 4 botões, cada um com uma frase diferente
- Voz reproduzida por alto-falante ligado direto ao DFPlayer
- Bateria recarregável 18650 com módulo de carga e proteção TP4056
- Porta USB **somente para carregar** a bateria
- Áudios em **cartão microSD**, trocáveis com um leitor externo (é preciso abrir o aparelho)
- Sem código, sem Wi-Fi: liga e usa
- Expansível até 14 botões

## Lista de materiais

| Qtd | Item | Observação |
|----:|------|------------|
| 1 | Módulo **DFPlayer Mini** | Toca MP3/WAV do cartão microSD |
| 1 | Cartão **microSD** | Formatado em FAT32 |
| 1 | Módulo carregador **TP4056 com proteção** | Carrega a bateria pela porta USB |
| 1 | Bateria **18650** Li-ion 3,7 V | De boa procedência |
| 1 | Alto-falante | Confira a impedância e a potência suportadas pelo DFPlayer (4 Ω / 3 W na versão documentada) |
| 4 | Botões de pressão (push-button) | |
| 3 | Resistores: 3 kΩ, 6,2 kΩ e 9,1 kΩ | O botão 1 liga direto (0 Ω) |
| 1 | Chave **liga/desliga** | Em série com a alimentação do DFPlayer |
| 1 | Porta USB de painel (carga) | Alimenta apenas o TP4056 |
| – | Caixa, placa perfurada, fios, cola quente, suporte da bateria, etiquetas | |

## Como funciona

```
Porta USB ──► TP4056 ◄──► Bateria 18650
                │
                └─ OUT+ ─► [chave] ─► DFPlayer (VCC) ──► Alto-falante
                   OUT− ──────────────► DFPlayer (GND)
                                           ▲
          4 botões ──► resistores ──► ADKEY1
```

- O **TP4056** carrega a bateria e a protege contra sobrecarga, descarga excessiva e curto-circuito.
- A saída do TP4056 alimenta o **DFPlayer Mini** pela chave liga/desliga.
- Os **4 botões** ficam na entrada **ADKEY1**, cada um em série com um resistor de valor diferente. O DFPlayer identifica o botão pela tensão e toca a faixa correspondente.
- O DFPlayer tem amplificador interno e aciona diretamente o **alto-falante**.

Esquema completo em [`docs/esquema-ligacao.svg`](docs/esquema-ligacao.svg) (versão em PDF: [`docs/diagrama-ligacoes.pdf`](docs/diagrama-ligacoes.pdf)):

![Esquema de ligação](docs/esquema-ligacao.svg)

## Expansão até 14 botões

O DFPlayer aceita até **14 botões de frases** (segmentos 1 a 14) usando as duas entradas **ADKEY1** e **ADKEY2**, cada botão com o seu resistor. Basta acrescentar botões, resistores e arquivos de áudio. A tabela de resistores está no [manual técnico](docs/MANUAL.md#5-expansão-até-14-botões).

## Uso rápido

1. Carregue a bateria conectando um carregador USB comum (5 V) à porta USB.
2. Ligue o aparelho na chave liga/desliga e aperte um botão: a frase correspondente é reproduzida.
3. Para trocar as frases, abra o aparelho, retire o cartão microSD e grave os novos arquivos em um computador, com um leitor de cartão externo (veja o manual).

## Documentação

- **[`docs/MANUAL.md`](docs/MANUAL.md)** – manual técnico: ligações, montagem, cartão SD, expansão e solução de problemas (também em [PDF](docs/MANUAL.pdf))
- **[`docs/MANUAL-USUARIO.md`](docs/MANUAL-USUARIO.md)** – manual do usuário final (também em [PDF](docs/MANUAL-USUARIO.pdf))
- **[`docs/esquema-ligacao.svg`](docs/esquema-ligacao.svg)** – esquema de ligação

## Estrutura do repositório

```
.
├── README.md
└── docs/
    ├── MANUAL.md
    ├── MANUAL.pdf
    ├── MANUAL-USUARIO.md
    ├── MANUAL-USUARIO.pdf
    ├── esquema-ligacao.svg
    └── diagrama-ligacoes.pdf
```

## Segurança

Este projeto usa uma bateria de íon-lítio. Use sempre o módulo TP4056 **com proteção**, não perfure nem esmague a bateria, evite curto-circuitos e não deixe o dispositivo carregando sem supervisão em superfícies inflamáveis. Se a bateria inchar, esquentar demais ou cheirar estranho, pare de usar. Por ser um dispositivo para crianças ou pessoas com necessidades de apoio, mantenha a tampa da caixa **parafusada**.

## Licença

Defina a licença do seu projeto (por exemplo, MIT para o código/documentação e CC BY-SA 4.0 para os materiais de hardware) e adicione um arquivo `LICENSE`.

## Contribuições

Melhorias, correções e adaptações (outras frases, mais botões, outros idiomas) são bem-vindas via *issues* e *pull requests*.
