# Guia de avaliação do portfólio — Adaptive RAG para Contratações Públicas do RJ

> Projeto coletivo da Residência TIC em Trilhas (PUC-Rio / Instituto ECOA). Este repositório é uma versão individual de portfólio; o código e os créditos pertencem à equipe indicada no README.

## Visão rápida

O protótipo atende perguntas em linguagem natural sobre um recorte de contratações públicas do Estado do Rio de Janeiro. Conforme a documentação do repositório, combina consultas estruturadas, cálculos sobre arquivos CSV e recuperação documental com fontes, escolhendo caminhos conforme o tipo de pergunta.

**Tecnologias documentadas:** Python, Gradio, FAISS, BM25, fusão RRF, embeddings, LLMs via endpoint compatível com OpenAI, CSV/JSON/PDF/HTML e pytest.

## Minha contribuição individual

Durante o trabalho em equipe, atuei na **coleta, organização e versionamento das bases de conhecimento**, com foco nos dados estruturados, normativos, documentais/conversacionais e agregados, além do manifesto e inventário do corpus. Essas responsabilidades estão descritas em `ARQUITETURA.md`.

## Como avaliar o projeto sem instalar a aplicação

1. Leia o [README](README.md) para entender o problema, os exemplos de perguntas e as limitações.
2. Consulte [ARQUITETURA.md](ARQUITETURA.md) para distinguir os componentes publicados do planejamento histórico.
3. Consulte [CORPUS_INVENTORY.md](CORPUS_INVENTORY.md) e [corpus_manifest.yaml](corpus_manifest.yaml) para conhecer o recorte e a organização das bases.
4. Consulte os diretórios [`src/`](src/), [`app/`](app/) e [`testes/`](testes/) para examinar implementação, interface e testes.
5. Veja o vídeo de apresentação já vinculado no README.

## Exemplos de questões tratadas no contexto do projeto

- Quantos itens de um pregão do recorte foram homologados, fracassados ou desertos?
- Qual foi o valor total homologado no pregão considerado?
- O que a Lei nº 14.133/2021 estabelece sobre o pregão?

Os exemplos acima são **perguntas**, não resultados verificados neste documento. A exatidão das respostas depende das bases, dos modelos e da configuração utilizados.

## Reprodutibilidade e limitações

- A versão pública **não inclui** os índices e todos os artefatos normalizados usados na demonstração acadêmica.
- O endpoint acadêmico de LLM/embeddings não é oferecido publicamente.
- A configuração e execução local em Windows, Linux e macOS ainda requerem validação independente.
- O corpus é um recorte histórico e não representa consulta ao PNCP em tempo real.
- Resultados e citações precisam ser conferidos nas fontes originais; o projeto não substitui análise jurídica nem auditoria.

## Privacidade, segurança e colaboração

Não publique arquivos `.env`, chaves de API, credenciais, informações pessoais ou bases não autorizadas. Antes de adicionar dados ou alterar código de autoria coletiva, confira as permissões e alinhe com os integrantes da equipe. O repositório não indica licença de reutilização nesta versão.

## Próximos passos sugeridos

- Criar uma demonstração reproduzível com **dados sintéticos** e configuração independente do ambiente acadêmico.
- Registrar comandos testados, versão do Python e resultados de testes em ambiente limpo.
- Documentar exemplos de saída com fontes e sem dados sensíveis.
- Publicar métricas de avaliação somente após medi-las e registrar seu método.
