# TCC — Modelos de Sobrevida em LUAD e LUSC

Este repositório organiza os notebooks do TCC para análise de sobrevida em câncer de pulmão de não pequenas células, considerando os subtipos LUAD e LUSC.

## Objetivo

Comparar modelos estatísticos, machine learning e deep learning para predição de sobrevida global (`OS`) em LUAD e LUSC, usando dados clínicos e expressão gênica do TCGA/UCSC Xena.

## Estrutura sugerida

```text
.
├── notebooks/
│   ├── 01_tratamento_luad_revisado.ipynb
│   ├── 02_tratamento_lusc_revisado.ipynb
│   ├── 03_modelos_luad_revisado.ipynb
│   └── 04_modelos_lusc_revisado.ipynb
├── data/
│   ├── raw/          # bases originais baixadas do UCSC Xena/TCGA
│   └── processed/    # bases intermediárias e finais geradas pelos notebooks
├── outputs/
│   ├── figures/      # figuras para o TCC
│   └── tables/       # tabelas de resultados dos modelos
├── docs/
│   └── tcc_artigo_atual.tex
├── requirements.txt
└── README.md
```

## Ordem de execução

Execute os notebooks nesta ordem:

1. `notebooks/01_tratamento_luad_revisado.ipynb`
2. `notebooks/02_tratamento_lusc_revisado.ipynb`
3. `notebooks/03_modelos_luad_revisado.ipynb`
4. `notebooks/04_modelos_lusc_revisado.ipynb`

Os notebooks 1 e 2 geram as bases tratadas. Os notebooks 3 e 4 usam essas bases para treinar e avaliar os modelos.

## Dados necessários

Coloque os arquivos originais em `data/raw/` ou ajuste a variável `DATA_DIR` no início dos notebooks de tratamento.

Arquivos esperados:

```text
data/raw/HiSeqV2
data/raw/HiSeqV2_lusc
data/raw/survival_luad.txt
data/raw/survival_lusc.txt
data/raw/TCGA-LUAD.clinical.tsv
data/raw/TCGA-LUSC.clinical.tsv
```

## Execução recomendada

### Opção 1 — Google Colab, mais simples

1. Suba este repositório para o GitHub.
2. Abra o notebook pelo GitHub.
3. Clique em **Open in Colab** ou copie o notebook para o Colab.
4. Faça upload dos arquivos em `data/raw/` ou monte o Google Drive.
5. Rode as células na ordem.

### Opção 2 — GitHub Codespaces

1. Abra o repositório no GitHub.
2. Clique em **Code > Codespaces > Create codespace**.
3. No terminal do Codespaces, rode:

```bash
pip install -r requirements.txt
```

4. Abra os notebooks dentro do VS Code Web/Codespaces.
5. Selecione o kernel Python e execute as células.

## Observação metodológica importante

A seleção de genes por Cox univariado foi mantida conforme a lógica original do trabalho. Para maior rigor científico, recomenda-se declarar no texto que essa etapa é exploratória, ou realizar a seleção de genes dentro de cada fold de validação cruzada.

## Saídas esperadas

Os notebooks de modelagem exportam tabelas em:

```text
outputs/tables/
```

Essas tabelas podem ser usadas diretamente na seção de resultados do TCC.
