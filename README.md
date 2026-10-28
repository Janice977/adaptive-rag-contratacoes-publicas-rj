# Adaptive RAG para Contratações Públicas do RJ

**Projeto coletivo — Grupo 1, Cenário 1 | Grande Desafio de IA Generativa & RAG | Residência TIC em Trilhas (PUC-Rio / Instituto ECOA)**

Este repositório é uma **versão individual de portfólio** do projeto desenvolvido em equipe. O sistema responde perguntas em linguagem natural sobre um recorte de contratações públicas do Rio de Janeiro, combinando **consultas estruturadas, cálculos sobre arquivos completos e recuperação documental com fontes**.

## Problema e solução

Informações sobre compras públicas estão dispersas em registros do PNCP, planilhas, atas e legislação. Perguntas diferentes exigem estratégias distintas: contar registros, somar valores, localizar um documento ou explicar uma regra. O **Adaptive RAG** identifica a natureza da pergunta e direciona a consulta à estratégia apropriada, exibindo resultados e evidências para conferência.

**Público:** profissionais de compras públicas, pesquisadores, controle e auditoria.

## Tecnologias

Python, Gradio, FAISS, BM25 (`rank-bm25`), fusão RRF, embeddings, LLMs por endpoint compatível com OpenAI, JSON, CSV, PDF, HTML e testes com pytest.

## Dados do protótipo

Na versão apresentada no Demo Day, o corpus de referência foi descrito com 2.172 chunks, distribuídos em quatro bases: estruturada, normativa, documental/conversacional e agregada. O recorte inclui **1.358 registros do PNCP** associados ao RJ e a março de 2026, Lei nº 14.133/2021, atas e planilhas de PCA e de um pregão específico. Os índices e arquivos normalizados de referência foram utilizados no ambiente de desenvolvimento do projeto, mas não estão disponibilizados nesta versão pública do repositório. O corpus é limitado e **não consulta todo o PNCP em tempo real**.

## Estrutura

- `app/` — interface Gradio e integração da aplicação.
- `src/` — roteamento, recuperação, geração, cálculos e utilitários.
- `data/v3_definitivo/ — artefatos de dados utilizados no desenvolvimento, não incluídos nesta versão pública.
- `scripts/` — rotinas de inicialização e apoio.
- `testes/` — testes automatizados.
- `ARQUITETURA.md` e `CORPUS_INVENTORY.md` — documentação técnica do projeto.

## Instalação local (orientação inicial; requer validação independente)

Pré-requisitos: Python 3.11+ (a compatibilidade exata com seu sistema operacional ainda deve ser testada), Git e um **serviço de LLM/embeddings compatível e acessível**, com os modelos adequados aos índices fornecidos.

```bash
git clone https://github.com/Janice977/adaptive-rag-contratacoes-publicas-rj.git
cd adaptive-rag-contratacoes-publicas-rj
python -m venv .venv
```

Ative o ambiente virtual:

- **Windows PowerShell:** `.\.venv\Scripts\Activate.ps1`
- **Linux/macOS:** `source .venv/bin/activate`

Instale as dependências:

```bash
python -m pip install -r requirements.txt
```

Copie `.env.example` para `.env` e configure `OLLAMA_URL`, `OLLAMA_API_KEY`, `GENERATION_MODEL` e `EMBEDDING_MODEL` com os valores do seu serviço. **Não publique `.env`.** O endpoint original do ambiente acadêmico não é fornecido como serviço público neste portfólio.

O inicializador existente (`scripts/iniciar_interface_colab.py`) foi preparado para **Colab** e exige variáveis de ambiente de logs, histórico, feedback e porta, além de um ambiente Gradio específico. **A execução local em Windows/Linux/macOS ainda não foi validada nesta versão individual.** Não é garantido que apenas instalar as dependências e rodar esse script seja suficiente; consulte o código e a documentação técnica para adaptar o ambiente.

Para executar testes que não dependem diretamente do serviço LLM (podem exigir os artefatos de dados):

```bash
python -m pytest -q -o addopts= -m "not llm" --ignore=testes/teste_integracao.py
```
## Demonstração em vídeo

🎥 **Apresentação do projeto (até 5 minutos):**

[▶️ Assista à apresentação do Adaptive RAG](https://youtu.be/_761VHkUPPA)

Neste vídeo, apresento o problema abordado pelo projeto Adaptive RAG para Contratações Públicas do Estado do Rio de Janeiro, a solução desenvolvida, as principais tecnologias utilizadas, a arquitetura, os exemplos de aplicação e os resultados.

Também destaco minha contribuição na coleta, organização e versionamento das bases de conhecimento.

O projeto foi desenvolvido coletivamente durante a Residência em Inteligência Artificial.

## Exemplos de perguntas

- Quantos itens do PE 038/26/2026 foram homologados, fracassados e desertos?
- Qual foi a soma dos valores homologados nesse pregão?
- O que a Lei nº 14.133/2021 estabelece sobre o pregão?

Os resultados dependem do corpus disponível e do ambiente de execução. Respostas e citações devem ser conferidas nas fontes.

## Limitações

A solução trabalha com um **snapshot** de dados; não substitui análise jurídica ou auditoria. A disponibilidade do modelo remoto, a compatibilidade dos embeddings com os índices e a configuração local afetam a execução. O sistema pode precisar solicitar esclarecimentos e pode não responder a perguntas fora do recorte.

## Equipe e créditos

Projeto desenvolvido coletivamente por:

- Calvin Vinicius Costa da Silva
- Eridalgo Ramos da Silva
- Felipe Teixeira da Silva
- **Janice Lira dos Santos** — organização desta versão individual de portfólio
- Luiz Carlos Gomes da Silva Júnior
- Maria Eduarda Ribeiro da Silva

**Usernames dos demais integrantes:** adicionar após confirmação, para evitar atribuições incorretas.

O código e a autoria coletiva devem ser respeitados. **Nenhuma licença de reutilização foi atribuída nesta versão**, pendente de alinhamento com a equipe.
