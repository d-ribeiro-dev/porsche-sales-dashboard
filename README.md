# Porsche Sales Dashboard

Dashboard interativa desenvolvida para o desafio da DIO, com o objetivo de transformar uma planilha de vendas Porsche em uma aplicação visual para exploração e análise dos registros.

O projeto reúne indicadores, gráficos, filtros combináveis e uma tabela detalhada. A aplicação final funciona localmente em um único arquivo HTML, sem depender de serviços de IA durante sua execução.

## 1. Objetivo do projeto

Transformar a base de dados fornecida no desafio em uma dashboard que facilite a leitura dos registros e permita explorar informações por modelo, ano, localização, método de pagamento e situação da entrega.

Além de apresentar os dados, procurei identificar limitações e inconsistências da base para evitar interpretações que os registros não permitem confirmar.

## 2. Perguntas de negócio

Foram escolhidas três perguntas para orientar a análise:

### 1. Quais modelos Porsche aparecem com maior frequência nos registros?

Essa análise permite comparar a quantidade de registros por modelo e identificar quais aparecem mais vezes na base.

### 2. Como os registros estão distribuídos geograficamente?

A visualização por cidade e estado permite observar onde os registros estão concentrados e comparar a distribuição geográfica.

### 3. Quais métodos de pagamento aparecem com maior frequência?

Essa análise permite identificar os métodos registrados com maior ocorrência, sem presumir que o pagamento tenha sido efetivamente recebido.

A dashboard também apresenta informações complementares sobre ano do modelo, evolução mensal dos registros e situação das entregas.

## 3. Base de dados e tratamento

**Fonte:** planilha sanitizada disponibilizada no desafio da DIO.

A base analisada contém 100 registros, identificados pelos IDs de venda de 6 a 105.

A preparação dos dados foi realizada com Python e `openpyxl`. Foram verificadas a estrutura da planilha, a presença de valores vazios, duplicidades, identificadores e inconsistências relevantes.

### Tratamentos e cuidados adotados

- Os 100 registros foram preservados.
- Os identificadores de venda foram mantidos.
- Os preços foram tratados como valores numéricos.
- As datas foram verificadas antes de serem utilizadas na análise temporal.
- Datas inválidas foram preservadas nos registros, mas excluídas do gráfico de evolução mensal.
- A quilometragem não recebeu uma unidade única, pois a fonte mistura valores em milhas, quilômetros e valores sem unidade especificada.
- Os dados apresentados na dashboard foram limitados aos campos necessários para a análise.

### Observações sobre a qualidade dos dados

Foram identificadas 24 datas inválidas e 18 datas posteriores a 07/11/2026, data de referência da auditoria. Entre as datas futuras, nove estão associadas a registros marcados como Delivered.

Essas ocorrências foram tratadas como limitações da fonte, não como fatos corrigidos ou confirmados.

A base também não permite comprovar se os pagamentos foram efetivamente recebidos. Da mesma forma, o status Delivered representa apenas o valor registrado no campo de situação da entrega.

Por esse motivo, a dashboard apresenta valores monetários como preços registrados, e não como receita efetivamente recebida.

## 4. Funcionalidades da dashboard

A aplicação contém:

- Filtros combináveis por modelo, ano do modelo, cidade e método de pagamento.
- Indicadores de quantidade de registros, entregas, preços registrados e ticket médio.
- Gráfico de barras para comparação entre modelos.
- Gráfico de rosca para distribuição por ano do modelo.
- Gráficos de barras para cidades e estados.
- Gráfico de rosca para métodos de pagamento.
- Gráfico de linha para evolução mensal dos registros.
- Gráfico de barras para situação das entregas.
- Indicadores e observações analíticas dinâmicas.
- Tabela pesquisável, ordenável e paginada.
- Avisos sobre datas inválidas e datas futuras.
- Layout adaptável a telas menores.

Os filtros atualizam os indicadores e as visualizações de acordo com o recorte selecionado.

## 5. Prompt e processo de desenvolvimento

O desenvolvimento foi realizado de forma iterativa.

### Solicitação inicial

A solicitação inicial foi criar uma dashboard interativa de vendas Porsche a partir da planilha fornecida, preservando os registros e verificando inconsistências, especialmente nas datas.

A aplicação deveria oferecer filtros combináveis, indicadores, gráficos, recomendações analíticas, tabela de registros e funcionamento local em um único arquivo HTML.

