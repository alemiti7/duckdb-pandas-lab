<div align="center">

# 🦆 DuckDB + Pandas Lab

### Processe gigabytes de dados com SQL puro — mesmo com 8 GB de RAM

[![Python](https://img.shields.io/badge/Python-3.9%2B-3776AB?logo=python&logoColor=white)](https://python.org)
[![DuckDB](https://img.shields.io/badge/DuckDB-0.10%2B-FFF000?logo=duckdb&logoColor=black)](https://duckdb.org)
[![Pandas](https://img.shields.io/badge/Pandas-1.5%2B-150458?logo=pandas&logoColor=white)](https://pandas.pydata.org)
[![License](https://img.shields.io/badge/Licença-MIT-green)](LICENSE)
[![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/seu-usuario/duckdb-pandas-lab/blob/main/notebooks/lab_duckdb_pandas.ipynb)

</div>

---

## 🎯 O que você vai aprender

Este laboratório prático ensina a usar o **DuckDB** — um banco de dados analítico embutido em Python — para manipular grandes volumes de dados de forma eficiente, sem precisar de servidores externos nem de máquinas caras.

| Seção | Tópico | Habilidade |
|-------|--------|------------|
| 1 | Configuração do ambiente | Instalar e verificar dependências |
| 2 | Banco de dados persistente | Criar, inserir e consultar dados em arquivo `.db` |
| 3 | Integração com Pandas | Rodar SQL diretamente sobre DataFrames |
| 4 | Processamento de arquivos grandes | Ler CSVs enormes sem estourar a RAM |
| 5 | Desafio prático | Aplicar o conhecimento sozinho |
| 6 | Referência de comandos | Consulta rápida para o dia a dia |

---

## 💡 Por que DuckDB?

```
Problema clássico com Pandas:
┌────────────────────────────────────────────────┐
│  df = pd.read_csv("5gb_de_dados.csv")          │
│  # 💀 Carrega TUDO na RAM antes de filtrar     │
│  # RAM necessária: ~5 GB + overhead do Python  │
└────────────────────────────────────────────────┘

Solução com DuckDB:
┌────────────────────────────────────────────────┐
│  duckdb.sql("""                                │
│      SELECT produto, SUM(valor)                │
│      FROM '5gb_de_dados.csv'                   │
│      WHERE status = 'Ativo'                    │
│      GROUP BY produto                          │
│  """).df()                                     │
│  # ✅ Streaming: usa ~256 MB de RAM            │
│  # ✅ Resultado: pouquíssimas linhas           │
└────────────────────────────────────────────────┘
```

O DuckDB processa o arquivo em **chunks** diretamente do disco (streaming), trazendo para a memória apenas o resultado final — que geralmente cabe em qualquer máquina.

---

## 🚀 Como executar

### Opção 1 — Google Colab (zero instalação)

Clique no badge [![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](#) acima.

### Opção 2 — Localmente

```bash
# Clone o repositório
git clone https://github.com/seu-usuario/duckdb-pandas-lab.git
cd duckdb-pandas-lab

# Instale as dependências
pip install -r requirements.txt

# Abra o Jupyter
jupyter notebook notebooks/lab_duckdb_pandas.ipynb
```

### Opção 3 — VS Code com extensão Jupyter

Abra o arquivo `.ipynb` diretamente no VS Code. Ele executa notebooks nativamente sem precisar do Jupyter instalado separadamente.

---

## 📁 Estrutura do Repositório

```
duckdb-pandas-lab/
│
├── 📓 notebooks/
│   └── lab_duckdb_pandas.ipynb   # Notebook principal do laboratório
│
├── 📄 requirements.txt            # Dependências Python
├── 📄 .gitignore                  # Arquivos a ignorar (*.db, *.parquet, etc.)
└── 📄 README.md                   # Este arquivo
```

---

## ⚙️ Requisitos

```
duckdb>=0.10.0
pandas>=1.5.0
numpy>=1.23.0
```

> Testado com Python 3.9, 3.10, 3.11 e 3.12 no Windows, macOS e Linux.

---

## 🏆 Benchmark Rápido

Resultado típico em uma máquina com 8 GB de RAM e SSD NVMe, processando **500.000 linhas**:

| Ferramenta | Estratégia | Tempo | RAM Usada |
|------------|-----------|-------|-----------|
| Pandas | `read_csv()` completo | ~0.9s | ~80 MB |
| **DuckDB** | **Streaming do CSV** | **~0.2s** | **~30 MB** |

A vantagem do DuckDB aumenta drasticamente com arquivos maiores — para 50 milhões de linhas, o Pandas pode não conseguir carregar enquanto o DuckDB termina em segundos.

---

## 🤝 Contribuindo

Contribuições são bem-vindas! Sinta-se livre para:

- 🐛 Abrir uma *issue* se encontrar algum erro
- 💡 Sugerir novos exercícios ou seções
- 🔀 Enviar um *pull request* com melhorias

---

## 📄 Licença

Distribuído sob a licença MIT. Veja [`LICENSE`](LICENSE) para mais informações.

---
## Contato
**Alexandre**  
📧 alemiti@gmail.com

<div align="center">
  Feito para a comunidade de dados 🇧🇷 &nbsp;•&nbsp; Bons estudos! 🚀
</div>
