# Atividade 04 — Do Caos à Estrutura

**Disciplina:** Engenharia de Prompt e Aplicações em IA  
**Professora:** Kadidja Valéria  
**Aluno:** Lucas Lima  
**Laboratório — Aula 04**

---

## O que foi essa aula

A prof abriu com uma frase que eu anotei porque bateu: *"A IA não lê mentes. Ela lê a estrutura das suas instruções."*

O laboratório era pra testar isso na prática. Três tarefas no Gemini, e o objetivo era ver com os próprios olhos como mudar a Persona e usar um framework diferente muda completamente o que a IA te devolve.

---

## Tarefa 1 — A mesma pergunta, dois personagens completamente diferentes

A ideia era escolher um tema técnico e pedir pra IA explicar duas vezes mudando só quem ela "era". Escolhi **banco de dados** porque aparece muito em Engenharia de Software e eu ainda não entendia direito.

**Prompt 1:** *"Explique o que é um banco de dados como um locutor de futebol muito empolgado."*

Olha o que saiu:

> **OLÁ, OLÁ, MEUS AMIGOS E MINHAS AMIGAS! ESTÁ VALENDO!** Prepare o seu coração, porque hoje a bola não vai rolar no gramado, ela vai rolar no mundo da tecnologia! Você já se perguntou onde ficam guardadas as estatísticas daquele craque, os nomes dos torcedores e todos os lances do campeonato?
>
> **É AÍ QUE ENTRA O GIGANTE DA COLINA DIGITAL: O BANCO DE DADOS!**
>
> Imagine um estádio monumental, organizado, onde cada torcedor tem sua cadeira numerada! O Banco de Dados é exatamente isso: um sistema organizado para guardar informações de um jeito que a gente consiga encontrar qualquer uma delas num contra-ataque veloz!
>
> - **A Tabela é o Campo:** tudo organizado em colunas e linhas, como a escalação do time!
> - **O Registro é o Jogador:** cada linha é uma informação única, um craque com nome, RG e posição!
> - **A Consulta é o Passe de Letra:** quando você quer saber algo, faz uma "query" o passe preciso que encontra o atacante na cara do gol!
>
> **SQL** = O Jogo de Posição: tabelas rígidas, organizadas, padrão europeu. **NoSQL** = O Futebol Total: mais flexível, aguenta volume absurdo.
>
> E quem comanda tudo isso? O **SGBD** treinador e goleiro ao mesmo tempo! MySQL (o capitão experiente), PostgreSQL (o craque técnico), MongoDB (o ponta-esquerda veloz).
>
> Quando você faz login num app, o sistema corre no banco, encontra seu nome na velocidade da luz e... **É GOOOOOL!** Acesso liberado!
>
> **HAAAAJA CORAÇÃO PARA TANTA INFORMAÇÃO!**

Cara, eu ri muito. Mas a parte mais interessante foi que deu pra entender a estrutura — tabela, registro, consulta. A analogia do estádio fez sentido de um jeito que uma definição técnica talvez não fizesse.

---

**Prompt 2:** *"Explique o que é um banco de dados como um engenheiro sênior de software do Google."*

Aí a coisa ficou séria de verdade:

> Olha, se a gente for direto ao ponto, sem o "marketing" da TI: um **banco de dados** não é apenas um lugar onde você guarda coisas. É um sistema projetado para garantir a **persistência**, a **integridade** e o **acesso eficiente** aos dados.
>
> Pensa assim: se você escreve um nome em um arquivo `.txt`, você está salvando um dado. Mas o que acontece se dois processos tentarem escrever ao mesmo tempo? E se o computador desligar no meio da gravação? E se você tiver 1 bilhão de nomes e precisar achar um em menos de 10 milissegundos? É aí que o "arquivo" vira um **SGBD**.
>
> **Os três pilares:**
>
> 1. **Modelagem** — escolhemos a estrutura baseada em como vamos consultar depois. **Relacionais (SQL)** como PostgreSQL ou Spanner (usado no Google), ótimos para consistência e transações. **Não-relacionais (NoSQL)** como MongoDB ou Firestore, para escala horizontal massiva.
>
> 2. **Contrato ACID** — a garantia de que nada vai dar errado: **Atomicidade** (tudo acontece ou nada acontece), **Consistência** (os dados seguem as regras), **Isolamento** (transações paralelas não se atrapalham), **Durabilidade** (após o commit, o dado não some nem se o servidor explodir).
>
> 3. **Indexação** — sem índice, você faz um *Full Table Scan*: lê registro por registro até achar o que quer. O índice é o catálogo que aponta exatamente onde o dado está.
>
> **Dica de sênior:** não se apegue a uma ferramenta específica. Aprenda a teoria por trás — Álgebra Relacional, Teorema CAP. As ferramentas mudam, mas a necessidade de organizar informação de forma segura é eterna.

