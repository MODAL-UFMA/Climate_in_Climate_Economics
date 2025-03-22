# The Climate in Climate Economics: Análise do Projeto e Artigo Científico

## Resumo do Projeto

Este repositório é uma implementação computacional que acompanha o artigo científico "The Climate in Climate Economics" desenvolvido pelos pesquisadores Doris Folini, Aleksandra Friedl, Felix Kuebler e Simon Scheidegger (2023). O objetivo principal é melhorar a representação dos componentes climáticos nos Modelos de Avaliação Integrada (IAMs), com foco especial na recalibração do modelo DICE (Dynamic Integrated Climate-Economy).

## O que são Modelos de Avaliação Integrada (IAMs)?

Os Modelos de Avaliação Integrada (IAMs) são ferramentas computacionais que combinam conhecimentos de diferentes disciplinas para analisar problemas complexos como as mudanças climáticas. Em termos simples, eles funcionam assim:

- **Integração de sistemas**: Combinam modelos econômicos com modelos climáticos para criar uma representação unificada de como esses sistemas interagem.

- **Função principal**: Permitem simular como decisões econômicas (como políticas de redução de emissões) afetam o clima e como as mudanças climáticas, por sua vez, impactam a economia.

- **Aplicação prática**: São utilizados por formuladores de políticas públicas para avaliar estratégias de mitigação de mudanças climáticas e estimar custos e benefícios de diferentes abordagens.

- **Exemplo concreto**: O modelo DICE (Dynamic Integrated Climate-Economy), desenvolvido pelo economista William Nordhaus (ganhador do Prêmio Nobel), é um dos IAMs mais conhecidos. Ele representa a economia global como um único setor que produz um único bem, gera emissões de gases de efeito estufa como subproduto, e sofre danos econômicos devido às mudanças climáticas resultantes.

- **Limitações comuns**: Tradicionalmente, esses modelos simplificam muito a representação do sistema climático, o que pode levar a estimativas imprecisas dos impactos econômicos das mudanças climáticas.

O projeto em análise busca justamente aprimorar essa representação climática nos IAMs, tornando as previsões econômicas e recomendações de políticas mais confiáveis.

## Estrutura e Componentes do Projeto

O projeto está organizado em três módulos principais:

### 1. calibration_data
- Contém dados brutos e scripts para calibração do ciclo de carbono e função de resposta de temperatura
- Foca nas seções 3 e 4 do artigo: "Um framework abrangente para calibrar o clima em IAMs" e "CDICE - recalibrando o clima do DICE"
- Permite calibração do ciclo de carbono contra diferentes modelos (Multi-Model Mean [MMM], MESMO, ou LOVECLIM)
- A função de resposta de temperatura utiliza coeficientes diretamente de Geoffroy et al. (2013)

### 2. DEQN_for_IAMs
- Implementa códigos para a seção 6: "O custo social do carbono e a redução ótima de emissões na economia DICE"
- Utiliza uma abordagem inovadora chamada "Deep Equilibrium Nets (DEQN)" para resolver modelos de avaliação integrada não-estacionários
- Inclui simulações de diferentes cenários: resultados ótimos de mitigação, cenário "business as usual" e análises complementares do apêndice

### 3. figures_replication
- Contém rotinas para replicar todos os gráficos apresentados no artigo
- Inclui códigos em Python e Julia para visualização de resultados

## Contexto e Significado do Artigo Científico

### Problema Abordado
Os Modelos de Avaliação Integrada (IAMs) são ferramentas essenciais para a análise de políticas climáticas e econômicas, mas frequentemente utilizam representações simplificadas do sistema climático. O artigo argumenta que essas simplificações podem levar a estimativas imprecisas do custo social do carbono e recomendações subótimas de políticas de mitigação.

### Abordagem
O artigo desenvolve o CDICE, uma versão melhorada do modelo DICE com:
- Um ciclo de carbono mais sofisticado e calibrado contra modelos climáticos complexos
- Uma função de resposta de temperatura com dois componentes (oceano profundo e superfície/atmosfera)
- Incorporação de incertezas climáticas através da calibração contra múltiplos modelos

### Metodologia
1. **Calibração climática**: Desenvolvimento de um framework para calibrar com precisão os componentes climáticos
2. **Análise de equilíbrio parcial**: Cálculo do custo social do carbono mantendo trajetórias econômicas fixas
3. **Análise de equilíbrio geral**: Solução do problema de otimização econômica completo usando Deep Equilibrium Nets (DEQN)

### Resultados Principais
1. A representação climática mais precisa resulta em estimativas do custo social do carbono significativamente diferentes das obtidas com o modelo DICE padrão
2. A calibração contra diferentes modelos climáticos revela a importância da incerteza climática para a política econômica
3. As trajetórias ótimas de mitigação são substancialmente impactadas pela representação climática escolhida

## Requisitos Técnicos e Replicação

### Requisitos de Software
- **Python**: Versão 3.8.10 recomendada
- **Julia**: Para códigos específicos de visualização
- **Dependências principais**: Tensorflow, Hydra, Tensorboard, Pandas, Scipy, Matplotlib, Numpy, Keras

### Requisitos de Hardware
- Para soluções completas de modelo IAM: 8 núcleos Intel, 64GB RAM recomendados
- Para pós-processamento: Notebooks com processadores quad-core são suficientes
- Tempo estimado para reprodução completa: 1-3 dias

### Processo de Replicação
Para replicar os resultados do artigo, deve-se seguir esta sequência:
1. Calibração do ciclo de carbono (usando scripts em calibration_data)
2. Cálculo do custo social do carbono em equilíbrio parcial
3. Determinação do custo social do carbono e trajetórias ótimas usando DEQN

## Contribuição Científica

Este trabalho representa uma contribuição importante para a intersecção entre ciência climática e economia ambiental ao:

1. Demonstrar que a precisão da representação climática em modelos econômicos impacta significativamente recomendações de políticas
2. Fornecer um framework replicável para calibrar modelos climáticos simplificados contra modelos complexos
3. Aplicar técnicas avançadas de aprendizado de máquina (DEQN) para resolver modelos econômicos não-estacionários
4. Quantificar como diferentes calibrações climáticas afetam o custo social do carbono e trajetórias ótimas de mitigação

O projeto destaca que melhores representações climáticas em modelos econômicos são essenciais para o desenvolvimento de políticas eficazes de mitigação das mudanças climáticas. 