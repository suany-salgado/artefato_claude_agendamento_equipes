# Agenda da Equipe – Formação Profissional: documentação técnica

> Cópia da documentação técnica mantida internamente no claude.ai, exportada em 24/11/2026 (revisão 22).
> O diagrama de arquitetura do documento original não é exportável e foi substituído por uma descrição em texto.
> Nesta cópia pública, os nomes da equipe foram trocados por cargos genéricos (Coordenador e Colaborador 1 a 5), e os endereços internos foram retirados.

## Visão geral

A Agenda da Equipe é uma página web interativa (artefato do claude.ai) onde a equipe de Formação Profissional da organização registra reuniões, a programação anual dos programas e as tarefas de cada colaborador, e todos consultam no mesmo lugar.

| Item | Valor |
| --- | --- |
| Endereço | Interno no claude.ai (não divulgado nesta cópia) |
| Plataforma | Artefato publicado no claude.ai (contrato de execução 0.2.96) |
| Acesso | Pessoas da organização com login no claude.ai |
| Conta responsável | Conta do setor |
| Versão em vigor | 52, de 24/11/2026 |
| Requisitos | Navegador do computador com login no claude.ai; fora do Claude a página não carrega os dados |

## Funcionalidades

Todas as funções ficam no painel principal, sem PIN, para qualquer pessoa com permissão de gravação.

| Função | Onde fica | O que faz |
| --- | --- | --- |
| Calendário do mês | Aba Agenda, à esquerda | Marca os dias: bolinha verde = tem informação; quadradinho turquesa = início de tarefa; quadradinho laranja vazado = prazo de tarefa. Ao clicar numa data, o painel da direita lista o dia |
| Tarefas no dia | Painel do dia, bloco "Tarefas" | Mostra só o nome do colaborador e quantos inícios e prazos caem no dia; "Ver tarefas →" abre a aba Tarefas na pessoa |
| Próximos itens | Aba Agenda | Lista o que vem a seguir |
| Programação do ano | Aba Programação | Linha do tempo de cada programa por ano, com navegação entre anos e botão "+ Novo programa" |
| Incluir informação: Reunião | Botão "+ Incluir informação" no dia | Campos: Nome do colaborador\*, Informação\*, Data\*, Horário, Detalhes |
| Incluir informação: Programação | Mesmo formulário, segmento Programação | Campos: Nome do colaborador\*, Nome do programa\*, Lançamento do edital\*, Encerramento das inscrições\*, Divulgação, Realização\* (ou Imersão), Local, Início das aulas online. Gera um registro por etapa |
| Tarefas por colaborador | Aba Tarefas | Primeiro o card "📥 Backlog", com as tarefas disponíveis à equipe; cada uma pode ser assumida com "✋ Pegar para…" e passa para o cartão de quem pegou, com a data. Depois, um cartão por pessoa com pendentes, concluídas e atrasadas (em vermelho). Tarefas concluídas não somem: vão para o grupo "Concluídas" do painel da pessoa, com um ✓ verde ao lado do título e "✓ Concluída em dd/mm/aaaa". Ao clicar no nome, lista as demandas com registro, início, prazo, status e a etiqueta "Atrasada"; cada uma pode ser concluída, reaberta, editada ou apagada |
| Nova tarefa | Botão "+ Nova tarefa" (aba Tarefas), "+ Nova tarefa para [nome]" e segmento "Tarefas" no formulário da Agenda | Pelo card de uma pessoa (ou do Backlog), a caixa já vem atribuída a ela, com o colaborador travado em todas as linhas; pelo botão do topo ou pela Agenda, o colaborador é escolhido livremente. Abre uma caixa com linhas: Tarefa\* (até 2.000 caracteres), Colaborador\*, Início (hoje, alterável) e Prazo (opcional). O ✓ verde indica linha completa e o "+" abre outra linha. Nada é gravado até clicar em "Concluir"; "Cancelar" descarta. Não há campo de quem registra |
| Relatório mensal de tarefas | Botão "📄 Relatório mensal (PDF)" na aba Tarefas | Escolhe o mês com ‹ › e baixa um PDF com as tarefas de início no mês, por colaborador (demanda, registro, início, prazo, status) |
| Editar / Apagar | Em cada item do dia | Edita ou exclui o registro (com confirmação); programas são editados ou apagados inteiros |
| WhatsApp | Em cada item e "Enviar o dia no WhatsApp" | Abre o WhatsApp com a mensagem pronta |
| Alertas | Banner de novidades e sininho no topo | Avisa quando há novidades desde a última visita. O sininho riscado = alertas do navegador desativados (clique para ativar); sem risco = ativados. Para desativar, use as configurações do navegador |
| Relatório | Botão "📄 Relatório" na aba Agenda | Do dia, do mês ou do ano, com setas ‹ › para trocar o período; baixa em CSV ou HTML para imprimir / salvar em PDF |