Essa resposta me assustou um pouco — ACID, Full Table Scan, sharding são termos que eu nunca tinha visto. Mas o que me chamou atenção foi que o Gemini percebeu que sou de Engenharia de Software e trouxe uma "dica de sênior" direcionada pro curso. Ele não mudou só o tom — mudou o que achou relevante me contar.

---

**Qual dos dois foi mais tecnicamente preciso?**

O segundo, de longe. O locutor foi divertido e criou uma imagem geral na cabeça, mas ele nunca falou em ACID, indexação ou no problema de dois processos escrevendo ao mesmo tempo. O engenheiro foi denso — precisei reler algumas partes — mas trouxe o vocabulário que vai aparecer nas próximas matérias.

Dá pra usar o locutor pra explicar pra alguém fora da área, e o engenheiro numa situação técnica. Cada Persona tem seu lugar.

---

## Tarefa 2 — Framework RTF na prática

A prof apresentou o **RTF: Role + Task + Format** — uma forma de estruturar o prompt em três partes bem definidas. Usei o exemplo exato do slide:

> **[R]** Você é um instrutor de Python experiente.  
> **[T]** Crie uma função que calcule a média de uma lista de números, incluindo tratamento de erros rigoroso para listas vazias.  
> **[F]** Forneça o código Python amplamente comentado, seguido de exatos 3 casos de teste.

Resultado:

```python
def calcular_media(numeros):
    # Verifica se a lista está vazia antes de qualquer cálculo
    # Listas vazias não têm média definida matematicamente
    if not numeros:
        raise ValueError("Erro: a lista não pode estar vazia.")
    
    # Soma todos os valores e divide pela quantidade de elementos
    total = sum(numeros)
    media = total / len(numeros)
    
    return media


# Caso de teste 1: lista com números inteiros comuns
print(calcular_media([10, 20, 30]))  # Saída esperada: 20.0

# Caso de teste 2: lista com um único elemento
print(calcular_media([7]))  # Saída esperada: 7.0

# Caso de teste 3: lista vazia — deve lançar o erro
try:
    calcular_media([])
except ValueError as e:
    print(e)  # Saída: "Erro: a lista não pode estar vazia."
```

O que me pegou foi o **[F]**. Só de escrever "exatos 3 casos de teste" vieram exatamente 3 — nem mais, nem menos. Parece bobagem, mas sem isso a IA poderia ter dado qualquer quantidade. Cada parte do RTF fecha uma brecha que você nem percebia que estava aberta no prompt.

---

## Tarefa 3 — Reflexão Crítica

*Como a definição explícita de um papel (Persona) alterou a qualidade e a estrutura técnica da resposta da IA?*

Antes dessa tarefa eu achava que Persona era só questão de estilo tipo, pedir pra IA responder mais descontraída ou mais séria. Mas não é só isso.

O que eu vi foi que a Persona mudou o que o modelo considerou importante mencionar. O locutor nunca falou em Full Table Scan. O engenheiro nunca falou em estádio. Era o mesmo tema, mas pareciam duas pessoas com repertórios completamente diferentes explicando ele.

A IA não tem uma resposta pronta guardada em algum lugar. Ela constrói a resposta baseada no contexto que você deu e a Persona é parte desse contexto. Quanto mais específico você for sobre quem ela deve ser, mais ela consegue filtrar o que é relevante entregar. É exatamente o que a prof disse: ela lê a estrutura, não a intenção.

---

[← Voltar ao índice](../README.md)
