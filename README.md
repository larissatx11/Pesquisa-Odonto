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