\* Obrigatório. Colaboradores da Agenda: Colaborador 1, Coordenador, Colaborador 2 e Colaborador 3; na aba Tarefas também Colaborador 4 e Colaborador 5. O nome aparece no item do dia, no relatório ("Cadastrado por") e na coluna "Colaborador" do CSV.

## Arquitetura e dados

A agenda é um único arquivo HTML (página, estilos e JavaScript juntos) publicado como artefato. Os dados não ficam no arquivo: ficam no banco compartilhado do artefato, lido e gravado em tempo real por todos que têm a página aberta.

```
Navegador (index.html) ──lê/grava──► Banco compartilhado do artefato (db)
Chat do Claude ─────────lê/grava──►        │
                                           ▼
                           Relatórios (CSV / HTML / PDF) ──► salvos manualmente na pasta compartilhada da equipe
```

A página e o chat do Claude gravam no mesmo banco; os relatórios são gerados a partir dele e salvos manualmente na pasta compartilhada da equipe.

**Capacidades declaradas no artefato**

| Capacidade | Uso |
| --- | --- |
| db | Banco compartilhado com as coleções abaixo; atualização ao vivo (onSnapshot) |
| downloads | Download dos relatórios em CSV, HTML e do relatório mensal de tarefas em PDF, com confirmação do navegador |

**Coleções do banco**

| Coleção | Conteúdo | Situação |
| --- | --- | --- |
| avisos | Um documento por reunião ou por etapa de programa | Em uso |
| tarefas | Um documento por tarefa (demanda) de um colaborador | Em uso |
| notas | Nota por ano da Programação (documento "ano-AAAA", campo texto) | Em uso |
| config/pin | Hash do antigo PIN da coordenação | Sem uso desde a versão 19 |

**Campos de um registro em avisos**

| Campo | Tipo | Descrição |
| --- | --- | --- |
| colaborador | texto | Quem cadastrou: Colaborador 1, Coordenador, Colaborador 2 ou Colaborador 3. Obrigatório desde a versão 21 |
| tipo | texto | "reuniao" ou "programacao" |
| titulo | texto | A informação (na programação, o nome da etapa) |
| data | AAAA-MM-DD | Data inicial |
| ate | AAAA-MM-DD | Data final, quando é um período |
| hora | HH:MM | Horário; vazio = dia todo |
| descricao | texto | Detalhes |
| evento | texto | Nome do programa (vazio em reuniões) |
| etapa | texto | lanc, enc, div, aulas, imer ou real |
| ordem | número | Ordem da etapa no programa |
| local | texto | Local da realização ou imersão |
| soMes / naoPrevisto | sim/não | Etapa com só o mês definido / sem data prevista |
| criadoEm / editadoEm | data e hora | Registro automático de criação e edição |

**Campos de um registro em tarefas**

| Campo | Tipo | Descrição |
| --- | --- | --- |
| colaborador | texto | Responsável: Backlog (sem dono, para quem puder pegar), Colaborador 1, Coordenador, Colaborador 2, Colaborador 3, Colaborador 4 ou Colaborador 5. Obrigatório. Ao pegar do Backlog, o campo pegaEm recebe a data e hora |
| descricao | texto | A tarefa, até 2.000 caracteres. Obrigatório |
| inicio | AAAA-MM-DD | Data de início; a caixa sugere a data de hoje. Obrigatório |
| prazo | AAAA-MM-DD | Prazo final, opcional; não pode ser antes do início |
| status | texto | "pendente" ou "concluida" |
| concluidaEm | data e hora | Quando foi marcada como concluída |
| criadoEm / editadoEm | data e hora | Registro automático de criação e edição |

Tarefas antigas podem ter o campo registradoPor (o antigo "De"), que não é mais usado nem exibido.

No navegador de cada pessoa ficam só preferências locais: a aba aberta e a data da última visita (para o aviso de novidades).

## Permissões e segurança

Quem pode alterar a agenda é definido pelo papel da conta no compartilhamento do artefato, não pela página. Por isso o PIN foi retirado na versão 19.

