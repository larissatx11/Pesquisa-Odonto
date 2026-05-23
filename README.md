# Classificação Ordinal de Lesões de Cárie Dentária com Transfer Learning

## Descrição

Repositório contendo o código e a metodologia para a classificação ordinal da severidade da cárie dentária em fotografias da superfície oclusal.

O projeto utiliza estratégias de **Transfer Learning** e a **Decomposição Binária de Frank e Hall** para modelar a progressão biológica natural da doença:

> **Hígido < Inicial < Cavitado**

---

# Metodologia

O pipeline computacional implementado permite avaliar dez arquiteturas convolucionais pré-treinadas no **ImageNet**.

O código suporta a execução de dois paradigmas principais:

## Abordagem Híbrida

Extração estática de características utilizando a CNN como base congelada, acoplada a classificadores clássicos otimizados via **GridSearch**:

- SVM
- MLP
- Random Forest

## Ajuste Fino Parcial

Adaptação das camadas convolucionais superiores ao domínio odontológico.

## Regressão Ordinal

Implementação da formulação matemática de **Frank e Hall** para converter o problema ordenado em classificadores binários em cascata.

---

# Conjunto de Dados

O modelo foi desenvolvido e validado utilizando **356 imagens fotográficas**.

As superfícies oclusais foram categorizadas com base nos critérios clínicos visuais do **ICDAS**:

| Classe | Critério |
|---|---|
| Hígido | ICDAS 0 |
| Lesão Inicial | ICDAS 1–2 |
| Lesão Cavitada | ICDAS 3–6 |

## Nota sobre Privacidade

O banco de imagens fotográficas institucional utilizado na pesquisa possui restrição de compartilhamento público por determinações do Comitê de Ética em Pesquisa.

No entanto, o código disponibilizado inclui:

- Todo o módulo de pré-processamento
- Protocolo completo de aumento de dados dinâmico (*Data Augmentation*)

Esses componentes podem ser aplicados a conjuntos de dados próprios.

---

## Instalação das dependências

```bash
pip install -r requirements.txt
```

# Principais Resultados

O comportamento preditivo dos modelos variou conforme a complexidade arquitetural da rede base.

O sistema atingiu estabilidade preditiva e desempenho de alto nível utilizando:

- **EfficientNetV2B3** na abordagem híbrida
- **VGG19** com estratégia de ajuste fino parcial

Ambas as estratégias superaram:

- **81%** de F1-Score
- **81%** de Sensibilidade
- **81%** de Precisão

Além disso, o modelo alcançou:

```math
QWK \approx 0.84
```

A viabilidade para aplicações de telediagnóstico em tempo real foi confirmada, com latências de inferência inferiores a 100 ms.

# Autores e Citação

Pesquisa desenvolvida na **Universidade Federal do Ceará (Campus Crateús e Sobral)**, em parceria com a **Faculdade de Farmácia, Odontologia e Enfermagem de Fortaleza** e instituições internacionais.

## Equipe

- Ana Larissa Teixeira Dantas
- Jadiel Silva da Cunha
- Julyana Raab Pereira
- Beatriz Gonçalves Neves
- Bruno Riccelli dos Santos Silva
- Adriana Pigozzo Manso
- Wellington Franco
- Lidiany Karla Azevedo Rodrigues