Este texto representa uma síntese do pedido inicial, não uma transcrição literal do prompt original.

### Refinamentos

Após revisar a primeira versão, solicitei ajustes para:

- Remover textos decorativos e referências que não contribuíam para a análise.
- Melhorar tamanho, contraste e legibilidade da tipografia.
- Diversificar os tipos de gráficos, evitando a repetição de gráficos de colunas.
- Melhorar a adaptação da interface para telas menores.

A versão final utiliza gráficos de barras, gráficos de rosca e gráfico de linha, conforme o tipo de informação apresentado.


## 6. IA, agentes, competências e tecnologias

É importante separar as ferramentas utilizadas durante o desenvolvimento da tecnologia que executa a aplicação.

### Assistência de desenvolvimento

- **Assistente utilizado na construção:** Manus.
- **ChatGPT:** apoio na auditoria, análise e correção da versão final.
- **Agentes:** não foram utilizados subagentes neste projeto.
- **Skills consultadas:** `data-analysis`, `office-documents`, `deep-research`, `webdev`, `imagegen` e `image-processing`.

A fotografia utilizada na interface foi obtida no Unsplash. Não foi gerada por IA.

### Tecnologias da aplicação

- HTML
- CSS
- JavaScript
- Python
- `openpyxl`
- Playwright
- Chromium

Python e `openpyxl` foram utilizados na preparação dos arquivos. Playwright e Chromium foram utilizados nos testes do projeto.

### IA na aplicação final

A dashboard não realiza chamadas a modelos de IA, APIs ou serviços externos de inteligência artificial durante sua execução.

Os indicadores, filtros, cálculos e gráficos são produzidos pelo código JavaScript, utilizando os dados incluídos na aplicação.

Manus e ChatGPT auxiliaram no desenvolvimento, mas não são necessários para a dashboard funcionar.

## 7. Testes e validação

A versão anterior, organizada em vários arquivos, teve uma suíte de testes com oito testes aprovados, incluindo verificações de filtros isolados e combinados, pesquisa, ordenação, paginação, gráficos e responsividade.

A versão final em arquivo HTML único foi revisada localmente no VS Code com Live Server.

Foram aplicados filtros de cidade e modelo, verificando a atualização dos indicadores e gráficos.

**Importante:** os oito testes automatizados pertencem à versão anterior do projeto. Eles não devem ser interpretados como uma suíte executada diretamente sobre o HTML único corrigido.


## 8. Evidências de funcionamento

Foram registradas capturas de tela para demonstrar o funcionamento da dashboard:

1. **Visão geral:** dashboard sem filtros, exibindo os indicadores e gráficos.
2. **Filtro aplicado:** dashboard com a cidade Atlanta selecionada, apresentando três registros e a atualização dos indicadores, gráficos e tabela.

A aplicação foi verificada com filtros de cidade e modelo.


## 9. Publicação

A dashboard está publicada pelo GitHub Pages e pode ser acessada pelo endereço:

https://d-ribeiro-dev.github.io/porsche-sales-dashboard/

O repositório público do projeto está disponível em:

https://github.com/d-ribeiro-dev/porsche-sales-dashboard

## 10. Privacidade e limitações

A dashboard incorpora os dados utilizados em seu próprio HTML. Portanto, os registros disponibilizados no repositório público poderão ser consultados por qualquer pessoa.

A publicação desses dados pressupõe autorização para divulgação e a verificação de que os arquivos não contêm informações pessoais ou confidenciais.

A identificação de uma planilha como sanitizada não garante, por si só, que todo o seu conteúdo esteja adequado para publicação.

Outras limitações:

- Os preços representam valores registrados na base, não valores comprovadamente recebidos.
- O método de pagamento não comprova a conclusão de uma transação.
- O status Delivered não comprova, isoladamente, a realização da entrega.
- A quilometragem não possui unidade uniforme na fonte.
- Datas inválidas não são utilizadas no gráfico de evolução mensal.

## 11. Estrutura da entrega

A versão final da aplicação foi consolidada em um arquivo HTML único.

Estrutura esperada para a publicação:

```text
porsche-sales-dashboard/
├── index.html
└── README.md
```

O arquivo da dashboard deve ser publicado como `index.html` na raiz do repositório para que o GitHub Pages possa identificá-lo automaticamente.

---

**Projeto desenvolvido para fins de estudo e análise de dados. Não é uma aplicação oficial da Porsche AG e não possui vínculo institucional com a marca.**