- **Por que o PIN saiu:** ele era conferido só dentro da página e escondia os botões, mas não impedia gravações. Pelo chat do Claude, qualquer conta com permissão alterava os dados sem PIN. Os relatórios usam os mesmos avisos que todos já veem no calendário, então o PIN também não protegia informação.
- **Regra de gravação atual:** a padrão da plataforma. Pessoas com login leem; contas com papel Colaborador (Contributor) ou acima gravam; Leitor e Comentarista não gravam.
- **Conta do setor:** é a dona do artefato e sempre pode alterar tudo. Como várias pessoas usam o mesmo login, a plataforma não distingue quem está usando. O campo Nome do colaborador registra essa autoria.
- **Chat do Claude ao lado da agenda:** não pode ser desligado e grava com as permissões de quem pede. O código da página traz uma regra escrita pedindo ao Claude que pergunte o colaborador e os campos obrigatórios antes de gravar. Isso aumenta a chance de ele perguntar, mas não é uma trava técnica.
- **Dados sensíveis:** não devem ser registrados na agenda. Tudo nela é visível para quem tem acesso.

Medida disponível, ainda não aplicada: restringir a gravação à conta do setor e a quem for Editor. As demais contas da organização continuariam vendo a agenda e recebendo os alertas.

## Histórico de alterações

Mudanças mais recentes primeiro. As versões anteriores podem ser restauradas pelo histórico de versões do artefato.

| Data | Alteração |
| --- | --- |
| 24/11/2026 | Tarefa concluída marcada só com um ✓ verde; Backlog com o texto "Disponíveis"; "+ Nova tarefa para [nome]" abre a caixa com o colaborador travado. Antes: card "📥 Backlog" no lugar do antigo "Atrasadas", que funciona como um colaborador em "Atribuir a…", com "✋ Pegar para…"; e "Ativar alertas do navegador" virou um sininho no topo (riscado = desativados, sem risco = ativados) |
| 24/11/2026 | Segmento "Tarefas" no formulário da Agenda (ao lado de Reunião e Programação), que abre a caixa de nova tarefa |
| 24/11/2026 | Card "⚠ Atrasadas" retirado da aba Tarefas; atrasos seguem no cartão de cada colaborador e na etiqueta "Atrasada" |
| 24/11/2026 | Nova tarefa em caixa com linhas (tarefa + colaborador, ✓ verde, "+"), gravadas só em "Concluir"; sai o campo "De" (quem registra); prazo opcional |
| 18/11/2026 | Início e prazo das tarefas no calendário, só com o nome do colaborador |
| 18/11/2026 | Colaborador 4 e Colaborador 5 na aba Tarefas |
| 18/11/2026 | Abas na ordem Agenda, Tarefas, Programação; relatório mensal de tarefas em PDF; botão "📄 Relatório" dentro da aba Agenda |
| 18/11/2026 | Nova aba Tarefas por colaborador |
| 16/11/2026 | Botão "📘 Documentação" na agenda |
| 16/11/2026 | Versão 21: campo obrigatório Nome do colaborador em Reunião e Programação; exibido no dia, no relatório e no CSV; regra para o chat do Claude no código |
| 16/11/2026 | Versão 20: setas ‹ › no relatório para trocar dia, mês ou ano |
| 16/11/2026 | Versão 19: PIN e "Área da coordenação" retirados; inclusão, edição, WhatsApp, programação e relatório no painel principal |

## Manutenção

Alterações na página são feitas pedindo ao Claude, com a conta do setor, informando o link da agenda. Ele publica uma nova versão no mesmo endereço, sem perder os dados.

- **Incluir ou trocar colaboradores:** os nomes da Agenda ficam na lista do formulário e na constante COLABS; os da aba Tarefas, na constante TCOLABS. Peça a alteração ao Claude, que atualiza todos e confere se há registros salvos com o nome antigo.
- **Registros antigos sem colaborador:** aparecem sem o nome. Ao editar um deles, é preciso escolher o colaborador para salvar.
- **Restaurar uma versão:** pelo histórico de versões do artefato. Isso volta a página, não os dados do banco.
- **Registro apagado por engano:** não há lixeira. Precisa ser cadastrado de novo; os relatórios em CSV salvos nesta pasta servem de cópia.
- **Cópia de segurança:** baixar mensalmente o relatório do mês em CSV e salvar na pasta compartilhada da equipe.
- **Limite de armazenamento:** se aparecer "A agenda atingiu o limite de registros", apague informações antigas depois de salvá-las em CSV.
