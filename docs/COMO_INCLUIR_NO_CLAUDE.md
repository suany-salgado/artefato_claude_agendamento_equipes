# Como colocar a Agenda da Equipe no seu claude.ai

Guia passo a passo para quem **nunca programou**. Você não vai precisar escrever código: o Claude faz a parte técnica. Você só vai baixar um arquivo, enviar para o Claude com uma mensagem pronta e conferir o resultado.

**Tempo estimado:** 15 a 20 minutos.

---

## Sumário

1. [Palavras que aparecem neste guia](#1-palavras-que-aparecem-neste-guia)
2. [Antes de começar](#2-antes-de-começar)
3. [Passo 1: Baixar o arquivo da agenda](#3-passo-1-baixar-o-arquivo-da-agenda)
4. [Passo 2: Abrir uma conversa nova no claude.ai](#4-passo-2-abrir-uma-conversa-nova-no-claudeai)
5. [Passo 3: Anexar o arquivo](#5-passo-3-anexar-o-arquivo)
6. [Passo 4: Preparar e enviar a mensagem](#6-passo-4-preparar-e-enviar-a-mensagem)
7. [Passo 5: Abrir a agenda e fazer um teste](#7-passo-5-abrir-a-agenda-e-fazer-um-teste)
8. [Passo 6: Compartilhar com a equipe](#8-passo-6-compartilhar-com-a-equipe)
9. [Passo 7: Guardar o link](#9-passo-7-guardar-o-link)
10. [Como pedir mudanças depois](#10-como-pedir-mudanças-depois)
11. [Se algo não funcionar](#11-se-algo-não-funcionar)
12. [Perguntas frequentes](#12-perguntas-frequentes)

---

## 1. Palavras que aparecem neste guia

| Palavra | O que significa |
| --- | --- |
| **claude.ai** | O site onde você conversa com o Claude, o assistente de inteligência artificial |
| **Artefato** | Uma página que o Claude cria e publica dentro do claude.ai. A agenda é um artefato |
| **index.html** | O arquivo que tem todo o código da agenda. É ele que você vai baixar e enviar para o Claude |
| **GitHub** | O site onde está este guia e o arquivo da agenda |
| **Banco compartilhado** | O lugar onde a agenda guarda as reuniões e tarefas. Ele fica dentro do claude.ai, não no arquivo |
| **Link** | O endereço da agenda, que você abre no navegador e compartilha com a equipe |

---

## 2. Antes de começar

Confira os quatro itens abaixo:

- [ ] **Você tem uma conta no claude.ai** e consegue entrar em [claude.ai](https://claude.ai).
- [ ] **A sua conta permite criar artefatos.** Se você já viu o Claude criar uma página, um documento ou um app ao lado da conversa, está tudo certo.
- [ ] **Para a equipe usar junto**, a conta precisa ser de uma organização (planos **Team** ou **Enterprise**). Numa conta individual, a agenda funciona, mas compartilhar e editar em grupo pode ser limitado.
- [ ] **Você sabe o nome de quem vai usar a agenda** (coordenação e colaboradores) e o nome da sua área.

**Importante saber:**

- A sua agenda vai **começar vazia**. As reuniões e tarefas da nossa equipe não estão neste repositório e não vão junto.
- A sua agenda **não fica ligada à nossa**. O que você fizer na sua não muda a nossa, e o contrário também não acontece.
- **Não registre dados pessoais ou sensíveis** na agenda (CPF, telefone pessoal, informações de saúde etc.). Tudo o que for escrito fica visível para quem tem acesso.

---

## 3. Passo 1: Baixar o arquivo da agenda

1. Abra a página principal deste repositório no GitHub.
2. Na lista de arquivos, clique em **`index.html`**.
3. Vai abrir uma tela com muito código. **Não precisa ler nem entender nada.**
4. Procure, no canto **direito**, logo acima do código, um ícone de **seta apontando para baixo** (o nome dele é **Download raw file**). Clique nele.
5. O arquivo é salvo na sua pasta **Downloads** com o nome `index.html`.

> **Não achou o botão?** Clique no botão **Raw**, que fica no mesmo lugar. Vai abrir uma página só com texto. Aperte **Ctrl + S** (no Mac, **Cmd + S**), escolha a pasta Downloads, confira se o nome está `index.html` e clique em **Salvar**.

> **Atenção:** se você der dois cliques no `index.html`, ele abre no navegador com a cara da agenda, mas **vazio e sem salvar nada**. Isso é normal. A agenda só funciona de verdade depois de publicada no claude.ai, nos próximos passos.

---

## 4. Passo 2: Abrir uma conversa nova no claude.ai

1. Abra o navegador (Chrome, Edge, Firefox ou Safari) e entre em [claude.ai](https://claude.ai).
2. Faça login com a sua conta. Se a sua empresa tem conta de organização, use **a conta da organização**, não uma conta pessoal.
3. No canto superior esquerdo, clique em **Nova conversa** (ou **New chat**, se estiver em inglês).

Use uma conversa **nova** para não misturar com outros assuntos.

---

## 5. Passo 3: Anexar o arquivo

Na caixa onde você escreve as mensagens, há duas formas de anexar:

- **Opção A:** clique no ícone de **clipe (📎)** ou de **mais (+)** ao lado da caixa de mensagem, escolha **Enviar arquivo** (ou **Upload a file**), vá até a pasta **Downloads** e selecione o `index.html`.
- **Opção B:** abra a pasta Downloads, clique no `index.html` e **arraste** o arquivo até a caixa de mensagem do claude.ai.

Você vai ver o arquivo aparecer como um pequeno cartão acima ou dentro da caixa de mensagem. **Ainda não envie.** Primeiro prepare a mensagem do próximo passo.

---

## 6. Passo 4: Preparar e enviar a mensagem

### 6.1 Copie a mensagem

Selecione todo o texto do quadro abaixo e copie (**Ctrl + C**, ou **Cmd + C** no Mac).

```
Publique este arquivo index.html como um artefato, sem mudar o layout nem
as funções. A página usa o banco compartilhado do artefato (coleções
avisos, tarefas e notas) e a função de downloads. Ative as duas.

Antes de publicar, faça estas trocas em toda a página:

1. Nomes da equipe (nas listas COLABS e TCOLABS e nas opções do formulário):
- Coordenador → [nome da coordenação]
- Colaborador 1 → [nome]
- Colaborador 2 → [nome]
- Colaborador 3 → [nome]
- Colaborador 4 → [nome]
- Colaborador 5 → [nome]

2. Nome da área: troque "Formação Profissional" por [nome da sua área].

Quando terminar, me mande o link da agenda publicada.
```

### 6.2 Cole e ajuste

1. Clique na caixa de mensagem do claude.ai (onde o arquivo já está anexado) e cole (**Ctrl + V**, ou **Cmd + V**).
2. Troque **tudo o que está entre colchetes `[ ]`** pelas informações reais. Apague também os colchetes.

**Exemplo de como fica depois de ajustar:**

```
1. Nomes da equipe (nas listas COLABS e TCOLABS e nas opções do formulário):
- Coordenador → Mariana
- Colaborador 1 → João
- Colaborador 2 → Carla
- Colaborador 3 → Rafael
- Colaborador 4 → Beatriz
- Colaborador 5 → Lucas

2. Nome da área: troque "Formação Profissional" por Recursos Humanos.
```

> **A equipe tem menos de 6 pessoas?** Apague as linhas que sobrarem e acrescente no fim da mensagem: *"Remova os colaboradores que não estão na lista."*
>
> **A equipe tem mais de 6 pessoas?** Acrescente linhas no mesmo formato, por exemplo `- Colaborador 6 → Ana`, e escreva no fim: *"Inclua os colaboradores novos em todas as listas."*

### 6.3 Envie

Confira se o arquivo `index.html` continua anexado e aperte **Enter** (ou clique na seta de enviar).

O Claude vai ler o arquivo, fazer as trocas e publicar a agenda. Isso pode levar de 1 a 3 minutos. **Não feche a página enquanto ele trabalha.**

Se o Claude fizer alguma pergunta (por exemplo, para confirmar a ativação do banco), responda **"Sim, pode ativar"**.

---

## 7. Passo 5: Abrir a agenda e fazer um teste

1. Quando o Claude terminar, a agenda aparece ao lado da conversa e/ou ele manda um **link**. Clique para abrir.
2. Confira se no topo aparece **"Agenda da Equipe"** com o nome da sua área.
3. Clique na aba **Tarefas** e confira se os **nomes da sua equipe** aparecem nos cartões.
4. Faça um teste de gravação:
   1. Volte para a aba **Agenda**.
   2. Clique no dia de **hoje** no calendário.
   3. Clique em **+ Incluir informação**.
   4. Preencha um título como **"Teste"**, escolha um nome e salve.
   5. Confira se aparece uma **bolinha verde** no dia de hoje.
5. **Atualize a página** (tecla **F5**). Se o "Teste" continuar lá, a agenda está salvando corretamente. 🎉
6. Apague o teste clicando em **Apagar** embaixo dele.

> **O teste sumiu depois do F5?** Veja a seção [Se algo não funcionar](#11-se-algo-não-funcionar).

---

## 8. Passo 6: Compartilhar com a equipe

1. Com a agenda aberta, procure o botão **Compartilhar** (ou **Share**), normalmente no canto superior direito.
2. Escolha quem pode acessar. Em contas de organização, dá para liberar para pessoas específicas ou para toda a organização.
3. Defina o tipo de permissão de cada pessoa:

| Permissão | O que a pessoa consegue fazer | Para quem dar |
| --- | --- | --- |
| **Ver** | Só olhar a agenda | Quem só precisa acompanhar |
| **Editar** | Incluir, alterar e apagar reuniões e tarefas | Só quem realmente vai cuidar da agenda |

> **Por que isso importa?** Quem controla quem pode mexer nos dados é a **permissão do compartilhamento**, não a página. Qualquer pessoa com permissão de edição consegue alterar ou apagar registros. Por isso, libere edição só para quem precisa.

4. Copie o link e mande para a equipe.

> **Os nomes dos botões mudaram?** O claude.ai atualiza a tela de tempos em tempos. Se não encontrar "Compartilhar", pergunte na própria conversa: *"Como eu compartilho esta agenda com a minha equipe?"*

---

## 9. Passo 7: Guardar o link

O link é o endereço da sua agenda. Guarde em pelo menos um destes lugares:

- Nos **favoritos** do navegador (estrela ⭐ na barra de endereço).
- No **canal ou grupo da equipe**, fixado no topo.
- Num documento interno da área.

> **Guarde também a conversa** em que a agenda foi criada. Ela fica no histórico do claude.ai, no menu da esquerda. É por ela que fica mais fácil pedir mudanças depois.

---

## 10. Como pedir mudanças depois

Sempre que quiser mudar algo (incluir uma pessoa, trocar uma cor, criar uma função):

1. Abra o claude.ai e entre na **mesma conversa** em que a agenda foi criada. Se não achar, abra uma conversa nova e **cole o link da agenda**.
2. Escreva o que você quer, em português simples. Exemplos:
   - *"Inclua a colaboradora Ana na agenda, em todas as listas."*
   - *"Remova o Lucas da lista de colaboradores."*
   - *"Troque o nome da área para Gestão de Pessoas."*
3. Peça sempre: *"Publique no mesmo endereço, sem apagar os dados."*

O Claude publica a nova versão **no mesmo link**, e as reuniões e tarefas já registradas continuam lá.

> **Dica:** antes de pedir mudanças grandes, baixe um relatório do mês em **CSV** (botão **Relatório** na aba Agenda) e guarde numa pasta da equipe. É a sua cópia de segurança.

---

## 11. Se algo não funcionar

| O que acontece | Por que acontece | O que fazer |
| --- | --- | --- |
| O Claude respondeu com o código, mas não abriu nenhuma página | Ele não publicou como artefato | Escreva: *"Publique como artefato, por favor."* |
| A agenda abre, mas o teste some depois do F5 | O banco compartilhado não foi ativado | Escreva: *"Ative o banco compartilhado (db) neste artefato e publique de novo."* Se continuar, o recurso pode não estar liberado no seu plano. Fale com quem administra a conta da organização |
| O botão de relatório não baixa nada | A função de downloads não foi ativada | Escreva: *"Ative a função de downloads neste artefato."* |
| Aparece "Colaborador 1" no lugar do nome | A troca de nomes não foi feita em todo lugar | Escreva: *"Troque Colaborador 1 por [nome] em toda a página, inclusive nas listas e no formulário."* |
| A equipe não consegue abrir o link | O compartilhamento não foi liberado | Refaça o [Passo 6](#8-passo-6-compartilhar-com-a-equipe) |
| Uma pessoa abre, mas não consegue salvar | Ela tem permissão só de **ver** | Mude a permissão dela para **editar** |
| Abri o `index.html` no computador e está vazio | É o esperado | A agenda só funciona publicada no claude.ai |
| O claude.ai diz que o arquivo é grande demais | Limite de anexo da conta | Tente de novo em outro navegador ou fale com quem administra a conta |

Para qualquer outro problema, descreva na conversa o que aconteceu e, se puder, mande um print da tela. O Claude ajuda a resolver.

---

## 12. Perguntas frequentes

**Preciso saber programar?**
Não. Você só baixa o arquivo, envia com a mensagem pronta e confere o resultado.

**Os dados da equipe que publicou este repositório vêm junto?**
Não. O arquivo tem apenas o "esqueleto" da agenda. Sua agenda começa vazia.

**Onde ficam guardadas as reuniões e tarefas que eu registrar?**
No banco compartilhado do artefato, dentro do claude.ai, na sua conta ou na conta da sua organização.

**Se eu apagar a conversa, perco a agenda?**
Evite apagar a conversa em que a agenda foi criada. Ela é o caminho mais fácil para fazer mudanças depois.

**Dá para recuperar algo que foi apagado na agenda?**
Não existe lixeira. Por isso, baixe o relatório do mês em CSV regularmente e guarde numa pasta da equipe.

**Posso mudar as cores ou o visual?**
Sim. Peça ao Claude na conversa, por exemplo: *"Troque o azul do topo por verde-escuro."*

**Quanto custa?**
A agenda em si não tem custo. Ela usa a sua assinatura do claude.ai. Confira com quem administra a conta da sua organização se os recursos de artefatos estão liberados.
