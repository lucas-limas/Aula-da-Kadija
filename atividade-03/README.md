# Atividade 03 — Desmontando a Máquina

**Disciplina:** Engenharia de Prompt e Aplicações em IA  
**Professora:** Kadidja Valéria  
**Aluno:** Lucas Lima  
**Aula 03 — 09/03/2026**

---

## O que foi essa aula

A professora explicou como um LLM funciona por dentro — e foi bem diferente do que eu imaginava. A IA não lê texto. Ela lê **tokens**: pedaços numéricos que representam fragmentos de palavras. Cada vez que você manda um prompt, o modelo não entende a frase inteira de uma vez — ele vai prevendo qual é o próximo fragmento mais provável, um por um.

Isso explicou muita coisa que eu achava estranha no comportamento das IAs.

---

## Etapa 1 — Fui ver os tokens com meus próprios olhos

Acessei o OpenAI Tokenizer e testei. Primeira coisa que notei: a interface tava em português e chamava os tokens de **"Fichas"**. Pequeno detalhe, mas mostra que a divisão é a mesma independente do idioma da interface.

**Testei meu nome: Lucas Lima**

Resultado: **3 fichas, 10 personagens**

Meu nome tem 10 letras contando o espaço, mas foi dividido em 3 tokens. O "Lucas" sozinho já virou mais de um fragmento — o modelo nunca viu meu nome inteiro, só pedaços dele.


**Testei a frase: "A engenharia de prompt otimiza LLM"**

Resultado: **8 fichas, 34 personagens**

Deu pra ver na visualização como cada palavra virou um bloco colorido diferente. A frase tem 7 palavras, mas virou 8 tokens — o que significa que pelo menos uma palavra foi quebrada em dois fragmentos. A prof tinha falado exatamente isso na aula: a divisão é por frequência estatística, não por palavra.


---

## Etapa 2 — Testando a "temperatura" da IA

Essa etapa não precisa de print, mas fiz e achei interessante registrar.

Mandei no ChatGPT: *"O gato come... Liste as 3 palavras mais prováveis para completar essa frase com justificativa lógica."*

As respostas foram bem óbvias: **rato**, **peixe** e **ração** — associações clássicas com gato. Faz sentido porque são os fragmentos estatisticamente mais comuns depois de "gato come" em tudo que o modelo foi treinado.

Depois pedi pra ser "muito criativo": a resposta saiu completamente diferente, inventando imagens que não faziam sentido lógico, mas eram esteticamente elaboradas. E pedindo pra ser "muito técnico": resposta seca, sem personalidade, mas precisa.

A temperatura baixa = previsível. Alta = arriscado. A prof resumiu bem.

---

## Etapa 3 — O desafio do CoT

O desafio era: *"Qual é a terceira letra da quinta palavra da frase 'O rato roeu a roupa do Rei de Roma'?"*

Mandei a pergunta direto no Gemini, sem instrução de raciocínio. O que aconteceu me surpreendeu: ele **acertou**, e ainda apareceu um botão escrito **"Mostrar raciocínio"** — que quando eu abri, mostrava o passo a passo que ele tinha feito internamente:

> *"A quinta palavra da frase é 'roupa' (O - rato - roeu - a - roupa). A terceira letra da palavra 'roupa' é a letra 'u'."*


Ou seja: o Gemini já faz Chain-of-Thought automaticamente, sem precisar que eu peça. O botão "Mostrar raciocínio" é exatamente isso — ele processou em etapas por baixo dos panos.

Isso me fez entender o CoT de um ângulo diferente: a técnica existe porque **nem todos os modelos fazem isso automaticamente**. Quando a IA tenta responder direto sem guiar o raciocínio, ela pula etapas e erra. Forçar o passo a passo no prompt é uma forma de simular o que os modelos mais avançados já fazem sozinhos.

---

## Conclusão

Essa aula foi a que mais mudou minha cabeça até agora. Ver o tokenizer dividindo "Lucas Lima" em 3 pedaços foi mais esclarecedor (em minha opinião) do que qualquer slide porque ficou concreto. O modelo nunca viu meu nome, só fragmentos dele.

A divisão de tokens influencia diretamente a resposta porque o modelo raciocina em cima desses fragmentos, não das palavras inteiras. Se o fragmento for ambíguo, ou se a frase não der contexto suficiente, o modelo completa com o que for estatisticamente mais provável — e isso pode estar errado.

O CoT resolve parte disso: ao forçar etapas intermediárias, você aumenta a chance de o modelo chegar na resposta certa antes de "chutar" a conclusão.

---

[← Voltar ao índice](../README.md)
