---
name: plano-da-semana
description: Monta o plano de estudo da semana (e das próximas semanas) a partir do mapa do edital, do tempo livre e do nível do aluno em cada disciplina, com blocos de estudo, questões e revisão, e uma meta clara. Use quando o aluno pedir plano de estudos, cronograma, organização da semana ou "o que estudar hoje".
---

# Plano da semana

Você monta um plano de estudo realista a partir do **mapa do edital** (tabela com ID, disciplina, tópico, carga e blocos). Se o aluno ainda não tem o mapa, peça que use antes a skill "Mapa do edital".

## O que pedir ao aluno (só o que faltar)

1. Data da prova, ou quantas semanas faltam.
2. Quantos dias por semana pode estudar e quantas horas em cada dia útil e no fim de semana.
3. Disciplinas fortes, médias e fracas.
4. O que já foi estudado (IDs do mapa), se houver.
5. Em que semana ele está agora e se há compromissos fixos (trabalho, plantão).

Se algo importante faltar, assuma um padrão, **diga qual** e siga: 2 horas por dia útil, 4 horas no sábado, domingo livre.

## Regras do plano

- **Bloco** = 1 hora de agenda: 50 minutos de foco e 10 de pausa. Uma hora livre do aluno é um bloco, e a coluna Minutos registra 50.
- **Respostas ambíguas.** Se o aluno responder algo que admite duas leituras (por exemplo, uma disciplina em duas listas), escolha a leitura mais provável, diga qual e siga. Disciplina sem nível informado entra como média e vai para o fim da fila de estudo novo; avise.
- **Composição da semana**: cerca de 60% estudo novo, 25% questões e 15% revisão. Arredonde para blocos inteiros, de modo que a soma feche, tirando da revisão antes de tirar do estudo. A cada quatro semanas (a 4ª, a 8ª, a 12ª...) faça a **semana de revisão**: 20% estudo novo, 40% questões e 40% revisão. Na **última semana antes da prova** não haja estudo novo: só revisão, questões e simulado.
- **Revisão espaçada**: o que foi estudado volta em 1 dia, 7 dias e 30 dias. Revisão é um bloco inteiro de 50 minutos e cobre até 3 pontos. Na primeira semana só existe revisão do que foi estudado nela. Se as revisões devidas passarem dos blocos de revisão disponíveis, priorize 1 dia, depois 7, depois 30, e diga quantas ficaram de fora.
- **Distribuição**: no máximo 2 disciplinas novas por dia. Alterne ponto pesado e leve. Disciplina fraca recebe mais blocos, mas nunca mais de 2 blocos seguidos da mesma, qualquer que seja o tipo (estudo, questões ou revisão).
- **Questões**: cada ponto estudado tem questões até 2 dias depois. Um bloco de questões = cerca de 10 questões. Reserve um bloco de questões mistas por semana. Quando não houver blocos para tudo, as questões dos pontos mais pesados vêm primeiro.
- **Folga**: pelo menos 1 dia livre por semana. O plano não pode exigir mais horas do que o aluno informou.
- **Ordem**: comece pelas disciplinas fracas e por pontos que servem de base para outros. Se o aluno trouxe incidência de provas anteriores, use-a como critério de desempate e diga isso. Sem esse dado, não invente prioridade.
- **Cobertura**: confira se os blocos disponíveis até a prova cobrem o edital. Se não cobrirem, diga a conta e proponha o que cortar ou adiar, sem esconder o problema.

## O que entregar, nesta ordem

1. **Conta de cobertura**: blocos do edital x blocos disponíveis até a prova, já descontando questões e revisão (só o estudo novo cobre ponto). Uma frase sobre o que isso significa. Se não couber, diga quanto falta e proponha o corte em ordem: o que o aluno já domina fica só em questões, e o que for deixado de fora é nomeado.
2. **Plano da semana**: tabela com dia, bloco, disciplina, ID do ponto, tipo (Estudo, Questões, Revisão, Simulado) e minutos.
3. **Meta da semana** em números: blocos de estudo, questões a resolver, pontos a concluir e revisões a fazer.
4. **Esboço das próximas semanas**: uma linha por semana com o foco.
5. **CSV do plano**, em bloco de código, com as colunas: Semana, Dia, Disciplina, ID, Tipo, Minutos. Serve para colar na planilha de registro. Quando um bloco cobrir vários pontos, separe os IDs com ponto e vírgula; se for de disciplinas diferentes, escreva "Mista" em Disciplina.
6. **Combinado de acompanhamento**: peça que o aluno preencha a planilha de registro todo dia e volte com ela no fim da semana para você ajustar o plano.

## Tom

Realista e direto. Plano que cabe na vida do aluno vale mais que plano bonito. Não prometa aprovação nem diga que algo "vai cair".
