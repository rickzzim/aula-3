# aula 3
# Processamento de Sinais de Áudio — Tons, Chirps e Simulação Acústica

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](COLOQUE_AQUI_O_LINK_DO_NOTEBOOK)

Este notebook explora conceitos fundamentais no processamento de sinais de áudio, abrangendo desde a geração de tons puros e sinais chirp até a simulação acústica de ambientes utilizando convolução. Ele serve como uma ferramenta prática para visualizar e ouvir como diferentes parâmetros de áudio afetam a percepção sonora e as representações no domínio do tempo.

> Material desenvolvido para fins didáticos, no contexto de uma disciplina de Processamento Digital de Sinais.

## Sumário

- [Requisitos](#requisitos)
- [Estrutura do repositório](#estrutura-do-repositório)
- [Conteúdo do notebook](#conteúdo-do-notebook)
  - [1. Geração e análise de sinais de tom puro](#1-geração-e-análise-de-sinais-de-tom-puro-ondas-senoidais)
  - [2. Geração e análise de sinais chirp](#2-geração-e-análise-de-sinais-chirp)
  - [3. Análise e reprodução de arquivos de áudio](#3-análise-e-reprodução-de-arquivos-de-áudio-domínio-do-tempo)
  - [4. Simulação acústica via convolução](#4-simulação-acústica-via-convolução)
- [Como usar](#como-usar)
- [Origem dos arquivos de áudio](#origem-dos-arquivos-de-áudio)
- [Licença](#licença)

## Requisitos

- Python 3.x
- [numpy](https://numpy.org/)
- [scipy](https://scipy.org/)
- [matplotlib](https://matplotlib.org/)
- [IPython](https://ipython.org/) (para `IPython.display.Audio`)

Se for executar localmente (fora do Colab):

```bash
pip install numpy scipy matplotlib ipython
```

## Estrutura do repositório

```
.
├── notebook.ipynb          # Notebook principal
├── audio/
│   ├── handel.wav           # Áudio de exemplo (domínio do tempo)
│   ├── h_banheiro.wav       # Resposta ao impulso de um banheiro (gravação própria)
│   └── sinal_taca.wav       # Sinal de áudio de uma taça (gravação própria)
└── README.md
```

> Ajuste os nomes/caminhos acima conforme a organização real do seu repositório.

## Conteúdo do notebook

### 1. Geração e Análise de Sinais de Tom Puro (Ondas Senoidais)

- **Objetivo:** Gerar e visualizar ondas senoidais com frequências específicas (500 Hz, 5000 Hz, 10000 Hz).
- **Experimento:** Observa-se como o aumento da frequência resulta em mais oscilações no mesmo intervalo de tempo, tornando o som percebido mais agudo.
- **Ferramentas:** `numpy` para geração de sinais, `matplotlib.pyplot` para visualização e `scipy.io.wavfile` junto com `IPython.display.Audio` para reprodução e salvamento em formato WAV.

### 2. Geração e Análise de Sinais Chirp

- **Objetivo:** Criar e analisar sinais chirp, onde a frequência varia gradualmente ao longo do tempo.
- **Experimento:** São gerados três tipos de chirp: linear, quadrático e logarítmico (exponencial), cada um com uma variação de frequência de 500 Hz a 10000 Hz. A visualização e a audição desses sinais demonstram como a frequência inicial grave se transforma em uma frequência final aguda, com diferentes curvas de aceleração de frequência.
- **Ferramentas:** `scipy.signal.chirp` é a função principal para a geração desses sinais.

### 3. Análise e Reprodução de Arquivos de Áudio (Domínio do Tempo)

- **Objetivo:** Carregar e visualizar o domínio do tempo de arquivos WAV existentes (`handel.wav`, `h_banheiro.wav`, `sinal_taca.wav`).
- **Experimento:** Demonstra-se como a alteração da frequência de reprodução (`rate` no `IPython.display.Audio`) impacta a percepção do áudio: frequências maiores aceleram e tornam o som mais agudo; frequências menores o desaceleram e tornam mais grave. Isso ilustra o conceito de taxa de amostragem na reprodução.
- **Ferramentas:** `scipy.io.wavfile.read` para leitura de arquivos WAV.

### 4. Simulação Acústica Via Convolução

- **Objetivo:** Simular o efeito acústico de um ambiente (representado por uma resposta ao impulso, `h_banheiro.wav`) em um sinal de áudio (`sinal_taca.wav`).
- **Experimento:** A convolução de um sinal de áudio com a resposta ao impulso de um banheiro (`h_banheiro.wav`) é realizada. O resultado é um sinal que simula como o som da taça seria percebido dentro de um ambiente com as características acústicas do banheiro (reverberação e eco). O gráfico resultante mostra um prolongamento e múltiplas reflexões no sinal.
- **Conceito:** A convolução é uma operação fundamental em processamento de sinais para modelar a interação de um sinal com um sistema linear e invariante no tempo (LTI), como um ambiente acústico.
- **Ferramentas:** `scipy.signal.convolve` para realizar a convolução.

## Como usar

1. **Execute as células:** Basta executar as células sequencialmente para observar a geração dos sinais, os gráficos no domínio do tempo e ouvir os exemplos de áudio.
2. **Experimente:** Altere os parâmetros dos sinais (frequência, duração, taxas de amostragem) e as taxas de reprodução para entender melhor seus efeitos.
3. **Explore:** Os arquivos `.wav` utilizados (`handel.wav`, `h_banheiro.wav`, `sinal_taca.wav`) são carregados do ambiente do Colab e representam diferentes tipos de áudio e respostas ao impulso.

## Origem dos arquivos de áudio

- `handel.wav`: arquivo de exemplo padrão (amplamente utilizado em material didático de processamento de sinais).
- `h_banheiro.wav` e `sinal_taca.wav`: gravações próprias, capturadas especificamente para este experimento de simulação acústica.

## Licença

Este projeto é disponibilizado **apenas para fins educacionais**. Não possui uma licença de código aberto formal — sinta-se à vontade para consultar o conteúdo como referência de estudo, mas reentre em contato antes de qualquer uso fora desse contexto.
