---
name: dashboards-de-estudo
description: Gera um dashboard de estudo em HTML de arquivo único a partir da planilha de registro do aluno, em um de três estilos (mapa de calor do edital, painel de metas ou caderno de erros). Use quando o aluno colar a planilha de registro e pedir dashboard, painel, gráfico ou controle do estudo.
---

# Dashboards de estudo

Você transforma o registro de estudo do aluno em um dashboard em HTML. Você mostra o que a planilha contém e não inventa nenhum dado: o painel é um espelho do registro, e quem decide o que fazer com ele é o aluno.

## O que pedir ao aluno (só o que faltar)

1. A planilha de registro, colada na conversa, com as linhas já preenchidas.
2. O estilo: **mapa de calor do edital**, **painel de metas** ou **caderno de erros**. Se ele não escolher, descreva os três em uma frase cada e pergunte qual quer.
3. Para o mapa de calor: o mapa do edital (ID, disciplina e blocos de cada ponto), que dá o total de cada disciplina. Para o painel de metas: as metas da semana (blocos, questões, acerto e revisões). Se ele não informar, assuma 12 blocos, 120 questões, 75% de acerto e 12 revisões, e diga que assumiu.

## Colunas esperadas

Data, ID do ponto, Disciplina, Tópico, Minutos, Questões, Acertos, Tipo de erro, Revisar em e Revisado.

Antes de gerar, confira se as colunas que o estilo escolhido usa estão presentes e preenchidas. Se faltar alguma, **avise primeiro**, diga o que ficará de fora do painel e só então gere. Nunca preencha, estime ou complete um dado que não está na planilha.

## Leitura dos dados

- **Datas** podem vir como dd/mm/aaaa ou aaaa-mm-dd. Mantenha o texto da planilha em `DADOS` e converta no script.
- **Disciplinas** são comparadas sem acento e sem diferença de maiúsculas, e aparecem com a primeira letra de cada palavra em maiúscula. Se o mapa do edital foi entregue, o ID do ponto manda sobre o nome da disciplina da planilha. ID que não existe no mapa: avise e deixe-o fora do mapa de calor (no caderno de erros ele aparece com a disciplina da planilha).
- **Revisado** vale quando for "Sim", sem diferenciar maiúsculas. Vazio ou qualquer outro texto conta como não revisado.

## Cálculos

- **Bloco** = 50 minutos. Blocos de uma linha = Minutos ÷ 50, com uma casa decimal.
- **% de acerto** = Acertos ÷ Questões, só quando Questões for maior que zero.
- **Semana** = blocos de 7 dias contados a partir da primeira Data do registro (S1, S2, S3...). A semana atual é a da última Data do registro. Se a última Data for depois de hoje, mostre um aviso discreto dizendo isso.
- **Revisão pendente** = linha com Tipo de erro preenchido, Revisar em até hoje e Revisado diferente de "Sim".
- **Cobertura** = pontos distintos já estudados ÷ pontos do edital, só se o mapa do edital foi entregue. Os blocos do mapa aparecem apenas no detalhe (ao passar o mouse).
- **Disciplina esfriando** = tem registro antes, mas as três últimas semanas estão sem nenhum registro.
- "Hoje" vem da data do computador de quem abre o arquivo (`new Date()`), não de uma data fixa escrita no código.

## Regras técnicas

- Um único arquivo HTML, com CSS e JavaScript no próprio arquivo, sem biblioteca externa e sem internet. Deve abrir com duplo clique.
- Os dados ficam em um bloco `const DADOS = {...}` no topo do script, com as linhas da planilha, para o aluno trocar sem mexer no resto.
- Gráficos em SVG escrito no próprio arquivo, com título, rótulos diretos nos valores importantes e `aria-label`. Nenhum gráfico de dois eixos.
- Estado nunca só por cor: use sempre ícone ou palavra junto (por exemplo "atrasada", "no ritmo", "esfriando").
- Passar o mouse ou focar com o teclado mostra o detalhe do item. Tudo funciona também por teclado, e os alvos de toque têm pelo menos 44 pixels.
- Funciona no celular (sem rolagem lateral na página) e tem contraste legível. O mapa de calor é sempre escuro; o painel de metas e o caderno de erros acompanham o tema claro ou escuro do aparelho.
- Todo texto em português do Brasil. Rodapé curto: "Dados do seu registro de estudo".
- `localStorage` só para conveniências (marcar revisão feita, metas editadas), sempre dentro de `try/catch`, para o painel funcionar mesmo se ele estiver bloqueado. Uma revisão que já veio "Sim" na planilha continua assim; o que o aluno marca no painel fica guardado à parte, como ajuste sobre os dados.

## Os três estilos

### 1. Mapa de calor do edital

Fundo escuro, tipografia grande, acentos em dourado e roxo. Mostra uma linha por disciplina e uma coluna por semana, com um quadrado cuja intensidade (cinco tons de uma única cor) é o número de blocos da semana: 0, 1, 2, 3 a 4 e 5 ou mais. Na visão de cobertura acumulada os tons são 0, até 10%, 11 a 25%, 26 a 50% e acima de 50%. Ao lado de cada linha, uma barra e o percentual de cobertura.

- Faixa de números no topo: cobertura do edital, blocos da semana, disciplinas iniciadas e disciplinas esfriando.
- Botão para alternar entre "Blocos por semana" e "Cobertura acumulada".
- Etiquetas "não iniciada" e "esfriando" ao lado do nome da disciplina.
- Legenda da escala e detalhe ao passar o mouse (disciplina, semana, blocos e acumulado).

### 2. Painel de metas

Fundo claro lavanda, cartões brancos. Quatro cartões no topo (blocos, questões, acerto e revisões), cada um com valor, meta, barra de progresso e estado com ícone e palavra.

- Gráfico de barras de blocos por dia da semana atual, com a meta do dia em linha tracejada e o dia de hoje destacado.
- Linha da evolução do acerto por semana, com a meta e o valor mais recente rotulado.
- Uma frase de ritmo calculada: quantos blocos e questões faltam e quantos dias de estudo restam.
- Campos para o aluno editar as metas, que o painel recalcula na hora.

### 3. Caderno de erros

Estilo de caderno: fundo creme com pauta, margem vermelha, títulos em fonte manuscrita e cartões de papel. Mostra por que o aluno erra e o que ele precisa rever.

- Números no topo: erros no caderno, revisões atrasadas, para hoje e já revisadas.
- Ranking horizontal dos tipos de erro, clicável para filtrar.
- Filtros por situação (todos, atrasadas, hoje, próximas, revisados).
- Só entram no caderno as linhas com Tipo de erro preenchido. Situação: **atrasada** se Revisar em é anterior a hoje, **hoje** se é igual e **próxima** se é posterior.
- Lista de cartões com ponto, disciplina, data do erro, tipo, situação e uma caixa para marcar como revisado, que muda o estado e recalcula os números.

## O que entregar

1. Em até três linhas por painel, antes do código: o que o painel mostra, o que ficou de fora por falta de coluna e como trocar os dados.
2. O HTML completo em um único bloco de código.
3. Depois do código, pergunte se o aluno quer outro estilo com os mesmos dados. Se ele pediu o painel de metas e não informou as metas, use as metas padrão, diga isso e ofereça ajustar.

## Tom

Direto, em português do Brasil. Não prometa resultado nem interprete o desempenho do aluno além do que os números mostram.
