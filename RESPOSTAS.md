# Respostas do Trabalho - Pipeline de ML

## Identificação do Grupo

- **Integrantes:**
  1. Nome: Henrique Pimentel
  2. Nome: Rodrigo M. Barros
  3. Nome: Felipe Gouveia
  4. Nome: Suellyn Schopping

---

## Parte 1: Resultados do Pipeline

### 1.1 O pipeline executou sem erros?
<!-- Marque com X a opção correta -->
- [X] Sim
- [ ] Não

### 1.2 F1-Score obtido:
<!-- Copie o valor exibido ao final da execução -->
```
F1-Score:  0.4043
```

### 1.3 Cole aqui o output final do pipeline:
<!-- Execute: python main.py e copie a saída -->
```

🚀🚀🚀🚀🚀🚀🚀🚀🚀🚀🚀🚀🚀🚀🚀🚀🚀🚀🚀🚀
INICIANDO PIPELINE DE ML
🚀🚀🚀🚀🚀🚀🚀🚀🚀🚀🚀🚀🚀🚀🚀🚀🚀🚀🚀🚀


[ETAPA 1/4] Carregando dados...
==================================================
EXPLORAÇÃO DOS DADOS
==================================================

**************************************************

SHAPE DO DATAFRAME

Shape: (5000, 8)
==================================================

**************************************************

TIPOS DAS COLUNAS

**************************************************
cliente_id              int64
idade                   int64
renda_mensal          float64
tempo_conta_meses       int64
num_produtos            int64
tem_cartao_credito      int64
score_credito         float64
respondeu_campanha      int64
dtype: object
==================================================

**************************************************

Primeiras 5 linhas

**************************************************
   cliente_id  idade  renda_mensal  tempo_conta_meses  num_produtos  tem_cartao_credito  score_credito  respondeu_campanha
0           1     56      46917.46                229             4                   1          600.0                   1
1           2     69      41274.41                  9             3                   0          758.2                   0
2           3     46      40649.98                 25             2                   1          595.7                   1
3           4     32      44336.79                217             5                   1          584.3                   0
4           5     60      35301.68                225             4                   0          797.8                   0
==================================================
==================================================
FIM DA EXPLORAÇÃO DOS DADOS
==================================================

==================================================

DISTRIBUIÇÃO DO TARGET
------------------------------
**************************************************

CONTAGEM DE CADA VALOR DO TARGET

**************************************************
respondeu_campanha
0    2803
1    2197
Name: count, dtype: int64
==================================================
**************************************************

CONTAGEM DE CADA VALOR DO TARGET

**************************************************
respondeu_campanha
0    0.5606
1    0.4394
Name: proportion, dtype: float64
==================================================

FIM DA DISTRIBUIÇÃO DO TARGET
------------------------------
==================================================

[ETAPA 2/4] Validando dados...
Validando dados...
✅ Dados válidos!

[ETAPA 3/4] Treinando modelo...
Dados de treino: 4000 registros
Dados de teste: 1000 registros
Treinando modelo...
✅ Modelo treinado!
Modelo salvo em: models/modelo_campanha.pkl

[ETAPA 4/4] Avaliando modelo...

==================================================
RESULTADOS DA AVALIAÇÃO
==================================================

📊 MÉTRICAS:
   Accuracy:  0.5550 (55.50%)
   Precision: 0.4951
   Recall:    0.3416
   F1-Score:  0.4043

📋 MATRIZ DE CONFUSÃO:
   Verdadeiros Negativos (TN): 404
   Falsos Positivos (FP):      154
   Falsos Negativos (FN):      291
   Verdadeiros Positivos (TP): 151

==================================================
🎯 F1-SCORE FINAL: 0.4043
==================================================

✅✅✅✅✅✅✅✅✅✅✅✅✅✅✅✅✅✅✅✅
PIPELINE CONCLUÍDO COM SUCESSO!
✅✅✅✅✅✅✅✅✅✅✅✅✅✅✅✅✅✅✅✅

📝 Anote o F1-Score no arquivo RESPOSTAS.md: 0.4043
```

---

## Parte 2: Interpretação dos Resultados

### 2.1 O modelo é bom ou ruim? Por quê?
<!-- Considere: F1 de 0.5 seria jogar moeda. Acima de 0.5 = melhor que aleatório. -->
  R) O modelo não é bom. F1-Score abaixo de 0.5. A quantidade de falsos positivos foi maior que a de positivos verdadeiros, dessa forma demonstrando que teríamos resultado similar ao associar o resultado com algum evento aleatório.


### 2.2 O dataset é balanceado ou desbalanceado? Como você descobriu?
  R) O dataset é balanceado em relação a classe respondeu_campanha pois temos:
      0    2803   56,06%
      1    2197   43,94%
    O desbalanceamento ocorre quando há uma quantidade  muito maior de uma determinada classe com relação a outra, por exemplo nos casos de
    detecção de fraude nos quais poderíamos ter 99% das amostras em uma classe e apenas 1% em outra.



### 2.3 Por que usamos F1-Score e não apenas Accuracy neste caso?
  R) A accuracy mede a quantidade de previsões corretas (positivas e negativas) com relação ao total de casos. A accuracy 
     no modelo foi de 55.50%, um pouco acima da probabilidade de escolher um evento aleatório.
     No caso atual como os falsos positivos e falsos negativos importam igualmente o F1-Socre é a métrica mais robusta para avaliar o modelo.

---

## Parte 3: Validação de Dados

### 3.1 Liste as validações Pandera que você implementou:
<!-- Descreva cada validação que você adicionou -->

1. cliente_id: tipo inteiro, não permite valores nulos, único para cada registro
2. idade: tipo inteiro (18 a 80)
3. renda_mensal: tipo float (1000 a 50000)
4. score_credito: tipo float (300 a 850)
5. respondeu_campanha: tipo inteiro (0 ou 1)

### 3.2 Por que validar dados ANTES de treinar o modelo?
<!-- Pense no contexto de produção: o que aconteceria se dados inválidos entrassem no modelo? -->

Validar os dados antes de treinar o modelo é fundamental para garantir que o algoritmo esteja aprendendo a partir de informações consistentes e compatíveis com o que esperamos ver em produção. Sem essa etapa, valores fora de faixa (ex.: idade negativa, renda absurda), tipos incorretos ou categorias inválidas podem entrar silenciosamente no pipeline e afetar o modelo.

---

## Parte 4: Versionamento

### 4.1 Liste os commits que vocês fizeram (copie do git log):
<!-- Execute: git log --oneline e cole aqui -->
```
(cole o output do git log aqui)
```

### 4.2 Por que mensagens de commit descritivas são importantes?
<!-- Pense: se outra pessoa olhar o histórico, vai entender o que foi feito? -->



---

## Parte 5: Reflexão (Opcional)

### 5.1 Qual foi a maior dificuldade do grupo?



### 5.2 O que vocês fariam diferente se fossem refazer?



---

**Data de entrega:** ___/___/______
